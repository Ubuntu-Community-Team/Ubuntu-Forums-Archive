---
title: "Cannot Conenct to Ubuntu Server until it's pinged"
date: 2012-12-12
forum: Networking &amp; Wireless
---

### Post by japricena on 2012-12-12
Hello All,

I have a question that maybe one of you can answer or have seen before. We recently deployed in our work environment a Ubuntu server. The server works fine, does it's needed purpose and then some. However, there seems to be a minor problem with the network on this machine. We have many VLANs in our organization, but I will just refer to this as the UBUNTU VLAN. We have a management VLAN that has access to all VLANs in our Datacenter including the VLAN the UBUNTU server resides.

The UBUNTU server can access everything locally on its same local VLAN, however if I try to access anything on our management VLAN it fails. If I initiate the connection from a host on the management VLAN to the UBUNTU server it also fails. However, if I simply ping the UBUNTU server from a host on the management network, all of a sudden connections begin working. The Ubuntu server then begins to accept connections on its ports (80,443,22, etc.) Example if I try to open up an SSH connection to the UBUNTU server from a host on the management network this doesn't work, but if I ping the UBUNTU server from the same host on the management network the UBUNTU server replies, and then I can connection on port 22. This is very strange.

Also as an FYI, there are other servers on the Ubuntu server (Windows servers), and they have no problem with communication to the management VLAN. The UBUNTU server is the only host that has this issue. Every morning when I come in, I have to initiate a ping to the UBUNTU server, in order for the services to work across the management network. Is there a way I can avoid this hassle everyday, and the network for this UBUNTU server can be 100% fully functional. Thank you so much in advance for any help or advice you guys can provide.

---

### Post by japricena on 2012-12-12
Can anyone advise or has anyone seen anything like this?

---

### Post by tgalati4 on 2012-12-12
Sounds like a gateway or netmask problem.  Compare the IP, Netmask, Gateway of all the machines that can talk to the Ubuntu Server and those that can't.  It could also be a rule set up in one of the routers for the port that it is plugged into.  Try putting into another port on the router or check the rules for the attached port.

---

### Post by japricena on 2012-12-13
Thanks tgalati!

I tried a few of the settings you specified, however it's sill having the issue. Could there be a network card/issue with the NIC? It's a VM, but maybe there just something wrong with it. Please see link below, my issue is nearly identical to this.

[http://ubuntuforums.org/showthread.php?t=1156633](http://ubuntuforums.org/showthread.php?t=1156633)

---

### Post by tgalati4 on 2012-12-13
I'm not familiar with how VM's handle the physical network card connection.  That sounds like the problem.  The VM won't make the card connection until a ping or active IP request is present.

If this VM is using Windows as the host operating system, then it's possible that security software or a firewall (either Window's or a part of a security application) could be interfering with your network connectivity.

Alternatively, if you have a firewall running on the Ubuntu server, then it's possible that certain rulesets could cause that behavior within your VLAN.

Tell your management to move everything "into the Cloud" and that will solve your problems.

---

