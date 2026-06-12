---
title: "Boot fails when I put in my video card."
date: 2009-07-13
forum: Multimedia Software
---

### Post by mcinto16 on 2009-07-13
Hi, I'm at a bit of a loss as to what is going on with my system. It works fine with the onboard video, but once I put in my video card, (e-GeForce FX 5200), it crashes during the splash screen.

Like I said, it boots fine with the video card out, or with BIOS set to the onboard, but if I try to boot with the card, it hangs for a bit on the splash screen and then spits errors to the screen ending with this:

```
init: Unable to execute "/sbin/getty" for tty3: No such file or directory
init: Unable to execute "/sbin/getty" for tty6: No such file or directory
init: Unable to execute "/sbin/getty" for tty1: No such file or directory
init: tty4 main process (1490) terminated with status 255
......
init: tty1 main process (1496) terminated with status 255
init: tty1 main process ended, respawning
init: tty1 main respawning too fast, stopped
```

I tried booting with my livecd USB to play around with it, but it also fails with a different error (again, only with the graphics card):

```
* Loading hardware drivers...
udevd-event[3714]: '/bin/mkdir /var/run/network' abnormal exit
```

I've been searching around the net but haven't found anything quite like what I have here. Is my graphics card defective, or is this some sort of incompatibility? I'm not a linux expert, and really, I'm lost and any help would be great.

Thanks!

---

### Post by overdrank on 2009-07-13
Hi and welcome, are you able to disable the onboard graphics and then boot with the nvidia card?
 If the onbard graphics are ati have removed the drivers before installing the nvidia card?

---

### Post by mcinto16 on 2009-07-13
I can disable the onboard graphics and boot with the nvidia, that is when I get the failure. Everything starts up fine if I only use the onboard.

The onboard is a Intel GMA 950. I initially installed ubuntu 9,04 without the nvidia card in, and when I did install it and started getting the failures, I figured I should try reinstalling ubuntu, which is when I discovered that I also had boot failures with the livecd.

---

### Post by kahlil88 on 2009-07-13
I had a similar problem awhile back. I think booting into recovery mode and running **sudo dpkg-reconfigure xserver-xorg** should set you straight.

---

### Post by overdrank on 2009-07-13
To add to kahlil88, have you tried any of the options under F4 when booting the live cd as for the resolution I believe.

---

### Post by mcinto16 on 2009-07-13
Wow. I tried booting into recovery and got this:
```
EXT3-fs warning (devices sda1): dx_probe: dx entry: limit != root limit
EXT3-fs warning (devices sda1): dx_probe: Corrupt dir inode 1859593, running e2fsck is recommended.
/bin/sh: 6: /sbin/sulogin: Stale NFS file handle
init: rcS-sulogin main process (1489) terminated with status 2
```

Again, I tried with just the onboard graphics and it worked fine. 
Thanks for the advice, but I ran that command, tried again with the nvidia card, and got the same original failure.

---

### Post by mcinto16 on 2009-07-13
huh.
tried booting with F4 graphics safe mode and got the same error:
```
* Loading hardware drivers...
udevd-event[3714]: '/bin/mkdir /var/run/network' abnormal exit
```

I am at a bit of a loss. Maybe I'll shove the card into something else and at least see if it's the hardware or the software.

---

### Post by mcinto16 on 2009-07-13
I tried the card in my other windows computer and it booted fine. So at least I've eliminated the card as the problem.

---

