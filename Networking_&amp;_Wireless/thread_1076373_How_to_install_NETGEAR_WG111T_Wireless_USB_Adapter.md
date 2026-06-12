---
title: "How to install NETGEAR WG111T Wireless USB Adapter?"
date: 2009-02-21
forum: Networking &amp; Wireless
---

### Post by Pedro D on 2009-02-21
Does anyone know how to install a NETGEAR WG111T Wireless USB Adapter on ubuntu 8.10?

---

### Post by superprash2003 on 2009-02-21
in your terminal type **lshw -C network** and post output here..

---

### Post by dellaportas on 2009-03-02
Hi
I also have the same problem, here it is what I get:

 lshw -C network 
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: 82801CAM (ICH3) PRO/100 VE (LOM) Ethernet Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:02:08.0
       logical name: eth0
       version: 42
       serial: 00:00:39:c6:cd:83
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=e100 driverversion=3.5.23-k4-NAPI firmware=N/A ip=192.168.2.2 latency=64 maxlatency=56 mingnt=8 module=e100 multicast=yes
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 86:3f:13:9d:6e:aa
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes

Many thanks in advance
Thomas

---

### Post by lindsay7 on 2009-03-02
Look in the forum (network and wireless - stickies) this came from there. I think you need to find out what chip set in in the adaptor. It looks like one will work with wpa and the other will not.

[https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsNetgear#USB](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsNetgear#USB)

---

### Post by dellaportas on 2009-03-02
done it -many thanks!
Thomas

---

### Post by Pedro D on 2009-03-02
Oh never mind I don't need help installing that anymore thanks to this PCI Card I found literately in my computer that happened to be there for a few years not connected and bouncing all over the place in there. When I heard it bouncing in there while I was  putting my computer on top of my desk, I thought...

"Gee, I wonder if that PCI Card works with Linux?" 

And it turned out.. It did work! It is a EZ Connect PCI Card I think it is a wireless g PCI Card since it has a g on it. But thanks for all your help people of the ubuntu community!

---

