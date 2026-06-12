---
title: "video redlines cpu"
date: 2008-04-23
forum: Multimedia Software
---

### Post by mar\/in on 2008-04-23
Total linux n00b here.  Just installed the 8.04 release candidate two days ago.  Please forgive me if this question is done to death...

So far any video I try to play redlines the cpu, then starts stuttering and balking until it's unwatchable.  So far I've tried some Xvid .avi files and a Quicktime .mov under using Totem, Mplayer, and VLC.  I believe I've downloaded the special restricted codecs and plug-ins correctly.  (As best I can tell, anyway.)  The files usually start OK, look great for about five or 10 seconds, and then gasp to a standstill as the CPU usage goes up to 100%.  The memory and swap files don't appear to be hit particularly hard according to the system monitor.  Usually the sound continues playing while the video stutters to a halt.

I have the same problem with Firefox 3 Beta 5 and the various flash plugins (I've tried something called gnash and now I'm using the latest restricted Adobe Flash plugin from the package manager.)  The difference here is that the sound stutters, too, while Firefox eats up the cpu.  (I see there are other topics about firefox & flash, but I don't see them accompanied by video woes in general.)

I'm starting to wonder if its not the software but the hardware, or the video driver.  The laptop I'm using (specs in the sig) has an old Radeon Mobility 7500, so I don't think it's eligible for the current ATI driver.  Any thoughts or points in good directions would be nifty.

---

### Post by overdrank on 2008-04-23
> **mar\/in said:**
> Total linux n00b here.  Just installed the 8.04 release candidate two days ago.  Please forgive me if this question is done to death...

So far any video I try to play redlines the cpu, then starts stuttering and balking until it's unwatchable.  So far I've tried some Xvid .avi files and a Quicktime .mov under using Totem, Mplayer, and VLC.  I believe I've downloaded the special restricted codecs and plug-ins correctly.  (As best I can tell, anyway.)  The files usually start OK, look great for about five or 10 seconds, and then gasp to a standstill as the CPU usage goes up to 100%.  The memory and swap files don't appear to be hit particularly hard according to the system monitor.  Usually the sound continues playing while the video stutters to a halt.

I have the same problem with Firefox 3 Beta 5 and the various flash plugins (I've tried something called gnash and now I'm using the latest restricted Adobe Flash plugin from the package manager.)  The difference here is that the sound stutters, too, while Firefox eats up the cpu.  (I see there are other topics about firefox & flash, but I don't see them accompanied by video woes in general.)

I'm starting to wonder if its not the software but the hardware, or the video driver.  The laptop I'm using (specs in the sig) has an old Radeon Mobility 7500, so I don't think it's eligible for the current ATI driver.  Any thoughts or points in good directions would be nifty.

HI and welcome, I believe the driver that comes with Hardy should be antiquate for that graphics card. You may try and configure you xorg with this command in the terminal ```
sudo dpkg-reconfigure -phigh xserver-xorg
``` Then restart x with the keys ctrl, alt, backspace bar. Hopefully this will correct the issues and you may want to view which driver is being used with this command ```
cat < /etc/X11/xorg.conf |grep Driver
``` and I believe you should see ATI.

---

### Post by mar\/in on 2008-04-23
> **overdrank said:**
> HI and welcome, I believe the driver that comes with Hardy should be antiquate for that graphics card. You may try and configure you xorg with this command in the terminal ```
sudo dpkg-reconfigure -phigh xserver-xorg
``` 

Thank you!  Google tells me that this command should give me an opportunity to fiddle with video preferences, but here's what I see when I run the command:

```
marvin@marvin-laptop:~$ sudo dpkg-reconfigure -phigh xserver-xorg
[sudo] password for marvin: 
xserver-xorg postinst warning: overwriting possibly-customised configuration
   file; backup in /etc/X11/xorg.conf.20080423072727
marvin@marvin-laptop:~$ 
```

> **overdrank said:**
> Then restart x with the keys ctrl, alt, backspace bar. Hopefully this will correct the issues and you may want to view which driver is being used with this command ```
cat < /etc/X11/xorg.conf |grep Driver
``` and I believe you should see ATI.

Ctrl Alt Backspace didn't seem to do anything.  Here's what I see when I run the second command:

```
marvin@marvin-laptop:~$ cat < /etc/X11/xorg.conf |grep Driver
	Driver		"kbd"
	Driver		"mouse"
	Driver		"synaptics"
marvin@marvin-laptop:~$ 

```

---

### Post by overdrank on 2008-04-23
Ok then you may try the the command without the -phigh tag
```
sudo dpkg-reconfigure xserver-xorg
``` And you can choose your driver there.

---

### Post by mar\/in on 2008-04-23
> **overdrank said:**
> Ok then you may try the the command without the -phigh tag
```
sudo dpkg-reconfigure xserver-xorg
``` And you can choose your driver there.

A-ha!  That did the trick.  It allowed me to turn off kernel frame buffering so the driver could access the hardware directly (or that's the gist of the explanation it gave me).  (It also asked me to make a bunch of choices about keyboard configuration.)

Anyway...the cpu now appears to be hit in proportion to the resolution and framerate of the video in question, and although there is a rare stuck frame in the HD video, things seem to be running smoothly in totem and Mplayer both.

Many thanks.  \\:D/

---

