---
title: "Sluggish Totem Movie Player when Virtualbox is running"
date: 2008-05-10
forum: Multimedia Software
---

### Post by austin1030 on 2008-05-10
Hi

After I install Ubuntu Hardy 8.04 server (btw, my machine failed to install desktop for some reason), I can't seem to watch a movie (avi format) on Totem player while Virtualbox is running. 

When I play a video when Virtualbox is running, my video is running very sluggish (frame by frame). However, when I turn Virtualbox off, then movie plays fine. 

Does any one has same or similar problem and how did you solved it?

thanks

Austin
---------------------------
Well, I've been search for solution and I figure out that installing NVIDIA driver done by Envy (which I love the effort) causing the problem. When I reinstall Ubuntu and install native NVIDIA driver that can be installed by going System->Administration->Hardware Drivers.

This eliminated all my sluggish problem. I guess native NVIDIA driver is far better than Envy one.

Hope this help

Austin

---

### Post by ladr0n on 2008-05-11
I tried to duplicate this on my laptop running Hardy Desktop.  I didn't have any problems with either the video or the performance of the VM.

That is possibly due to the limited capabilities of your computer.  Running a vitual machine and watching a video both take a good deal of processing power and RAM, so together, it might just be more than your system can handle.  (My laptop has 2GB RAM and a 2.2 GHz dual-core processor)

Also, the problem might have something to do with the fact that you're using server rather than desktop.  The server edition uses a different kernel optimised for server performance, which could degrade from the performance of desktop apps (such as video viewing) especially while running server-type apps (such as a VM)

---

### Post by austin1030 on 2008-05-11
> **ladr0n said:**
> I tried to duplicate this on my laptop running Hardy Desktop.  I didn't have any problems with either the video or the performance of the VM.

That is possibly due to the limited capabilities of your computer.  Running a vitual machine and watching a video both take a good deal of processing power and RAM, so together, it might just be more than your system can handle.  (My laptop has 2GB RAM and a 2.2 GHz dual-core processor)

Also, the problem might have something to do with the fact that you're using server rather than desktop.  The server edition uses a different kernel optimised for server performance, which could degrade from the performance of desktop apps (such as video viewing) especially while running server-type apps (such as a VM)

Hey ladr0n

Thanks for your response.

I'm not quite sure I have issue on the limitation of my hardware. Here is my machine's spec.

AMD Athlon 64 3500Mhz (it can run 64bit OS)
4GB of RAM
60GB PATA, 200GB SATA, 250GB SATA, and 300 SATA
256MB Nvidia GeForce 6600 video card

I don't think my machine has any limitation that might cause this problem. I think it might have to do with Nvidia driver or some thing else. Here are few facts that support my idea.

1. This problem never has on 7.04 or 7.10 version (desktop and server)
2. My current laptop running 8.04 desktop version and has same problem.

My laptop is
Dell Latitude D620
2GB of RAM
80GB HDD
256MB Nvidia video card

Don't you think if there is another issue may cause the problem I have?

thanks

Austin

---

### Post by rashtao on 2008-05-16
hi
I have the same problem on my laptop. This is my hw:
Acer 5720
Centrino Duo 5250 @1500
ram 2GB
video card: Intel GM965

My OS: 
Ubuntu 8.04 desktop
FS: reiserFS

installed package: 
virtualbox-ose.deb (v. 1.5.6-dfsg-6ubuntu1)
virtualbox-ose-modules-2.6.24-16-generic.deb


So I don't think it's a problem with Nvidia video cards...

---

### Post by cor2y on 2008-05-16
I have the latest virtualbox running and i can run audio and video in both ubuntu and on vm at the sametime with no system slowdowns.
My specs
Ubuntu 8.04 32bit edition
Virtualbox 1.6.0 (closed source version not OSE)

My specs
AMD 64 X2 4000+
2gb of Ram (I forgot what kind)
Nvidia 512mb 8600gts (with closed source nvidia driver)

The problem may be the settings for the VM.
Example i have the system ram at 221 and video ram at 8mb in the virtualbox settings i haven't taken it higher because i have no need to.
Try messing around with those settings also what are you trying to run in the vm Xp or vista?

---

### Post by rashtao on 2008-05-25
I have the same problem on my desktop pc...

CPU: intel Dual Core E2140 @ 2800 MHz
RAM: 2GB @ 800 MHz
Video: Nvidia 7300 GS 256 MB (proprietary drivers)
HD: Seagate Barracuda 320 GB

The installed SW is the same I installed on my laptop (Ubuntu 8.04 + VirtualBox OSE...)

So I don't think it's a problem regarding hw performances...
It could be a SW bug, maybe concerning the OSE edition...

PS: in the Virtual Machine I'm running WIN XP Prof. SP2

---

### Post by rykel on 2008-06-08
Hi guys,

I also have Virtualbox installed and my Totem would perform great but turn sluggish after a while, but I personally don't think my problem is related to Virtualbox - simply because Virtualbox is NOT running when the sluggish slowdown in Totem occurs. Virtualbox does NOT run in the background or autostart with the system, I hope!

I have BOTH totem-xine and totem-gstreamer though - something which would NOT have happened in older versions of Ubuntu. They used to be mutually exclusive, so I am not sure why I am able to install both versions on Hardy. This co-existence MIGHT be the problem...

I am now uninstalling totem-gstreamer without logging off to see if I can restore the video performance.

btw, I think in my case, the sluggishness takes place when Bittorrent is running hard and fast, but I cannot be very sure, since turning off BT sometimes solves the problem, sometimes NOT.

Thanks for helping!!

This sluggish issue is annoying me!

---

### Post by morris.johns on 2008-10-14
I went into VirtualBox settings and the audio driver was set to ALSA - changed to PulseAudio and the problem was fixed immediately!

Yayyy - this has been annoying me for months :)

From: "When I set Host Audio Driver of VirtualBox VM to PulseAudio, problem disappeared." from [http://ubuntuforums.org/showpost.php?p=5952184&postcount=7](http://ubuntuforums.org/showpost.php?p=5952184&postcount=7)

---

