---
title: "Network Manager - ifupdown - ifconfig - static config"
date: 2011-05-08
forum: Networking &amp; Wireless
---

### Post by tburt11 on 2011-05-08
I am not a noob. I used to setup AT&T sysV networking by adding ifconfig and route commands to the /etc/rc file. Long before there was an network manager, ifup command or even an init.d folder.
 
Just for the record, I have already got a workaround, by creating a script in init.d called networking.override that executes the ifconfig and route commands to setup the interfaces I need. I have removed the entire network manager package. I don't need wireless or roaming interfaces or anything fancy. Just a static IP.
 
I hope this discussion will help others, and possibly smoke out a small networking problem with setting up static interfaces.
 
I am using Ubuntu 10.04.2 LTS on May, 8 2011, all patched up. Fresh install.
 
I wish to setup a gateway, with two network cards, regular old 10/100 network cards, one interface with DHCP to get the IP from my ISP, and the other interface needs to be static, because this box is going to run DHCP for all of the machines behind it.
 
I went into the GUI, and tried setting up a static interface, but it kept ignoring it, and setting another interface with params that made little sense. I tried several times, and then resorted to making manual entries in the interfaces file, which I was led to believe network manager would honor. I have done this dozens of times in Debian (pre-network manager), and I copied my settings from a working box doing exactly what I want it to do. something like:
 
auto lo
iface lo inet loopback
 
auto eth0
iface eth0 inet dhcp
 
auto eth1
iface eth1 inet static 
address = 10.10.33.1
network = 10.10.33.0
broadcast = 10.10.33.255
netmask = 255.255.255.0
 
pretty striaghtforward.
 
When I reboot the box, I get the loopback, and the DHCP eth0, but no eth1 interface.
 
When I run /etc/init.d/networking start, I get: FAILED to start interface.
 
When I run "ifup eth1", I get "=: Unknown host"
 
I have done about an hour of google and even downloaded the source for ifupdown.c and looked around, and I am out of time.
 
Has anyone else noticed problems when trying to setup a static interface using /etc/network/interfaces config file?
 
If I am not mistaken, network-manager is calling ifup which is calling ifconfig.
 
I really long for the simple days, when you just put a couple of lines in your /etc/rc file:
 
ifconfig eth1 10.10.10.1 broadcast 255.255.255.0 netmask 255.255.255.0
ifconfig eth1 up
route add default gw 10.10.10.1 eth1
 
Can anyone give an example that is known to work?
 
Thanks!

---

