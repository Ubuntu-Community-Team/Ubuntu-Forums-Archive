---
title: "broadcom on compaq v2000"
date: 2009-05-16
forum: Networking &amp; Wireless
---

### Post by ixifx on 2009-05-16
I've tried linux before with knoppix and ubuntu briefly, but I'm still pretty much a noob.  I've been running the liveCD for xubuntu 9.04.  everything works great, except for the wireless.  if I can get that working, I will totally ditch windows on my laptop.  

I have wireless access from my apartment, but no wired, or I'm almost positive I could have gotten this working.

I have gotten to [ [here]("http://s614.photobucket.com/albums/tt221/jcbelvin/?action=view&current=hardwaredrivers.png") ]where I activated the software modem, and the gold-looking icon appeared in the top right of the screen, but when I try to activate the wireless card, it gives a message that it is downloading, stays at 0% and then gives the error message box shown in the screen capture.

I'm wondering if there is a package or something I can download, put on my flash drive and test it in the liveCD environment.

any and all help greatly appreciated.

---

### Post by ixifx on 2009-05-19
ubuntu@ubuntu:~/Desktop$ lshw -C network
WARNING: you should run this program as super-user.
  *-network:0             
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: eth0
       version: 10
       serial: 00:16:36:5b:12:89
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=8139too driverversion=0.9.28 latency=64 maxlatency=64 mingnt=32 module=8139too multicast=yes
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
       physical id: 2
       logical name: wlan0
       serial: 00:14:a5:a6:f2:24
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg
  *-network:1 DISABLED
       description: Ethernet interface
       physical id: 3
       logical name: pan0
       serial: 22:2a:29:a2:58:34
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes


I've tried several guides to setting this up, and none seem to be working.  after looking at the output of that command, I believe it has to do with the on/off button just not working.  I found the following in a faq on linuxwireless.org, but it doesn't make much sense to me, being virtually completely new to linux

Q: The radio-enable-button on my laptop does not work.

A: You have to enable RF-kill support in the kernel configuration. The config options you have to enable are: CONFIG_RFKILL, CONFIG_RFKILL_INPUT, CONFIG_INPUT_POLLDEV.

the lshw command was run after doing my best to follow information found [here]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#head-bc33832c0547766a33c3a84f13f971ca757b2851").

again, any and all help is greatly appreciated =)

---

### Post by superprash2003 on 2009-05-19
try this [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)

---

### Post by ixifx on 2009-05-19
I tried that one, too lol =)

I ended up going to a friend's and hooking up to the LAN.

just installed the fwcutter and was able to get the files it needed for the firmware off the net.

everything is running beautifully so far

and no more windows.

---

