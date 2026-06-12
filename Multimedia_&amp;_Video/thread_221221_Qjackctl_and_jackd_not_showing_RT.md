---
title: "Qjackctl and jackd not showing RT"
date: 2006-07-22
forum: Multimedia &amp; Video
---

### Post by rasears on 2006-07-22
I've been trying to get jackd to run in RT mode, but haven't been having alot of luck. Using the default ubuntu 6.06 amd64 kernel with CONFIG_PREMPT and the limits.conf changes mentioned in the Dapper setup page, neither qjackctl with Realtime checked nor jackd with -R indicate that RT is enabled (the RT is not illuminated in qjackctl and jackd mentions nothing about realtime in -v output). I also get XRuns, even with the period set at 1024.

I also tried recompiling the kernel with the RT patches, and the only result of that was an unstable system (90% of the time, when the nvidia module was loaded it would hang the system). The nvidia module must have some issue with the patch...anyone else get that running with an Nvidia card with 2.6.17? I've also tried the 2.6.16.27 kernel with CONFIG_PREEMPT and timers set to 1000, and while it is stable and functional, it still doesn't change qjackctl or jackd issues with RT mode. I can run jackd with the period as low as 512 without too many overruns, but that's 23 msec latency and I think I ought to be able to do better.

Does the RT patch have to be applied for jackd -R to work, or should it work with the Ubuntu standard CONFIG_PREEMPT? I should be able to tell that realtime is enabled from the jackd -v output, correct?

My system is:
AMD64 X2 3800
Asus A8V Deluxe
1.5 GB RAM
Nvidia 6600GT
M-Audio Quattro USB audio

---

### Post by dolson on 2006-07-24
You're right, it doesn't make sense. But I don't have experience with a USB sound card... Is it possible that this is normal for USB devices?

No, you do not need the -rt patch for jackd -R to work. To get realtime access, you need a kernel >= 2.6.12, as well as PAM with the limits.conf changes (realtime-lsm, setrlimits, or sudo also work but are less than ideal).

Either way, the RT indicator on QjackCtl looks faded when it is enabled, and I don't know why that is. But when you don't have RT, it is off, as far as I know.

Also, no, I don't have stability issues with a -rt kernel on either of my systems. One has an i810 and the other a GeForceFX 5200. It seems to be hit-or-miss for most people. But I am using 2.6.16, as in the wiki, not 2.6.17.

---

### Post by www.rzr.online.fr on 2007-02-18
Same Issue here (2.6.20-rt8) I have a ali5451 sound card .. how comes ?
[http://rzr.online.fr/q/rt](http://rzr.online.fr/q/rt)

---

