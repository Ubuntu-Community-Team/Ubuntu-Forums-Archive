---
title: "Unable to connect to internet"
date: 2009-03-24
forum: Networking &amp; Wireless
---

### Post by cdawley4 on 2009-03-24
Hi,

I know this topic has been posted many times on here.  I just installed Ubuntu 8.10 on a Dell Laptop.  The CD drive is broke, so I had to use my usb flash drive as a boot device and install Ubuntu on the laptop.  Currently, I don't have an internet connection, even if I use a cable connected to my router.  My network card is a Linksys WPC54G ver. 3, which is supported, according to the wiki.  I tried to use ndiswrapper to install the driver for it.  I have downloaded the ndisgtk, ndiswrapper-common, & ndiswrapper-utils to my flash drive and copied them to my desktop on the laptop.  What do I need to do to unpackage them and install the drivers?

Thanks,

---

### Post by andrewwg94 on 2009-03-24
welcome to the forums.

well, i'm a noob like you, but i'll try to help.

to use ndiswrapper, you need to find the *.inf and *.sys files of your windows driver. (i used winrar to extract them out of the *.exe).

i would definatly try to connect my computer with ethernet first. then i would check for restricted hardware drivers. this is how i got mine to work. although make sure you're intenet is working via ethernet first.

---

### Post by BillyPrefect on 2009-03-24
If you have a Dell, like mine, brace yourself... 

and practice typing the letters "r-m-m-o-d" and "m-o-d-p-r-o-b-e" 

what is your wireless card?

type .. lshw -C network 

if it's a Broadcom, practice the typing above... rmmod b44, rmmod b43, rmmod ssb, modprobe wl, modprobe b43, modprobe b44, modprobe ssb  in that order

---

### Post by cdawley4 on 2009-03-25
> **andrewwg94 said:**
> welcome to the forums.

well, i'm a noob like you, but i'll try to help.

to use ndiswrapper, you need to find the *.inf and *.sys files of your windows driver. (i used winrar to extract them out of the *.exe).

i would definatly try to connect my computer with ethernet first. then i would check for restricted hardware drivers. this is how i got mine to work. although make sure you're intenet is working via ethernet first.
How do I get ethernet working?  I plugged in a cable from the laptop to my router, but when it tries to connect, it can't DHCP an IP address.  Do I need to reinstall Ubuntu with my ethernet cable connected and let Ubuntu see that I have an ethernet cable plugged in?

---

### Post by cdawley4 on 2009-03-25
Hi,

Here are my lspci and lshw -c network files.

> 00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d3)
00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 03)
00:1e.3 Modem: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller (rev 03)
00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)
02:01.0 CardBus bridge: Texas Instruments PCI1510 PC card Cardbus Controller
02:08.0 Ethernet controller: Intel Corporation 82562ET/EZ/GT/GZ - PRO/100 VE (LOM) Ethernet Controller Mobile (rev 03)
03:00.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)

> 
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: 82562ET/EZ/GT/GZ - PRO/100 VE (LOM) Ethernet Controller Mobile
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:02:08.0
       logical name: eth0
       version: 03
       serial: 00:14:22:ba:76:d3
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=e100 driverversion=3.5.23-k4-NAPI firmware=N/A ip=192.168.1.108 latency=64 maxlatency=56 mingnt=8 module=e100 multicast=yes
  *-network
       description: Network controller
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64 module=ssb
  *-network:0 DISABLED
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:14:bf:bc:e5:e4
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg
  *-network:1 DISABLED
       description: Ethernet interface
       physical id: 3
       logical name: pan0
       serial: 12:58:09:08:0a:bb
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes


Is there any way I can connect to the internet to update my computer and get the wireless working?

---

### Post by kevmitch on 2009-03-25
First thing's first. We need to get your wired connection working before we even think of getting wireless working.

When you plug in your ethernet cable, you SHOULD see the swirly connection animation on the network manager system tray applet. Does it stop at some point without connecting, go on forever or just never appear?.

With the ethernet cable plugged in what happens when you enter 

```
sudo dhclient
```

On the command line?

---

### Post by cdawley4 on 2009-03-25
> **kevmitch said:**
> First thing's first. We need to get your wired connection working before we even think of getting wireless working.

When you plug in your ethernet cable, you SHOULD see the swirly connection animation on the network manager system tray applet. Does it stop at some point without connecting, go on forever or just never appear?.

With the ethernet cable plugged in what happens when you enter 

```
sudo dhclient
```

On the command line?
When I ran that command, I got:

> 
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wmaster0: unknown hardware address type 801
SIOCSIFFLAGS: No such file or directory
SIOCSIFFLAGS: No such file or directory
SIOCSIFFLAGS: Operation not supported
SIOCSIFFLAGS: Operation not supported
wmaster0: unknown hardware address type 801
Listening on LPF/wlan0/00:14:bf:bc:e5:e4
Sending on   LPF/wlan0/00:14:bf:bc:e5:e4
Listening on LPF/wmaster0/
Sending on   LPF/wmaster0/
Listening on LPF/pan0/de:6b:c1:a5:05:54
Sending on   LPF/pan0/de:6b:c1:a5:05:54
Listening on LPF/eth0/00:14:22:ba:76:d3
Sending on   LPF/eth0/00:14:22:ba:76:d3
Sending on   Socket/fallback
receive_packet failed on wlan0: Network is down
receive_packet failed on wmaster0: Network is down
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on pan0 to 255.255.255.255 port 67 interval 6
DHCPOFFER of 192.168.1.102 from 192.168.1.1
DHCPREQUEST of 192.168.1.102 on eth0 to 255.255.255.255 port 67
DHCPACK of 192.168.1.102 from 192.168.1.1
bound to 192.168.1.102 -- renewal in 41347 seconds.


Upon typing in that command, I am instantly connected to the internet.  I am going to try restarting the computer to see if I can get an internet connection.

Thanks,

---

### Post by cdawley4 on 2009-03-25
Here's the verdict.  I rebooted my computer and am now using an ethernet connection.  All is working well, upon running the command provided by kevmitch.  Now, I need to get the wireless working.

Thanks,

---

### Post by cdawley4 on 2009-03-25
Hi,

Where is a good place to get b44, b43, wl, & ssb from for my broadcom based wireless card?

---

### Post by kevmitch on 2009-03-25
It sounds like your network manager is slightly screwed. It should be doing the equivalent of that dhclient command automatically when you plug in your ethernet cable. 

Those broadcom modules should come with the generic kernel. From your lshw output, it looks like you even have them loaded already. I'm not an expert in this since I've only played with a broadcom card once, but I do remember having to install b43-fwcutter. You should be able to do that through the synaptic package gui or by entering the command 
```
aptitude install b43-fwcutter
```

It should ask you if you want to download the firmware to which the answer is of course yes. 

First of all do you see the network manager applet in the system tray?
Second, do you see your wired connection and or any wireless connections when you left click this icon? Third, when you right click on the network manager applet do you see two checkboxes "Enable Networking" AND "Enable Wireless"?

If you don't see any wireless in network manager what does

```
iwconfig
```

give you?

---

### Post by kevmitch on 2009-03-25
It's also possible that going to System->Administration->Hardware Drivers will register your broadcom card and set up things like b43-fwcutter for you. If so, then this is probably the most ubuntu way to do things.

---

### Post by kevmitch on 2009-03-25
I guess I should explain some of these commands

```
sudo dhclient
```

is the equivalent of

```
ipconfig /release
ipconfig /renew
```

in windows if you are familiar with those.
 
```
iwconfig
```

is the low-level command line interface to the networking subsystem. Entering the command with no arguments will just list available wireless cards.

---

### Post by cdawley4 on 2009-03-25
I have a small problem.  When trying to install b43-fwcutter, it is asking me for my disk labeled Ubuntu 8.10 _Intrepid Ibex into my CD drive.  The only problem is that I didn't install this with a CD, I installed it via USB Flash Drive.  Can you point me in the right direction, as my CD Drive doesn't work.

Thanks,

---

### Post by kevmitch on 2009-03-26
Mmm that's unfortunate, try going to System->Administration->Software Sources and unselecting the CDROM there.

---

