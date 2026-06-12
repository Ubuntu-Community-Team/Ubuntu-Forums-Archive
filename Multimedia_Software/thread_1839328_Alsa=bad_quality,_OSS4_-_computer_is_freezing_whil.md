---
title: "Alsa=bad quality, OSS4 - computer is freezing while doing osstest command"
date: 2011-09-05
forum: Multimedia Software
---

### Post by Shaom on 2011-09-05
Hi my english isnt very well sorry for that. Here is my problem: (Ubuntu 11.10 i was trying this on 11.04 too.)

1. I choosed oss in sudo dpkg-reconfigure linux-sound-base and restarted.
2. I installed deb file from this website: [http://www.opensound.com/download.cgi](http://www.opensound.com/download.cgi) - restart
3. After run osstest command my computer freezes. Here is what oss says:

*** Scanning sound adapter #-1 ***
/dev/oss/oss_ymf7xx0/pcm0 ([COLOR=blue]**_audio_**[/COLOR] engine 0): Yamaha YMF724F
Note! Device is in use (by PID 0/VMIX) but will try anyway
Performing audio playback test...
<left> Device returned error: Input/output error

I was trying unistalled pulse and installed gstreamer and when i run gstreamer-properties and try to change plugin to oss computer is freezing too. Thanks for help i really dont know what to do.

Alsa is working but sound quality is really bad.

---

