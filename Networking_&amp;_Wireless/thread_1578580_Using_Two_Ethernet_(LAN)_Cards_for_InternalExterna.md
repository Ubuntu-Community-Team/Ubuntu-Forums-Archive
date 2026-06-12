---
title: "Using Two Ethernet (LAN) Cards for Internal/External Access"
date: 2010-09-20
forum: Networking &amp; Wireless
---

### Post by violetdream on 2010-09-20
Try as I might, I can't find a good tutorial online on how to configure two lan cards (eth0 and eth1). Generally it looks like you turn off DHCP for the external network but is that all you have to do? I'm running Lucid Server edition. I heard that some people use Smoothwall red and green configuration, but I only need the capabilities that it provides for red/green network settings. I also want to keep my server install easy and if I could just change some files and maybe IP tables and so forth. Thanks!

---

### Post by perspectoff on 2010-09-20
Why are you using two NIC cards? 

Are you intending to make your Ubuntu server box the network's DHCP server as well? Is your Ubuntu Server box to be the proxy/network security device for the entire LAN? Doesn't Smoothwall have installation instructions, and a forum at

[http://community.smoothwall.org/forum/](http://community.smoothwall.org/forum/)  ?

Are you trying to accomplish Internet Connection Sharing, as in this thread?

[http://ohioloco.ubuntuforums.org/showthread.php?t=604104](http://ohioloco.ubuntuforums.org/showthread.php?t=604104)

Most likely all you need to do is edit /etc/networking/interfaces:

 sudo gedit /etc/networking/interfaces

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
address 192.168.0.140
netmask 255.255.255.0
network 192.168.0.0
broadcast 192.168.0.255
gateway 192.168.0.1
# dns-* options are implemented by the resolvconf package, if installed
dns-nameservers 192.168.0.1

# The secondary network interface
auto eth1
iface eth1 inet static
address 192.168.1.1
netmask 255.255.255.0
network 192.168.1.0
broadcast 192.168.1.255
# dns-* options are implemented by the resolvconf package, if installed
dns-nameservers 192.168.0.1

It is correct that should have only one DHCP server for each network, but you needn't turn off your DHCP server on your router unless you intend to install your own DHCP server. The example above assumes the router is 192.168.0.1. Notice that in the example both networks use the router for DNS resolution. 

Most routers then obtain DNS resolution from the ISP.

Some of the information at 

[http://kubuntuguide.org/Lucid#Internet_connection_sharing_.28DHCP_server.29](http://kubuntuguide.org/Lucid#Internet_connection_sharing_.28DHCP_server.29)

or

[http://ubuntuguide.org/wiki/Ubuntu:Lucid#Internet_connection_sharing_.28DHCP_server.29](http://ubuntuguide.org/wiki/Ubuntu:Lucid#Internet_connection_sharing_.28DHCP_server.29)

may also be helpful to you or be what you are looking for.

---

### Post by maziar_bijari on 2010-11-02
[SIZE=5]hi ,i install ubuntu server 10 with one onboard nic and one pci dlink nic ,now i check and eth0 (onboard) is oky ,but i set ip in eth1 but i cant ping out of computer and also i cant ping my ubuntu from another computer(when i ping own ubuntu server ip  i can give replay but when i ping out of computer it say destenation host unrechable)  ,i install ethtool with sudo apt-get install ethtool[/SIZE]
[SIZE=5]ethtool eth1 :it show ip with tx :86- rx:0   packet ,it say link is up but i cant use this nic ,anyone can help me plz(im new in linux world)[/SIZE]

---

