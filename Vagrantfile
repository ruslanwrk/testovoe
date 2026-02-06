Vagrant.configure("2") do |config|
  config.vm.box = "ubuntu/jammy64"

  # VM1: Nginx LB
  config.vm.define "nginx-lb" do |lb|
    lb.vm.hostname = "nginx-lb"
    lb.vm.network "private_network", ip: "192.168.56.10"
    lb.vm.provision "ansible" do |ansible|
      ansible.playbook = "ansible/playbook.yml"
      ansible.groups = { "nginx-lb" => ["nginx-lb"] }
    end
  end

  # VM2: Backend
  config.vm.define "backend" do |backend|
    backend.vm.hostname = "backend"
    backend.vm.network "private_network", ip: "192.168.56.11"
    backend.vm.provision "ansible" do |ansible|
      ansible.playbook = "ansible/playbook.yml"
      ansible.groups = { "backend" => ["backend"] }
    end
  end

  # VM3: PostgreSQL
  config.vm.define "postgres" do |pg|
    pg.vm.hostname = "postgres"
    pg.vm.network "private_network", ip: "192.168.56.12"
    pg.vm.provision "ansible" do |ansible|
      ansible.playbook = "ansible/playbook.yml"
      ansible.groups = { "postgres" => ["postgres"] }
    end
  end
end
