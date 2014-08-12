# -*- mode: ruby -*-
# vi: set ft=ruby :

# Vagrantfile API/syntax version. Don't touch unless you know what you're doing!
VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
  config.vm.box = "ubuntu-14.04"
  config.vm.box_url = "https://oss-binaries.phusionpassenger.com/vagrant/boxes/latest/ubuntu-14.04-amd64-vbox.box"

  config.vm.provision "chef_solo" do |chef|
    chef.add_recipe "rvm::vagrant"
    chef.add_recipe "rvm::user" # RVM pra um user
    # chef.add_recipe "rvm::system" # Instala o RVM pra todos os users, comentar a linha de baixo e o chef.json

    # You may also specify custom JSON attributes:
    chef.json = {
      rvm: {
        user_installs: [ {
          user: 'vagrant',
            default_ruby: '2.1',
            rubies: ['1.9.2', '2.1']
        } ],
        vagrant: { 
          system_chef_solo: "/opt/chef/bin/chef-solo"
        }
      }
    }
  end
end
