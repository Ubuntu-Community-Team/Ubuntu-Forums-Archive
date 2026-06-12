---
title: "Newbie - wifi and WPA"
date: 2010-03-19
forum: Networking &amp; Wireless
---

### Post by tcedinburgh on 2010-03-19
Hi

I am a complete beginner at ubuntu etc and was curious at what it could do - using an old (5 year) laptop with XP loaded I installed wubi to save altering partitions etc. It all downloaded fine and connected to the internet by wire. I set up the wireless connection using WPA but could not connect. The wirelsss card does see my network and others. After lurking around the forum and trying various things I found that I could connect without encryption. The more I read the more I became confused.
Anyway what I could glean about my Wireless Card it is a 
Intersil Prism2 mini usb adapter - but also shows up as an Acer ?? Warplink  802.11.

using lshw I found this reference to wireless
 
*-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:01:24:b3:8b:7b
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11-DS

using lsusb  I found this
*-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:01:24:b3:8b:7b
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11-DS
tom@ubuntu:~$ lsusb
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 004: ID 0967:0204 Acer (??) WarpLink 802.11b Adapter
Bus 003 Device 002: ID 046d:c501 Logitech, Inc. Cordless Mouse Receiver
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

I became even more confused and got a bit lost using the various codes in the terminal and looking up things about drivers etc  but would like to persist.

Could some one help? - Sorry for such a long 1st post.

Tom

---

### Post by tcedinburgh on 2010-03-28
After doing some reading it seems that my wifi card is not compatable with WPA in Linux - so I have ordered an Edimax EW7108PCG PCMCIA card to insert into my laptop. I will keep you posted on another thread that I have running.

---

