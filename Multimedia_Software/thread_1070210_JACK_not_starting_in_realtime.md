---
title: "JACK not starting in realtime"
date: 2009-02-14
forum: Multimedia Software
---

### Post by swornbrother on 2009-02-14
Hey guys, I'm getting this error message every time I try running JACK in realtime:

> 

loading driver ..
can't load "/usr/lib/jack/jack_alsa.so": /usr/lib/jack/jack_alsa.so: failed to map segment from shared object: Bad address
cannot load driver module alsa
libgcc_s.so.1 must be installed for pthread_cancel to work



Unfortunately I have to use Jaunty development (Alpha 4) because earlier versions will not run on this hardware.

It seems as if somebody on the Arch Linux forums is having the same problem, after recently updating.  [http://bbs.archlinux.org/viewtopic.php?pid=498277](http://bbs.archlinux.org/viewtopic.php?pid=498277)

Any thoughts on this?  It's mission-critical that I get JACK running.

---

### Post by markbuntu on 2009-02-15
I have just got Jaunty installed myself but will be triyng jack etc out on it in the next few days. I will get back if i find something.

---

### Post by swornbrother on 2009-02-16
Ok, after a little more digging, I found a bug fix on launchpad ([https://bugs.launchpad.net/ubuntu/+source/gcc-3.3/+bug/40285](https://bugs.launchpad.net/ubuntu/+source/gcc-3.3/+bug/40285)), which kind of helped, in that it removed
> libgcc_s.so.1 must be installed for pthread_cancel to work

Now after running ```
 jackd -R -dalsa -dhw:1,1 -r44100 -p256 -n3 -D -Chw:1,1 -H
 
``` the terminal outputs just this:

> 

loading driver ..
can't load "/usr/lib/jack/jack_alsa.so": /usr/lib/jack/jack_alsa.so: failed to map segment from shared object: Bad address
cannot load driver module alsa




On the JACK website it says they are at version 1.9.1, but Ubuntu is running 0.116.1.  Perhaps this has something to do with it?

Installing the latest JACK from source is a little over my head.  Any recommendations for this?

---

### Post by artfwo on 2009-02-16
Same problem here. I thought jackd was broken completely, but it does work without -R. Thanks for the tip! Actually, it *worked* on a fresh alpha-4 install, so I think one of the recent updates is guilty...

Going to dig it further today!

---

### Post by artfwo on 2009-02-16
Woah, it looks like a Debian bug against libasound2 ([link]("http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=515185")) is all about the same issue! Perhaps, a downgrade of libasound2 may serve as a temporary workaround...

---

### Post by swornbrother on 2009-02-18
ok, interesting...  how would we go about downgrading?

---

### Post by artfwo on 2009-02-18
I think there's no need to downgrade, the problem has just disappeared with latest updates. Weird...

---

### Post by swornbrother on 2009-02-19
I can verify that the problem did indeed get fixed with the latest update.

I'm still getting massive XRUNS on my USB audio interface, even with the wireless button off and running in RT.  Not sure what's going on here, but I think it's a different issue.

---

### Post by artfwo on 2009-02-20
Yep, also getting XRUNs with ALSA (and crashes with FFADO). I don't even have a clue how to report this as a bug lol :D

---

### Post by artfwo on 2009-02-25
Just found out, that a temporary solution for the XRUNs is offered at 64studio forums:
[http://www.64studio.com/node/936]("http://www.64studio.com/node/928")

And here's the original thread:
[http://www.64studio.com/node/928]("http://www.64studio.com/node/928")

An older JACK package, anyone? :lolflag:

---

