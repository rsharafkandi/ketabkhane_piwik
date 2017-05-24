# -*- mode: ruby -*-
# vi: set ft=ruby :

# Vagrantfile API/syntax version. Don't touch unless you know what you're doing!
VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
  config.vm.box = "centos/7"

  config.vm.provider "virtualbox" do |vb|
    vb.memory = 4096
    vb.cpus = 2
    # Needed for multiple CPUs
    vb.customize ["modifyvm", :id, "--ioapic", "on"]
  end

  config.vm.network "forwarded_port", guest: 80, host: 8888 

  config.vm.provision "ansible" do |ansible|
    ansible.playbook = "playbook.yml"
    ansible.extra_vars = {
       piwik: { mysql_password: 123456 }
    }
  end

end
