---
title: "High Xorg-CPU after Interpid upgrade"
date: 2008-11-01
forum: Multimedia Software
---

### Post by ustramooner on 2008-11-01
I recently upgraded to Interpid. Almost everything went perfectly, good work kubuntu!

The 'almost' is that now I have a sluggish machine. I know it's new, so we can expect problems, but I'll post this here to be a good community member anyway :)... plus who knows, someone might help me fix it :)

So... specs are:

```
lspci |grep VGA
gives: 00:02.0 VGA compatible controller: Intel Corporation 82945G/GZ Integrated Graphics Controller (rev 02)
```

```
cat /var/log/Xorg.0.log|grep Module:
(II) LoadModule: "extmod"
(II) LoadModule: "dbe"
(II) LoadModule: "glx"
(II) LoadModule: "freetype"
(II) LoadModule: "record"
(II) LoadModule: "dri"
(II) LoadModule: "intel"
(II) LoadModule: "int10"
(II) LoadModule: "vbe"
(II) LoadModule: "vgahw"
(II) LoadModule: "int10"
(II) LoadModule: "ddc"
(II) LoadModule: "i2c"
(II) LoadModule: "fb"
(II) LoadModule: "exa"
(II) LoadModule: "ramdac"
(II) LoadModule: "evdev"
```

```
cat /proc/version:
Linux version 2.6.27-7-generic (buildd@palmer) (gcc version 4.3.2 (Ubuntu 4.3.2-1ubuntu11) ) #1 SMP Thu Oct 30 04:18:38 UTC 200
```

I also tried with 2.6.24, but no change.


Top gives:
```

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND
 8265 root      20   0  413m  64m 5156 S   16  6.5  11:43.51 Xorg
 8520 ben       20   0  132m  34m  15m R    3  3.4   0:14.66 konsole
 8459 ben       20   0  100m  31m  20m S    1  3.1   0:43.65 plasma
 8554 ben       20   0  341m 186m  26m S    1 18.6   6:42.25 firefox

```

Note that without firefox Xorg is strangely high (~12%). Before upgrade the Xorg process would use about 5%. 

I'm not sure if this is relevant or not, but I'm getting a lot of this:
```

(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) intel(0): Modeline "640x480"x0.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) intel(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) intel(0): Modeline "1024x768"x0.0   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz)
(II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) intel(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) intel(0): Modeline "1152x864"x75.0  104.99  1152 1224 1352 1552  864 865 868 902 -hsync +vsync (67.7 kHz)
(II) intel(0): Modeline "1280x1024"x60.0  108.88  1280 1360 1496 1712  1024 1025 1028 1060 -hsync +vsync (63.6 kHz)
(II) intel(0): EDID vendor "DEL", prod id 16404

```

in the /var/log/Xorg.0.log logs. Every 15 seconds or so, the above lines would be printed out. Seems a bit strange to me.

Let me know if there's anything else I can give to help.

B

---

### Post by MirzaD on 2008-11-02
I have very similar problem, after upgrade to Interpid my Kubuntu seems to take much cpu even when I am not doing anything.
Average cpu temp has risen by 4°C.

When I take a look at the proces table xorg is allways around 5% and 16%.

I also did not have this problem on hardy.

---

### Post by hielscher on 2008-11-03
I have the same problem, using both the ati and the fglrx drivers.  Before the upgrade Xorg used < 10% CPU, now it's at 30% when not displaying anything but the desktop and 60% when playing video in something like vlc.  Thus the system is unusable.

System is a 1.6GHz Pentium M with an ATI Radeon X300.

---

### Post by lizardkinger on 2008-11-05
Same here but with GNOME desktop. Usually the utilization is about 60%. So the mouse cursor constantly stops while moving when I do additional work tasks. 
I'm using the fglrx driver but it also occurs with the radeon driver, also disabling compiz doesn't help.

**I found an ugly workaround for me:**
I killed the gnome-settings-daemon and the utilization is gone: Xorg then only takes 3-5%

Is there already a bug report on launchpad?

System is a 1.7GHz Pentium M with an ATI X600

---

### Post by waydownsouth on 2008-11-09
Don't know if it helps, I've been experiencing similar issues and filed a bug:

[https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/294972]("https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/294972")

Feel free to chip in.

---

### Post by ustramooner on 2008-11-09
I went over to xcfe so that I could continue working. Today I came back to Kde and did an apt-get update. I got a lot of updates, including some around Xorg and kwin. It seems that the update fixed (or at least, vastly improved) the problem. No idea what it was, but good work to whoever fixed it! :)

Still getting lots of those message blocks in Xorg.0.log. Not sure if that's a problem or not.

waydownsouth: I didn't add anything to that bug, because I think it's different - I'm not getting the client rejected line.

---

### Post by m4rqz on 2008-11-11
> **lizardkinger said:**
> Same here but with GNOME desktop. Usually the utilization is about 60%. So the mouse cursor constantly stops while moving when I do additional work tasks. 
I'm using the fglrx driver but it also occurs with the radeon driver, also disabling compiz doesn't help.

**I found an ugly workaround for me:**
I killed the gnome-settings-daemon and the utilization is gone: Xorg then only takes 3-5%

Is there already a bug report on launchpad?

System is a 1.7GHz Pentium M with an ATI X600

Thanks! restarting gnome-settings-daemon actually fixed what restarting the computer did not, thank you!

---

### Post by carlmig on 2008-11-12
My computer is having similar symptoms. After booting, after a while the Xorg process starts hogging the cpu.
If I'm not doing anything, cpu sits between 15% to 30%. If I alt-tab, it gets worse. In fact I can trace it down to rendering on the screen. It really feels that it gets slow when something big has changed on screen. If I keep a key pressed down in some text editor, cpu usage rises...
However if I just move a window, nothing happens, cpu stays the same.

I tried to check what would trigger this behaviour, as it doesn't happen immediately after logging in. In my case it seemed to be triggered by opening a Nautilus window. I disabled Compiz and CPU usage got better. I thought that had fixed it, but no such luck. After a few alt-tabs, etc computer started to freeze...even worse than before. It didn't seem like a complete freeze as I could move the mouse pointer...so I waited...after a few minutes!!! CPU went down as if nothing had happened. Only to happen again later....
I'm not so sure about nautilus being the trigger (or the only trigger)...I'll have to do some more tests, but the fact remains that I can reproduce this, when I open a Nautilus folder.

My CPU is a T9400 @ 2.5 and I have an Nvidia 9600M GT. I'm using the recommended 177 driver.


Btw, killing gnome-settings-daemon didn't work for me.
Any ideas ?

---

### Post by unclebob on 2008-11-17
I am having the same problem with gnome ubuntu intrepid. Intel 965gm hardware. Xorg sucks up 20-30% while the screen is doing basically nothing. :-(

---

### Post by matjoeman on 2008-11-20
I'm having the same problem on Kubuntu after upgrading to Intrepid.  I think it might have something to do with the fact that it thinks I have 2 cores when I really only have 1, I'm pretty sure this started with the upgrade too.  I haven't figured out how to fix that yet.

---

### Post by damis648 on 2008-12-14
I would like to bump this; this just started happening to me today.

---

### Post by noiq on 2009-01-20
I'm quite sure this is neither a problem specific to kubuntu nor to nvidia. I have the same problem here and I'm running xubuntu on an Acer Aspire One with an Intel 945GME. Without anything runnig but an xterm showing top, I get ~15% cpu load for Xorg. I tryed both with and without the hardware accelerated desktop (Compositor).

It really seems to be a problem of Xorg.

Maybe the change to HAL, which came with intrepid could have something to do with this?

---

### Post by qwerty111 on 2009-01-22
I have this problem too. Xorg sits around 20-30% with nothing happening. As soon as I run Firefox or anything else the processor goes to 100%, with xorg and (firefox or whatever) sharing it. Actually I have a dual core amd64 and xorg shows up to 117% cpu in top.

The machine is a hp/compaq 6715b laptop with the fglrx video driver.

I've tried running fluxbox and the problem is still there, so it doesn't seem to be kde related. I haven't tried gnome because we don't get on.

I originally had 8.04 with kde4 installed, and it ran well. I did the upgrade to 8.10 and the problem started. I did a fresh install of 8.10 and the problem is still there.

It's really unuseable. Hopefully someone will have a brain flash and find the answer, otherwise it's back to 8.04 for me after the weekend!

---

### Post by vinodkhare on 2009-01-25
I have a compaq b1200 laptop and I'm having a similar problem. Xorg is using nearly 300 MB of memory and 20-30% cpu. When I restore a window, there is visible time delay between the appearance of the titlebar and the actual window contents. Scrolling and tab switching on firefox are just plain unusable.

Does anyone have a cure for this yet? :(

---

### Post by noiq on 2009-02-07
I am not sure if the cause of my problem was the same, but for me this thread

[https://wiki.ubuntu.com/X/Troubleshooting/HighCPU](https://wiki.ubuntu.com/X/Troubleshooting/HighCPU)

helped a lot to search at the right place. Using **powertop** I saw that my xfce plugins (like mixer, cpu-graph and net-graph) cause a lot of wake-ups. Closing all of them brought my Xorg back down to 2-3% cpu load (instead of ~15%, that I had before). So the problem was **not** Xorg.

---

### Post by qwerty111 on 2009-02-10
I'm not sure about plugins. fluxbox showed the problem for me with only an xterm running. Actually it showed the problem just logging in. There could have been KDE or Gnome services running in the background I suppose. Anyway, I couldn't use it - so I reinstalled 8.04 and it's running fine again.

---

### Post by carlmig on 2009-02-10
My problems just disappeared afeter installing the new nvidia driver 180.
I know some of you are using other cards and also experiencing these problems, but hopefully this will solve the problem of the nvidia card holders.

Cheers

---

### Post by ustramooner on 2009-02-27
Well... after several months of an almost unusuable computer (after trying Gnome, Kde, Xfce, etc) and very high CPU usages for X I reinstalled Ubuntu again... BUT...... This time I installed from a Ubuntu CD instead of a Kubuntu CD... everything now flies!!! Xorg sits on around 4-8 even with a whole bunch of applications open.

Actually, it's not just me. Everyone at my work who uses Ubuntu had installed from a Kubuntu CD (and at home for several people as well) have been complaining about speed (nothing quite as extreme as my home computer though). They have all now reinstalled using an Ubuntu CD and said what a massive difference it made.

I don't know what is different on that CD (doesn't make any sense to me) but I really recommend reinstalling from an Ubuntu CD if you installed from a Kubuntu CD and are having problems.


Hope this post helps some people


Cheers
Ben

---

### Post by djtm on 2009-03-20
Edit: Sorry, I think this is not the same problem probably.

(There's actually a fix available. It worked great for me, finally!!!!!!!! :)
Check this [http://linux-tipps.blogspot.com/2009/03/fixing-high-latency-with-kde4-display.html]("http://linux-tipps.blogspot.com/2009/03/fixing-high-latency-with-kde4-display.html") and see if it helps.)

---

