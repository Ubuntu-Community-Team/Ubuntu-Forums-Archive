---
title: "no wired internet now on lucid"
date: 2010-10-18
forum: Networking &amp; Wireless
---

### Post by linuxhippy on 2010-10-18
I have been using lucid ubuntu 64 bit on this pc for months with no problem till yesterday.  I noticed yesterday that eth0 was no longer being set up on boot and so internet is not there now.  I am currently on the internet using karmic ubuntu.

Any ideas why this happened...I'm thinking an update with aptitude?  What can I do in lucid to get my networking working?  I tried booting into recovery mode and repairing packages but my pc could not get on the net to check the packages.

---

### Post by dineshs on 2010-10-18
can you post the results of```
sudo lshw -C network
``````
route -n
```and```
ping -c5 4.2.2.1
```

---

### Post by linuxhippy on 2010-10-18
tux@LinuxHippyIII:~/Desktop$ sudo lshw -C network
  *-network DISABLED      
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 3
       bus info: pci@0000:02:03.0
       logical name: eth0
       version: 10
       serial: 00:13:d3:21:bc:7f
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full latency=64 link=yes maxlatency=64 mingnt=32 multicast=yes port=MII speed=100MB/s
       resources: irq:23 ioport:7800(size=256) memory:ff3ffc00-ff3ffcff memory:58000000-5800ffff(prefetchable)

tux@LinuxHippyIII:~/Desktop$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface

tux@LinuxHippyIII:~/Desktop$ ping -c5 4.2.2.1
connect: Network is unreachable

---

### Post by dineshs on 2010-10-18
> *-network DISABLED 
Rightclick the network manager icon on top right of the panel and see that [COLOR="Blue"]enable networking[/COLOR] is ticked.
Hope it is enabled in BIOS

---

### Post by linuxhippy on 2010-10-18
I don't have a network icon in xubuntu...how do I pull up the network manager using CLI?

---

### Post by dineshs on 2010-10-18
I am not sure about xubuntu.Can you post the results of```
gksudo gedit /etc/NetworkManager/nm-system-settings.conf
```and```
gksudo gedit /var/lib/NetworkManager/NetworkManager.state
```

---

### Post by dineshs on 2010-10-18
You may try if this works(shows icon)
Right click on the top panel-click add to panel-select notification area -click add

---

### Post by linuxhippy on 2010-10-18
I don't have NetworkManager binaries (I did a locate NetworkManager and nothing was in /bin /sbin /usr/bin or /usr/sbin) and nothing called NetworkManager was available to add to my panel.

Here's nm-syste-settings.conf

# This file is installed into /etc/NetworkManager, and is loaded by 
# NetworkManager by default.  To override, specify: '--config file' 
# during NM startup.  This can be done by appending to DAEMON_OPTS in 
# the file:
#
# /etc/default/NetworkManager
#

[main]
plugins=ifupdown,keyfile

[ifupdown]
managed=false

******************************************

Here's NetworkManager.state


[main]
NetworkingEnabled=false
WirelessEnabled=true
WWANEnabled=true


**********************************************

Here's what's been bothering me since I'm the only user on this pc...WHO did this?!?!?!  Was my pc broken into by somebody on the net who disabled my networking?

---

### Post by dineshs on 2010-10-18
> nothing called NetworkManager was available to add to my panel.You need to add [COLOR="Blue"]notification area[/COLOR] as follows
1)Right click on the top panel-click add to panel-select notification area -click add (pl see attachment)
2)run ```
gksudo gedit /etc/NetworkManager/nm-system-settings.conf
```and set```
managed=true
```
3)run```
gksudo gedit /var/lib/NetworkManager/NetworkManager.state
```
and set```
NetworkingEnabled=true
```Restart and see if it works
> Here's what's been bothering me since I'm the only user on this pc...WHO did this?!?!?! Was my pc broken into by somebody on the net who disabled my networking?
Updates did I think

---

### Post by linuxhippy on 2010-10-18
woohoo!!  That did it-I think you were right too about updates causing this.  Weird-I'm working inside XUbuntu x86_64, so why is aptitude grabbing Ubuntu packages that could mess up my system?

---

### Post by dineshs on 2010-10-19
Happy to hear your problem is solved.Please mark the thread as solved via thread tools

---

