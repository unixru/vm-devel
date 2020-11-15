# -*- mode: ruby -*-
# vi: set ft=ruby :

# Vagrantfile API/syntax version. Don't touch unless you know what you're doing!
VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
  # Public settings
  provider = "virtualbox"
  net_ip = "192.168.35"

  # Nodes for develop and testing
  #
  #  name       IP address      RAM       OS                    OS Version
  Nodes = [
    ["vm-node1",  "#{net_ip}.51", "2048", "ubuntu/xenial64",     "20201106.0.0" ],
    ["vm-node2",  "#{net_ip}.52", "2048", "ubuntu/bionic64",     "20201106.0.0" ],
    ["vm-node3",  "#{net_ip}.53", "2048", "ubuntu/focal64",      "20201105.0.0" ]
  ]
  Nodes.each do |name,ip,mem,osbox,osbox_ver|
    config.vm.define "#{name}", primary: true do |node|
      node.vm.provider "#{provider}" do |provider|
        provider.memory = "#{mem}"
        provider.cpus = 1
        provider.name = "#{name}"
      end
      node.vm.box = "#{osbox}"
      node.vm.box_version = "#{osbox_ver}"
      node.vm.network "private_network", ip: "#{ip}", auto_config: false, virtualbox__intnet: "Nat35", hostname: true
      node.vm.hostname = "#{name}"
    end
  end
end

