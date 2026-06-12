---
title: "Buy advice:Need workng 802.11g+ or n USB WLAN  under Ubuntu 8.10 64 bit!"
date: 2009-01-31
forum: Networking &amp; Wireless
---

### Post by makrophage on 2009-01-31
Hi!

I have installed Itrepid 8.10 [COLOR="Red"]64-bit[/COLOR]! and i need a working USB Wlan stick, at least (g+ or n) which is supported by Ubuntu.

My former TP-Link TL-WN620G USB does not work (i díd all instructions which were mentioned in the ndiswrapper guides) seems to be cuz of my 64 bit system, even through a Windows 64 drivers exists!
If ur interested i get the same error as the guy here:
[http://ubuntuforums.org/showthread.php?t=553729](http://ubuntuforums.org/showthread.php?t=553729)

Here the info i get from Ubuntu:
lsusb
Bus 008 Device 007: ID 0cf3:0002 Atheros Communications, Inc. AR5523 (no firmware)

As the Vista x64 driver is installed i get this ok message:
locutus@Collective:~$ ndiswrapper -l
netathrxusb : driver installed
    device (0CF3:0002) present

But when i type: 
locutus@Collective:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.


So now to my core question (if u can solve my problem above i would be truly happy but i doubt)
Which 802.11g+ or n USB Wlan has someone got to run under Ubuntu Intrepid with 64 bt?
Can u post the brands so i can buy one to get my internet connection running.

ty in advance!

---

### Post by makrophage on 2009-02-01
Can it be that NOBODY has a working USB WLAN under Ubuntu 8.10 64 bit???? Looks like a hotfix for the new ubuntu release...

---

### Post by Reiger on 2009-02-01
Some ASUS draft-n dongle. Used ndiswrapper with the XP drivers and Wicd for connection manager. That kind of works; altough rumour (the ASUS site, actually) has it there are Linux drivers for it out there. Unfortunately I could not get it to work using those drivers... :(

---

