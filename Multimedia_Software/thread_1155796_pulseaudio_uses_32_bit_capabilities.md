---
title: "pulseaudio uses 32 bit capabilities"
date: 2009-05-11
forum: Multimedia Software
---

### Post by zika on 2009-05-11
on random check of dmesg I found: [   29.457148] warning: `pulseaudio' uses 32-bit capabilities (legacy support in use) ...
this is all-64-bit Phenom X3 machine, as I was able to make it, with latest versions (0.9.15, as I recall) of all pulseaudio files available from themuso ...
any thoughts ... ?
it works OK but ...

---

### Post by RavanH on 2009-09-29
Old post but still relevant?

Having problems with random freezes I was reading through the log files and found the same message in my syslog, messages and kern log files. An old bugreport on launchpad [https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/339448](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/339448) states this has been fixed in pulseaudio since release 0.9.14-0ubuntu11

However, on my system it is back (or never went away) with pulseaudio version 0.9.15-1ubuntu2~jaunty1~ppa1 which came from I forgot which PPA repo.

Could this be causing the 3 random freezes I had today?

---

