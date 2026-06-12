---
title: "faint horizontal shadows"
date: 2006-06-04
forum: Multimedia &amp; Video
---

### Post by ubuntu_demon on 2006-06-04
Hi.

My applications cast (very) faint horizontal shadows. I don't like this. It's ugly. 

Most of the time I have had dark backgrounds. I guess that's the reason I didn't discover this before.

I have an asus geforce 3 ti 200 videocard. I have tried both the nvidia and nv driver. 

This is the result of 
$lspci :
> 
0000:00:00.0 Host bridge: Intel Corporation 82865G/PE/P DRAM Controller/Host-Hub Interface (rev 02)
0000:00:01.0 PCI bridge: Intel Corporation 82865G/PE/P PCI to AGP Controller (rev 02)
0000:00:1d.0 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 (rev 02)
0000:00:1d.1 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 (rev 02)
0000:00:1d.2 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3 (rev 02)
0000:00:1d.3 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4 (rev 02)
0000:00:1d.7 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02)
0000:00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c2)
0000:00:1f.0 ISA bridge: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge (rev 02)
0000:00:1f.1 IDE interface: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller (rev 02)
0000:00:1f.3 SMBus: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller (rev 02)
0000:00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
0000:01:00.0 VGA compatible controller: nVidia Corporation NV20 [GeForce3 Ti 200] (rev a3)
0000:02:03.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev 80)
0000:02:04.0 RAID bus controller: VIA Technologies, Inc. VT6410 ATA133 RAID controller (rev 06)
0000:02:05.0 Ethernet controller: 3Com Corporation 3c940 10/100/1000Base-T [Marvell] (rev 12)


I've attached a screenshot. Look carefully and you'll see. It's only very faint but once you see it you can't stop noticing it.I most easily notice it when moving the a window in front of this wallpaper.

It's not related to XGL or something because both of my Dapper installations(seperate partitions) face the same problem (and in one of them I've never done anything with XGL).

I'm also seeing it in a lower resolution and at lower refresh rates.

I've tried reconfiguring xserver-xorg. 

I am having the same problem running from the breezy live cd so this is probably my monitor that's getting older :(.

I've lowered my contrast and the problem has become less irritating :).

---

### Post by sparX CG on 2006-06-04
I don't see anything wrong with your screenshots...  Are you sure it's not just you monitor?  They sometimes do that. ;)

---

### Post by ubuntu_demon on 2006-06-05
> **sparX CG]I don't see anything wrong with your screenshots...  Are you sure it's not just you monitor?  They sometimes do that.  said:**
> 
thnx for the reply. Yeah I discovered it was probably my monitor a bit after posting this thread.

[quote=ubuntu_demon]
I am having the same problem running from the breezy live cd so this is probably my monitor that's getting older . :(

I've lowered my contrast and the problem has become less irritating. :)


---

### Post by tseliot on 2006-06-05
Try decreasing the colour depth in your xorg.conf, restart the xserver and see if anything changes

---

### Post by ubuntu_demon on 2006-06-05
[QUOTE=tseliot]Try decreasing the colour depth in your xorg.conf, restart the xserver and see if anything changes[/QUOTE]
thnx for the suggestion. I tried it on 8 bit and the problem remains.

It definetely looks like it's my monitor.

---

### Post by robert114 on 2006-10-25
Is it simulair to this behaviour wich i'm having take a look at the picture from the link

[http://ubuntuforums.org/attachment.php?attachmentid=18163&d=1161768210]("http://ubuntuforums.org/attachment.php?attachmentid=18163&d=1161768210")

---

### Post by factotum218 on 2006-10-26
sorry, delete this if you want. My bad

---

### Post by factotum218 on 2006-10-26
Yeah, I have the same problems with my other monitor. All I could do to remedy it was lower the contrast and the refresh rate. As far as I can tell it's the hardware/monitors fault.
If I have the monitor set at 1200x1600 and anything over 80hz I get lines no matter what graphics card I try using. If I run it at 1280x960 its fine at any refresh rate.

---

### Post by robert114 on 2006-10-26
that's weird, because I didn't have this problem with dapper drake!
and when I restart my X server the problem is over.

So I don't think it is an hardware problem

Ubuntu_demon do you think you've got the same problem?

---

### Post by ubuntu_demon on 2006-10-27
My problem was definetely my monitor getting old.

---

### Post by handy on 2006-10-28
> **ubuntu_demon said:**
> My problem was definetely my monitor getting old.

This is pretty funny you know, when you've got us all looking at screen shot's of your monitor on our monitors trying to diagnose your monitor... :D

---

### Post by ubuntu_demon on 2006-10-28
> **handy said:**
> This is pretty funny you know, when you've got us all looking at screen shot's of your monitor on our monitors trying to diagnose your monitor... :D
LOL yeah. But this thread is quite old and suddenly got back into live :-D

---

### Post by robert114 on 2006-11-02
I solved my problem by switching from 64bit to 32 bit, very weird

---

