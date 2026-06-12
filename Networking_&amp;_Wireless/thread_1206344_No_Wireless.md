---
title: "No Wireless?"
date: 2009-07-07
forum: Networking &amp; Wireless
---

### Post by rob2nd9th on 2009-07-07
Hi , ok I have two laptops, an Acer Aspire 5720 running ubuntu 9.4 Kernel 2.6.28-13-generic

This sees and picks up the wifi (3com) fine

The other a Compaq presario CQ60 running ubuntu 9.4 Kernel 2.6.28-13-generic sees no wireless at all?

Any thoughts

thanks

---

### Post by superprash2003 on 2009-07-07
post output of **lshw -C network**

---

### Post by rob2nd9th on 2009-07-07
Here it is.

WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: MCP78S [GeForce 8200] Ethernet
       vendor: nVidia Corporation
       physical id: a
       bus info: pci@0000:00:0a.0
       logical name: eth0
       version: a2
       serial: 00:1f:16:63:ea:ae
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=forcedeth driverversion=0.61 ip=192.168.1.2 latency=0 maxlatency=20 mingnt=1 module=forcedeth multicast=yes
  *-network UNCLAIMED
       description: Ethernet controller
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:07:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: cap_list
       configuration: latency=0
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 66:e8:b4:5e:6b:18
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes

---

### Post by Sankou on 2009-07-07
This is your wireless adapter:
> 
*-network UNCLAIMED
       description: Ethernet controller
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:07:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: cap_list
       configuration: latency=0
It currently has no driver assigned to it. Get ndiswrapper and use it to install the windows driver for the device. You need the .inf and .sys files. Put the two in the same location. Open a terminal and change the directory to that location and run this:

```

sudo ndiswrapper -i [your driver].inf

```Then run:

```

sudo ndiswrapper -l

```The output should say that the driver is installed and the device is present. Reboot the system and it should recognize your wireless card.

---

### Post by Idefix82 on 2009-07-07
Sankou, ndiswrapper is not as simple to get to work, as you seem to think. By far the most drivers don't work with it and it sometimes takes a long time to find the right driver.

rob2nd9th, please try [this guide]("http://ubuntumanual.org/posts/185/install-atheros-ar242x-802-11abg-wireless-driver-in-ubuntu") by just copying and pasting the commands into the terminal and providing your password whenever you are asked for it. But instead of the last command (sudo gedit...) please do the following **without rebooting**
```
sudo modprobe ath_pci
```
and let us know whether your wireless comes up. If not, please post the output from
```
lshw -C network
```
again. If you get any errors along the way, please paste them here. Don't forget that at the beginning you have to disable the currently used wireless drivers (very first bullet point in the guide).

---

### Post by superprash2003 on 2009-07-07
have you tried system->admin->hardware drivers?

---

### Post by rob2nd9th on 2009-07-07
I Followed this

[http://ubuntumanual.org/posts/185/install-atheros-ar242x-802-11abg-wireless-driver-in-ubuntu](http://ubuntumanual.org/posts/185/install-atheros-ar242x-802-11abg-wireless-driver-in-ubuntu)

Worked very well

Thanks for all the help.

---

