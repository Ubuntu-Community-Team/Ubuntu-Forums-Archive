---
title: "Flash Running  Slow"
date: 2009-07-15
forum: Multimedia Software
---

### Post by jdb91 on 2009-07-15
Hi all,
Got a EEE PC 1000H, just having the poblem that when i try and run flash videos, they're pretty skippy and keep locking up, is this just due to the lack of resource or is there something i can do? Youtube works fine in normal mode, locks up with full screen, BBCi just works slow all the time.

Cheers.
Joe

---

### Post by igorzwx on 2009-07-15
it is PulseAudio
it is the problem for old boxes and netbooks
processor power

---

### Post by jdb91 on 2009-07-15
is Pulse Audio required for ALSA to work?

---

### Post by igorzwx on 2009-07-15
it seems like.
I tried to disable it in some way.
It did not work.
The evil mutates every day.
It looks like they are hacking ALSA modules and
everything else (e.g. "global equalizer")
to fix Pulse.

I removed all these evil eventually.

By the way, some days ago I made an interesting experiment:
[http://www.4front-tech.com/forum/viewtopic.php?t=3237](http://www.4front-tech.com/forum/viewtopic.php?t=3237)

it way work on a netbook too

---

### Post by rgb1701 on 2009-07-15
This is what we get for accepting a close, proprietary binary necessary to view 99% of web content :(

Anywho, try disabling Pulseaudio, updating Flash to 10.xx, ensuring you are running the lastest video driver for your GPU.

As stated previously, those netbooks have poor GPU's and low speed CPU's, and Flash on Linux relies 100% on the CPU for decoding and scaling, eating FAR more CPU than Flash on Windows- by design I suspect, as MS and Adobe probably work together to maintain their lockin.

Adobe single handedly turned the web into their exclusive closed domain, from the open standards it was supposed to be...

---

### Post by igorzwx on 2009-07-15
I can believe this.
This is the first time I hear a reasonable explanation of all my troulbles.
But,
Does it mean that OSS4 is better for Linux than ALSA (by design)?

---

### Post by lovinglinux on 2009-07-15
See Flash Optimization section of [**[COLOR="DarkRed"]Firefox optimization and troubleshooting thread[/COLOR]**](http://ubuntuforums.org/showthread.php?t=1193567)

To remove pulseaudio: [Tips: Things that might improve Jaunty performance](http://ubuntuforums.org/showthread.php?t=1152095)

Also these discussions:

[http://ubuntuforums.org/showthread.php?t=1206888](http://ubuntuforums.org/showthread.php?t=1206888)
[http://ubuntuforums.org/showthread.php?p=7614460](http://ubuntuforums.org/showthread.php?p=7614460)

---

