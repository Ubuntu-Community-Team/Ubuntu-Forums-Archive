---
title: "WiFi trouble, Realtek 8188CE"
date: 2013-02-25
forum: Networking &amp; Wireless
---

### Post by wisecat on 2013-02-25
I've solved my WiFi problem already, but thought I'd share the solution here for anyone else having this difficulty.

PROBLEM: WiFi not working in Ubuntu 12.04, even though it >SEEMS< like the right driver is installed 
SOLUTION: Compile & install driver from source code, downloaded from Realtek website.  (do NOT use the binary downloaded from the website, though!)

Details:---------------

typing:  sudo lshw -C network

reveals:

*-network               
       description: Network controller
       product: RTL8188CE 802.11b/g/n WiFi Adapter
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=rtl8192ce latency=0
       resources: irq:16 ioport:3000(size=256) memory:f0200000-f0203fff


note the driver listed, rtl8192ce, is indeed the correct one.  However, looking closely, you will notice that not ALL of the information is there in the listing.  I did a comparison with a working one (from Ubuntu 12.10, which installs with working WiFi right off the bat, on the same machine), and noticed that some info was missing, indicating that perhaps the operating system wasn't FULLY engaging the WiFi card.

Reinstalling the driver (binary) downloaded from Realtek website DID NOT WORK.
SOLUTION: Reinstall a FRESHLY COMPILED driver, downloading the SOURCE code from the Realtek website.  Works great now!

now typing: sudo lshw -C network
reveals:

*-network               
       description: Wireless interface
       product: RTL8188CE 802.11b/g/n WiFi Adapter
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 01
       serial: 20:16:d8:3c:d1:0b
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rtl8192ce driverversion=3.5.0-25-generic firmware=N/A ip=192.168.1.9 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
       resources: irq:16 ioport:3000(size=256) memory:f0200000-f0203fff

which matches what appears in Ubuntu 12.10, where the WiFi works without any hassle.

If you need step-by-step directions, I'll have to hunt down the link and post it here.
------------------------------------
This was a really frustrating problem! It took me hours. I am surprised that it worked, in the end!  I thought that recompiling from source code was a long shot, at best, for a solution.

Specs:
Computer: Toshiba Satellite C855D-S5320 (laptop)
Processor: AMD E2-1800 APU with Radeon(tm) HD Graphics x2
Graphics: AMD Radeon HD 7340 (driver not currently working, so in fallback mode)
WiFi: Realtek 8188CE 802.11b/g/n WiFi Adapter
Operating System: Ubuntu 12.04 LTS, and dual boot with Ubuntu 12.10

---

### Post by ErikMAkkerman on 2013-03-09
Yes, Wisecat, I really woud like to have your step-by-step instructions. I'm using an MSIu270 with a rtl8188ce which is not working properly. So I would like to try your solution!

---

### Post by vadertater on 2013-03-11
**I second EricMAkkerman! **

---

### Post by Supergoose on 2013-07-02
I realize that this is a bit old, but it seems people are still having trouble with this card (myself included).  Getting the latest driver from Realtek seems like a reasonable course of action.

Here is blog post with the relevant procedure.  It is basically just telling you to do what the readme in the driver source tells you to do.
[http://www.perseosblog.com/en/posts/solving-connection-problem-with-realtek-wifi-card-rtl8188ce-rtl8192ce-rtl8191se-and-rtl8192de-on-debian-ubuntu-and-derivatives/](http://www.perseosblog.com/en/posts/solving-connection-problem-with-realtek-wifi-card-rtl8188ce-rtl8192ce-rtl8191se-and-rtl8192de-on-debian-ubuntu-and-derivatives/)

Here is a bug report:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/902557](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/902557)

Here are a few notes:
To get the driver source on the Realtek webpage,

Clicked on Downloads

Navigate the pull down menus:

Communications Network ICs > Wireless LAN ICs > WLAN NIC > IEEE b/g/n 802.11 Single chip > Software

Selected my wireless card.

Selected the linux version of the driver for the newer kernels.

I only just did this so it remains to be seen whether it actually helps.  I'm running 64-bit 12.04 on a Lenovo X220 with the Realtek 8188ce chipset.
Good luck,
Spencer

---

