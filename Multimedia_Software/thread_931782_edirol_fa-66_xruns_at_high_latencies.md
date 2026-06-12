---
title: "edirol fa-66 xruns at high latencies"
date: 2008-09-27
forum: Multimedia Software
---

### Post by nightfrost on 2008-09-27
I recently purchased an edirol fa-66 in order to start recording a little at home. The reasons I bought this particular audio device are because a) I understood it had pretty good linux support (using freebob) and b) it is a firewire device and I thought that as such it would give me pretty low latencies.

Right now, I'm getting xruns even with a latency of 250-300ms. With the internal audio device (a crappy on board intel thing), I get no xruns at lower latencies. I've tried everything from rt-kernels to priority settings and so on and so forth. Nothing seems to help. Could there be something wrong with the device? Unfortunately, I don't have the possibility to try it under Windows, so my only bet is to troubleshoot it with all ye good forum people, or return the device and settle for a cheaper USB based option.

First thing: Is anyone here using this device successfully?

EDIT:

Things I have done so far:

* Running on an -rt kernel
* fixed permissions of /dev/raw1394
* Using ridiculously high figures on frames/period (just to make sure)
* Added variations of these three:
     @audio - rtprio 100
     @audio - nice -20
     @audio - memlock 1048576
  to /etc/security/limits.conf
* used the rtirq.sh script to fix the priorites of the firewire device, as well as fixed the priority of jackd (jackd is at 75, the rtc device is as at 90, ohci1394 at 85, snd at 80)

EDIT 2: Solution lied in updating freebob to ffado and jack to the latest available here: [https://edge.launchpad.net/~ubuntustudio-dev/+archive](https://edge.launchpad.net/~ubuntustudio-dev/+archive)

---

### Post by xc3RnbFO8P on 2008-09-27
> First thing: Is anyone here using this device successfully?
Someone does:
[http://www.nabble.com/a-100--guaranteed-firewire-interface-for-linux--td18074094.html]("http://www.nabble.com/a-100--guaranteed-firewire-interface-for-linux--td18074094.html")

---

### Post by nightfrost on 2008-09-28
Thanks for the reply!

So, obviously, it should be plug and play (more or less), in which case I really don't see what's dead wrong here. Any suggestions of how I can find out whether something's wrong with the actual device? I'm pretty new to using jack, but as far as I understand by now, running on 4096 frames/period and 3 periods/buffer should under almost no circumstances give xruns. Yet, that's precisely what's happening.

(This is driving me crazy).

Thanks again.

---

### Post by xc3RnbFO8P on 2008-09-28
Maybe this will help:
[https://help.ubuntu.com/community/HowToJACKConfiguration]("https://help.ubuntu.com/community/HowToJACKConfiguration")

---

### Post by nightfrost on 2008-09-28
It seems the problem was related to jackd and/or libfreebob.
I updated the jack and installed ffado from the ubuntustudio ppa ([https://edge.launchpad.net/~ubuntustudio-dev/+archive](https://edge.launchpad.net/~ubuntustudio-dev/+archive)), and the new packages work so much better!

Now, does anybody know where to give feedback to the ubuntustudio guys? Cause these packages seriously need to be in the next release.

---

