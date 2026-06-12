---
title: "ATI 8.7 and Envy"
date: 2008-07-21
forum: Multimedia Software
---

### Post by rbmorse on 2008-07-21
I use Envy to install the proprietary ATI FGLRX driver into Ubuntu 8.04 (thanks guys!)

ATI released version 8.7 of the Catalyst driver package today. 

Will Envy detect the new version, or will the Envy devs have to push an update to accommodate 8.7?

---

### Post by NT4usB on 2008-07-21
[http://albertomilone.com/envyfaq.html#H](http://albertomilone.com/envyfaq.html#H)

---

### Post by chalewa on 2008-07-21
i just installed it manually....

really is not that tough at all.

---

### Post by rbmorse on 2008-07-22
On my system (ATI HD3870), installing 8.7 with the ATI installer results in a working box, but with the following anomalies not present with the ATI Catalyst 8.6 driverset installed by EnvyNG:

1.  Overall performance about 20% slower (the not-a-benchmark glxgears goes from 14,400 to 10,200)

2. glxinfo, fglrxinfo, (not-a-benchmark) glxgears and the ATI control center only work when run with sudo (needs root). 

3. (most vexing) With desktop effects enabled, watching anything video related results in severe blanking/tearing in the window displaying the video. The 8.6 drivers installed via EnvyNG do not display this problem. This is enemy #1 over on the Phoronix site. I don't know what the Envy devs do here, but I am glad they do it. 

I just this morning reverted back to the 8.6 drivers...purging FGLRX 8.51.3 (8.7) and installing 8.6 using the ATI installer.  I get  the same video blanking problem I see with the 8.7 drivers, but not the performance drop or need to be root to use utilities.   

Purging again and installing the ATI 8.6 drivers with EnvyNG results in a box that works without problems, for me.  I'll assume those known issues endemic to the release, which are legion, are still issues, but fortunately they do not manifest in the way I use the machine. 

I'll wait until Envy gets updated and try again.

---

