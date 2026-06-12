---
title: "VLC Sound distorts"
date: 2008-10-04
forum: Multimedia Software
---

### Post by GuDoN on 2008-10-04
It is hard to explain, but I played the exact same video in mplayer, and it played just fine...

VLC however, the sound randomly like cracks, and goes on, it is super fast, it's like a 0.1 distort, and then it carries on like normal. But it is very irretating! Haha...

This happens about every 10 seconds, but sometimes earlier or later, as I said, random!! :D

Anyone know anything about this?

I'm using:
System Information for anarki: CPU: GenuineIntel
vendor_id : GenuineIntel Intel(R) Pentium(R) 4 CPU 3.40GHz
model name : Intel(R) Pentium(R) 4 CPU 3.40GHz 3391.898
cpu MHz  : 3391.898 MHz, 1024 KB
cache size : 1024 KB Cache RAM: 1035 MB HDD: 335 GB OS: GNU/Linux 2.6.24-16-generic Uptime: 22:06:21 up  1:46,  1 user,  load average: 0.28, 0.43, 0.48

---

### Post by rainwalker on 2008-10-04
It's an issue between VLC and PulseAudio; for some reason VLC doesn't play nice with it all the time

As far as I've been able to tell, there's not a fix (yet?)

---

### Post by markbuntu on 2008-10-04
I use vlc all the time with pulseaudio and have never experienced that problem. In Settings/Preferences/Audio/Output Modules do you have Pulseaudio audio output selected?

You need the Advanced options box checked to see that.

---

