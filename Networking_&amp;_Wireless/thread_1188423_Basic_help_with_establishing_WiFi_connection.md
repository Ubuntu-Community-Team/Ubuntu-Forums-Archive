---
title: "Basic help with establishing WiFi connection?"
date: 2009-06-15
forum: Networking &amp; Wireless
---

### Post by oxf on 2009-06-15
I've just installed Jaunty 9-04 on my laptop. Compaq Presario M2000. 
It doesn't appear at this point to be automatically detecting my WiFi. However, I'm not quite sure what I should be trying at this point. I just may not be doing it right?
 
Anyway I do have the Broadcom BC4318 wireless card which in the past (eg under 8.04 needed a little bit of tweaking to get it functioning. I've heard this is much improved under Jaunty so it may/may not be  a particular problem.   
 
So starting at the absolute begining after install could someone point me in the right direction on what I should be doing/clicking/trying etc to set it up?
 
Many thanks

---

### Post by Iowan on 2009-06-15
Does the desktop fire up with an icon in the top right corner that looks like a wireless signal strength indicator?   A right-click should reveal if wired/wireless is enabled.  A left-click *should* reveal available wireless networks.  I gotta remember to turn wifi on before it finds anything (DUH).
If nothing shows, you might need to create a wireless connection.  If it won't let you - or the connection won't work, it may be time to troubleshoot the interface. First step will be to check/post **lshw -C network**. I haven't done a lot of wireless debug, but seems like **iwconfig** is another useful source of information (as well as **ifconfig -a**).

---

### Post by oxf on 2009-06-15
> **Iowan said:**
> Does the desktop fire up with an icon in the top right corner that looks like a wireless signal strength indicator?   A right-click should reveal if wired/wireless is enabled.  A left-click *should* reveal available wireless networks.  I gotta remember to turn wifi on before it finds anything (DUH).
If nothing shows, you might need to create a wireless connection.  If it won't let you - or the connection won't work, it may be time to troubleshoot the interface. First step will be to check/post **lshw -C network**. I haven't done a logt of wireless debug, but seems like **iwconfig** is another useful source of information (as well as **ifconfig -a**).

Thanks. Yes the wireless sighal strengh icon is there and a right click will enable/disable it but its not finding anything. So I guess I need to create one which I'm trying to do.

I just went back to my notes from Hardy and folowed them. I.e. Used a wired conection, went to System>Administration>HardwareDrivers. In that should have auto detected and listed the drivers. i.e BC4318 to download. However the box is empty! So where do I go from here? 

lspci -v | less
05:02.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
        Subsystem: Hewlett-Packard Company Device 1356
        Flags: bus master, fast devsel, latency 64, IRQ 20
        Memory at c0204000 (32-bit, non-prefetchable) [size=8K]
        Kernel driver in use: b43-pci-bridge
        Kernel modules: ssb

mbdb@M2000:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network:0             
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: eth0
       version: 10
       serial: 00:c0:9f:f3:97:78
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=8139too driverversion=0.9.28 ip=192.168.1.75 latency=64 maxlatency=64 mingnt=32 module=8139too multicast=yes
  *-network:1
       description: Network controller
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 2
       bus info: pci@0000:05:02.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64 module=ssb
  *-network:0 DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:14:a5:29:d2:c2
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg
  *-network:1 DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: fe:fe:40:69:8f:bb
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes
mbdb@M2000:~$

---

### Post by oxf on 2009-06-15
I should also add that when left clicking on the wireless or network icon "Wireless Networks" hat is greyed out. Whether or not wireless is enabled on right click.

What is VPN? do I need to do something here?

---

### Post by Iowan on 2009-06-15
VPN is a Virtual Private Network. Interesting concept I gotta try sometime... but not something that *needs* to be set up to make net... work.

---

### Post by Iowan on 2009-06-15
> **Iowan said:**
> I gotta remember to turn wifi on before it finds anything (DUH). Does your Compaq have a separate on/off switch? I presume that (unlike me) you don't try to use the wireless whilst it is switched off.

---

### Post by oxf on 2009-06-15
> **Iowan said:**
> Does your Compaq have a separate on/off switch? I presume that (unlike me) you don't try to use the wireless whilst it is switched off.

Yes it does but at this point its non functional. When I installed Hardy the wireless switch was non functional until I got the driver working.

I just went back to my notes and followed the procedure I used under Hardy. i.e. 
Installed ndiswrapper from the live CD. Then just as in Hardy it detects and lists the driver under Admin>HardwareDrivers. However, when I try to download and activate it sits at 0% for the longest of time and fails, give some message about "backend" not functioning. So I dont know if I have another issue going on here or not.

---

### Post by superprash2003 on 2009-06-16
you would need a wiredc onnection when trying to activate hardware drivers..

---

### Post by oxf on 2009-06-16
> **superprash2003 said:**
> you would need a wiredc onnection when trying to activate hardware drivers..
 
Yes all of the above was with a wired connection. Which make me all the more puzzled why I cant load the driver! I can do anything else online fine, including post this repy etc, just haveing dificulty downloading the driver!

---

