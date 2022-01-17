ENV['VAGRANT_DEFAULT_PROVIDER'] = 'libvirt'
BRIDGE_INT = "br-mgmt"

Vagrant.configure("2") do |config|
  config.ssh.insert_key = false
  config.vm.synced_folder ".", "/vagrant"
 
  config.vm.define :nodo1 do |nodo1|
    nodo1.vm.box = "generic/ubuntu2004"
    nodo1.vm.hostname = "nodo1"
    nodo1.vm.box_check_update = false

    nodo1.vm.provision :docker
    nodo1.vm.provision :docker_compose    

    nodo1.vm.network "public_network",
    :dev => BRIDGE_INT,
    :type => "bridge",
    :mode => "brigde",
    :ip => "10.21.7.88"
    
    nodo1.vm.provider :libvirt do |v|
      v.memory = 2048  
      v.cpus = 2
    end  
  end
end

#https://jeremy.geek.nz/tag/libvirt/