---
title: "HVR1600 Only works On LiveCD"
date: 2013-12-09
forum: Mythbuntu
---

### Post by 7.11brown on 2013-12-09
Hey All.

I have gotten the Hauppauge HVR 1600 to work on this specific box before, but am struggling to make it go again.  System specs are Dual Core 1.6ghz Atom, 4gb ram.  No Nvida on this computer, so that isn't a conflict.  I have installed the Latest mythbuntu 12.04.3 64 bit.

When booting from the live cd, if I cat /dev/video0 to a test mpg file, there is video as expected.  After the install, if I do the very same thing, I only get a black video.  Digital side of card works just fine--this is only analog

In an effort to replicate the Live Environment, I did a fresh install without a backend installation, then removed the frontend.  The results are the same, with no video.  Running dmesg, the output loads all the correct firmwares. 

Trying to remove the cx18 and cx18_alsa modules, it fails. 

 ```
daniel@DVR:~/Desktop$ sudo rmmod cx18_alsa 
ERROR: Module cx18_alsa is in use
daniel@DVR:~/Desktop$ 

```

I currently have both modules in the blacklist so that they do not load on boot.   Any help or ideas would be greatly appreciated.

Thanks!

---

### Post by 7.11brown on 2013-12-09
Not sure if this is really a solution, but is an action that resolved the problem....I simply swapped the SATA ports that the SSD and HDD were plugged in.

Just curious if anybody has an explanation as to why?

---

### Post by khPWXxF on 2013-12-10
A very tentative hunch.  It's not the total power cycling you will have (or should have) done in order to do the swap is it?
My system will do some really odd things with vga vs hdmi and with Hauppauge firmware if I don't power cycle (ie turn off at wall socket/power supply) after any change.
Proof of the hunch:  Power off completely and swap the disks back (but needs some courage!).

Phil.

---

### Post by 7.11brown on 2013-12-10
So my latest status is as follows: I have video working consistently, but no analog audio--same old problems! Its (oddly enough) my SSD booting too fast! Mythbackend starts before cx18 can fully load, so myth gets confused. The cure for this is blacklisting cx18 & cx18_alsa, stopping the backend, and loading them, and bringing the backend back to life. I also noticed I had configured the analog wrong in myth--its NOT V4L, its MPEG2, didn't see that one!

I'm about to do a fresh reinstall to (hopefully) fix the problem of being unable to rmmod cx18_alsa after even myth was killed.

---

