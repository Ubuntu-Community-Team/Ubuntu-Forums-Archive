---
title: "Pulseaudio and Flash Delay"
date: 2009-07-07
forum: Multimedia Software
---

### Post by Mall Zombie on 2009-07-07
Ok here's my problem.  I've had about a .5 second delay in the flash plugin ever since intrepid (using Jaunty now).  It happens with with games and interactive flash programs, stuff like youtube work fine.  I think it has something to do with pulseaudio. I've tried removing pulseaudio and that seemed to help but i want to keep pulseaudio. I've tried updating pulseaudio to the latest versions with repositories, and that seemed to fix it too, until i restarted my computer and then back to the delay. I was wondering if there was a permanent solution to this.

---

### Post by lovinglinux on 2009-07-07
You could try this: [http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)

Pulseaudio is only causing problems for me. I tried to fix it, but ended removing it completely on my desktop running Jaunty. A notebook running Intrepid started to display performance issues since a couple of weeks, with Firefox going grey very often and slowing down the machine to a point of no return. So I also removed pulseaudio from it two days ago and Firefox isn't freezing anymore. It just goes grey eventually, but comes back.

---

### Post by captaincrook on 2009-08-09
Hate to bump this but I'm having the same issue and its a real P.I.T.A. Any solutions?

---

### Post by captaincrook on 2009-08-20
Booty bump.

No solutions and PA's delay makes me weep. :(

---

### Post by organelas on 2010-06-10
I opened a bug report a while ago. Still no fix.

[https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/458581]("https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/458581")

---

### Post by rlarrowe on 2010-06-14
Not sure if this will help, but I had the same problem with Doom 3 sound delay in PA.  Use pasuspender:

pasuspender -s=alsa -- <the program you want to run>

---

### Post by Mozenrath on 2010-09-13
Hey guys, if you install libflashsupport, the delay goes away.

I know some of you might think "Eeewww, evil libflashsupport!"  Well, it's the best solution I've found and I haven't had any issues with it.

Just add this line to your software sources:
```
deb http://archive.ubuntu.com/ubuntu hardy main restricted universe multiverse
```

Then reload your package information, and install libflashsupport through Synaptic.

The description of libflashsupport says that it's for Flash 9, but it works for Flash 10 as well.

The only drawback to this is that it won't work for 64-bit users who use the 32-bit version of Flash.  However, it may be possible if you install the 32-bit version of libflashsupport.  I haven't tried this, though.

---

