---
title: "3D Mapping Issues with Nvidia."
date: 2007-08-28
forum: Multimedia &amp; Video
---

### Post by Amof on 2007-08-28
Ok well I have been having a problem with my 3D applications on Ubuntu ever since I started using it. It's really hard to explain exactly what happens but it appears to be some sort of distortion when the 3D object is skinned (Picture below). I have tried many different remedies to no avail. I have tried out different versions of video drivers for my card. Including the official drivers and the x.org drivers. I have also tried many modifications to my xconf file. After doing extensive research I have found almost nothing! Please! Someone at least give me a lead on how to fix this annoying graphical issue!

Anyways, here is a list of applications where I experience problems.

Quake 3

Beryl

Second Life

Tux Racer

Diablo 2 (3D Mode)

I only seem to have problems in the skinning department because I have tried glxgears with no issues.

here is a lspci:

```
00:00.0 Host bridge: VIA Technologies, Inc. VT8377 [KT400/KT600 AGP] Host Bridge

00:01.0 PCI bridge: VIA Technologies, Inc. VT8235 PCI Bridge

00:0a.0 Multimedia audio controller: Creative Labs SB Audigy LS

00:0a.1 Input device controller: Creative Labs SB Audigy LS Game Port

00:0b.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)

00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)

00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)

00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)

00:10.3 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 82)

00:11.0 ISA bridge: VIA Technologies, Inc. VT8235 ISA Bridge

00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)

01:00.0 VGA compatible controller: nVidia Corporation NV43 [GeForce 6600 GS] (rev a2)
```



[IMG]http://i16.photobucket.com/albums/b13/Yotoadaki/Screenshot-1.png[/IMG]

I have heard that my problem might be from some buggy drivers that have issues with my VIA chipset. I also heard that it might have something to do with Mesa. I'm really at a dead end here. 

Please help! Thanks!

---

### Post by tseliot on 2007-08-28
try asking here:
[http://www.nvnews.net/vbulletin/forumdisplay.php?s=&forumid=14](http://www.nvnews.net/vbulletin/forumdisplay.php?s=&forumid=14)

---

### Post by Amof on 2007-09-05
I look forward to the day that I can register on the forums. Every attempt I make I get the error "Your email address has been banned." I have never been there before ether.



So anyone else got any ideas?

---

### Post by Amof on 2007-09-06
Does anyone have the least amount of info on this problem? This is really the only thing holding me back from getting rid of Windows all together. Has anyone even seen a problem that looks remotely like this?


I'm getting gray hairs. :(

---

### Post by Amof on 2007-09-06
Ok! Well I have a bit more news. If you look at my pcils above you will see that is says I have a "[GeForce 6600 GS] (rev a2)" for a video card. It just so happens that that is not the correct version of my card. I have a 6800 XT (Confirmed on video bios). Could this be affecting it? Or is it just 101 of today's bug list?


RESPONDERS WILL RECEIVE A COOKIE!

---

