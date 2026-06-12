---
title: "Broadcom 4311, network unclaimed"
date: 2011-05-01
forum: Networking &amp; Wireless
---

### Post by arahn2 on 2011-05-01
I have a Dell Latitude D820 which uses a Broadcom PCI 4311 wireless interface. The wireless interface worked great with ubuntu 10 but when I upgraded yesterday to 11.04,it no longer works.
When I ran lshw -c network, it gives me information on the wireless interface but it starts off with "-network UNCLAIMED". I'm pretty much a newbie at Linux and am not sure how to proceed. When I went from windows to Ubuntu 10 it picked everything up with no problem. I checked and the proprietary broadcom drivers are loaded and activated.

---

### Post by tcarp on 2011-05-05
Same issue here - unclaimed according to $ lshw -c Network.  Tried it on two different Dells, one with a 4306/3 (which is b43 drivers) and 4311 which is STA drivers.  It works on a third Dell which has an Intel wireless modem.

bcmwl-kernel-source and b43-fwcutter are both installed according to Synaptic Package Manager.

On the Dell with the 4311, when I run Control Center / Hardware / Additional Drivers, the Broadcom STA wireless driver is activated and currently in use.

On the Dell with the 4306/3, Additional Drivers reports "no proprietary drivers are in use"

---

### Post by tcarp on 2011-05-05
$ lshw -c Network
WARNING: you should run this program as super-user.
  *-network UNCLAIMED     
       description: Network controller
       product: BCM4311 802.11a/b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0
       resources: memory:f1ffc000-f1ffffff
  *-network
       description: Ethernet interface
       product: NetXtreme BCM5755M Gigabit Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth4
       version: 02
       serial: 00:21:70:be:8f:4e
       size: 1Gbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.116 duplex=full firmware=5755m-v3.29 ip=192.168.222.215 latency=0 multicast=yes port=twisted pair speed=1Gbit/s
       resources: irq:45 memory:f1ef0000-f1efffff
WARNING: output may be incomplete or inaccurate, you should run this program as super-user.
$ lspci -nn | grep -i 14e4
09:00.0 Ethernet controller [0200]: Broadcom Corporation NetXtreme BCM5755M Gigabit Ethernet PCI Express [14e4:1673] (rev 02)
0c:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11a/b/g [14e4:4312] (rev 01)

I also went through several other very relevant looking threads such as [http://ubuntuforums.org/showthread.php?t=1025957](http://ubuntuforums.org/showthread.php?t=1025957)  to no avail.  I was bummed - they looked quite hopeful, although none of them mentioned "unclaimed."

---

### Post by curious-wanderer on 2011-05-07
was in the same situation as you.
have a read on this page. sorted me out!!! all that was required for me was to link the drivers to the wifi card using the modprobe command!!!

[http://randomphilosophyideas.blogspot.com/2011/05/ubuntu-1104-and-wireless-connectivity.html](http://randomphilosophyideas.blogspot.com/2011/05/ubuntu-1104-and-wireless-connectivity.html)

---

### Post by tcarp on 2011-05-09
You are right!  On my Dell Latitude D630 with the BCM4311, all I need to do after boot is to pop a shell and enter:

 $ sudo modprobe b43

I had tried uninstalling / installing all those packages before, and rebooting.  Never just that one modprobe.  Note that I have to do it after every boot, but at least I now have wireless.  Later I will try it on the other Dells and an HP.

Thanks!

---

### Post by josephmills on 2011-05-09
lets see what the kernel has to say ```
dmesg | grep b43 
```

---

### Post by meenxo on 2011-05-18
Thank you! I was pulling my hair out, I thought it was a hardware issue due to dropping my laptop.

---

