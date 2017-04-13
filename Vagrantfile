# -*- mode: ruby -*-
# vi: set ft=ruby :



Vagrant.configure(2) do |config|
  numNodes = 4
  config.vm.box_url = "http://files.vagrantup.com/precise64.box"
  ipAddrPrefix = "192.168.56.10"
  config.vm.network "forwarded_port", guest: 8091, host: 3001
  config.vm.provision :puppet
  
  config.vm.provider "virtualbox" do |client|
        client.customize ["modifyvm", :id, "--memory", 1024]
    end

  1.upto(numNodes) do |num|
    nodeName = ("node" + num.to_s).to_sym
    config.vm.define nodeName do |node|
        node.vm.box = "precise64"
        node.vm.network :private_network, ip: ipAddrPrefix + num.to_s
        node.vm.provider "virtualbox" do |v|
            client.name = "Couchbase Server Node " + num.to_s
        end
    end
end

end

