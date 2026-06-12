---
title: "Two Lan Network Cards, and wireless (for ps3 setup)"
date: 2009-02-09
forum: Networking &amp; Wireless
---

### Post by zoostation07 on 2009-02-09
Hi could anyone help me please. I moved to linux a few weeks back and i think its great. Im having problems getting my setup to work with my ps3. 

This is my setup:

2 Lan network cards:

SiS900 PCI Fast Ethernet
+
Not sure, it has no product name (in ifconfig)

1 wireless card:

RT2561/RT61 802.11g PCI

---------

Im trying to setup ubuntu (8.10 intrepid) kernel linux: 2.6.27.11 generic, Gnome 2.24.1

to work with my ps3 via [ps3 media server]("http://code.google.com/p/ps3mediaserver/") without success.

Here is my ifconfig log / terminal:

  *-network:0 DISABLED    
       description: Ethernet interface
       product: SiS900 PCI Fast Ethernet
       vendor: Silicon Integrated Systems [SiS]
       physical id: 6
       bus info: pci@0000:01:06.0
       logical name: eth1
       version: 02
       serial: 00:06:4f:09:e7:ec
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=sis900 driverversion=v1.08.10 Apr. 2 2006 latency=32 maxlatency=11 mingnt=52 module=sis900 multicast=yes
  *-network:1
       description: Wireless interface
       product: RT2561/RT61 802.11g PCI
       vendor: RaLink
       physical id: 8
       bus info: pci@0000:01:08.0
       logical name: wmaster0
       version: 00
       serial: 00:11:50:de:20:3f
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=rt61pci ip=192.168.2.2 latency=32 module=rt61pci multicast=yes wireless=IEEE 802.11bg
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 76:84:34:9d:45:ed
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes

And also network interfaces (/etc/network - gedit):

auto lo
iface lo inet loopback

iface pan0

auto eth1
iface eth1 inet static
address 192.168.1.1
netmask 255.255.255.0
broadcast 192.168.1.255
network 192.168.1.0

I have setup this using [this ]("http://news.softpedia.com/news/How-to-Turn-Linux-Into-a-PS3-or-Xbox-360-Media-Server-102831.shtml")website. It basically tells you to install two network lans, plug one ethernet cable into one network card then one into the console and then gives you settings to add.

Im having troubles getting my playstation 3 to work with this, it seems the network lan interface(s) are down / disabled?

Could someone please help / point me in the right direction, i have spent hours trying to find solutions, sadly as im new linux i have not gotten very far.

Thanks for any help!

Dan.

---

### Post by cariboo on 2009-02-09
Have a look at this [article]("http://www.linux.com/feature/55617"), to see if it will help.

Jim

---

### Post by zoostation07 on 2009-02-09
> **cariboo907 said:**
> Have a look at this [article]("http://www.linux.com/feature/55617"), to see if it will help.

Jim

Thanks Jim ,will take a look try it out and report back.. :)

---

### Post by zoostation07 on 2009-02-09
> **zoostation07 said:**
> Thanks Jim ,will take a look try it out and report back.. :)

Sadly this isnt what im after..

[http://news.softpedia.com/news/How-to-Turn-Linux-Into-a-PS3-or-Xbox-360-Media-Server-102831.shtml]("http://news.softpedia.com/news/How-to-Turn-Linux-Into-a-PS3-or-Xbox-360-Media-Server-102831.shtml") is the url im using. i dont know if someone can make sense of this, it makes sense for me what to do, but when i do what it says it just doesnt work!

any info appreciated.

Dan

---

### Post by zoostation07 on 2009-02-10
bump..

?? Any help.. 

Dan.

---

