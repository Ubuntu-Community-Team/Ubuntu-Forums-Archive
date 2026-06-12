---
title: "default drivers? what are does 8.04 use ase default to detect wireless?"
date: 2009-04-10
forum: Networking &amp; Wireless
---

### Post by jcm1107 on 2009-04-10
Hi I need to know what Ubuntu 8.04 Hardy uses as default to find wireless card. I had a graphics driver problem and had to install an updated driver in the process I had to disable drivers and whatever I disabled also caused my wireless card to not be detected anymore. When I first installed my Ubuntu it worked perfect. I have a Linksys pci wirless card. Also the internet seemed alot faster before I disabled drivers. I have an XfXnForce630i motherboard with 7150 graphics. I know in windows Xp I had to install Ethernet drivers to get the internet to work I just wonder if there were drivers for the ethernet that I may have disabled also. when I disabled the drivers I serched synaptic for nvidia and I disabled almost everything in that search. Thanks!

---

### Post by superprash2003 on 2009-04-10
post output of **lshw -C network** to find out your wifi card..

---

### Post by jcm1107 on 2009-04-10
Here are the results of that command

justin@ubuntu:~$ sudo lshw -C network
[sudo] password for justin: 
  *-network UNCLAIMED     
       description: Network controller
       product: BCM43XG
       vendor: Broadcom Corporation
       physical id: 6
       bus info: pci@0000:01:06.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: latency=64
  *-network
       description: Ethernet interface
       product: MCP73 Ethernet
       vendor: nVidia Corporation
       physical id: f
       bus info: pci@0000:00:0f.0
       logical name: eth0
       version: a2
       serial: 00:1d:92:ed:ec:75
       size: 100MB/s
       capacity: 1GB/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm msi bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.61 duplex=full ip=192.168.1.101 latency=0 link=yes maxlatency=20 mingnt=1 module=forcedeth multicast=yes port=MII speed=100MB/s
justin@ubuntu:~$

---

### Post by superprash2003 on 2009-04-11
try this [http://www.prash-babu.com/2008/11/how-to-configure-broadcom-wireless-in.html](http://www.prash-babu.com/2008/11/how-to-configure-broadcom-wireless-in.html) if that doesnt work.. try this [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty)

---

### Post by jcm1107 on 2009-04-11
> **superprash2003 said:**
> try this [http://www.prash-babu.com/2008/11/how-to-configure-broadcom-wireless-in.html](http://www.prash-babu.com/2008/11/how-to-configure-broadcom-wireless-in.html) if that doesnt work.. try this [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty)

When I first installed ubuntu I had to install ubuntu 7.1 Gibbon because Hardy wouldn't install then I upgraded to hardy and did all the updates and my wireless was recognized I believe it is the broadcom sta wireless driver but it is not showing anything when I go to system-administration-hardware-
it says no proprietary drivers are in use on this system. I know this is because I had to remove alot of packages in synaptic to install my new graphics driver. I just need to know how I can get the driver back for my wireless. Thanks

---

