---
title: "Bridge setup in a virtual machine"
date: 2011-02-15
forum: Networking &amp; Wireless
---

### Post by shanmukhan.b on 2011-02-15
Hi,
I have a 64bit machine with ubuntu 10.04LTS in it. I have installed KVM virtual machine and in that virtual machine again i installed ubuntu 10.04LTS.

The problems are
a) I am able to do ssh from my guest os to other machines in the network but the reverse is not happening

b) If i do 'ifconfig' in host machine, I could see a virtual bridge 'virbr0',  and the same is not there when I open the /etc/network/interfaces' file.

c) host machine Ip is: 172.16.21.31 and guest machine ip is coming like: 192.168.122.31
  but i want to set an static ip like '172.16.21.32' for the guest machine.
  I edit the /etc/network/interfaces' file and added the folowing: 

"
```
address 172.16.21.32
    netmask 255.255.255.128
    network 172.16.21.0
    broadcast 172.16.21.127
    gateway 172.16.21.101
    
    bridge_ports eth0
    bridge_fd 9
    bridge_hello 2
    bridge_maxage 12
    bridge_stp on
```"
after this change and restarting networking, I could not do ssh to other machines in the network(before editing 'interfaces' file i could do ssh to that machine.)

[earlier interfaces file is using dhcp.]

Do I need to edit the /etc/network/interfaces file in the host machine or in the guest machine.

please help in this.

Thanks
B.Shanmukhan

---

