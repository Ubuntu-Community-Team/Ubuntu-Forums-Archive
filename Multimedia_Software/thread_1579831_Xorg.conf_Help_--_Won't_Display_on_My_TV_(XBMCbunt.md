---
title: "Xorg.conf Help -- Won't Display on My TV (XBMCbuntu)"
date: 2010-09-22
forum: Multimedia Software
---

### Post by shaft0 on 2010-09-22
Hi, I installed XBMCbuntu following this guide: [http://wiki.xbmc.org/?title=XBMCbuntu](http://wiki.xbmc.org/?title=XBMCbuntu)

All is well if I boot my computer using a regular computer monitor, but my LCD TV is a piece of crap when it comes to accepting VGA connections, and will only take two resolutions: 1024x768@60Hz, or 640x480@60Hz.

I've edited my xorg.conf file to only have reference to 1024x768@60, but whenever I boot up with my TV connected, it just says "INVALID MODE" on the TV.  If I disconnect the TV and connect the monitor, for whatever reason it's in 800x600.

If I boot the computer with the monitor connected, it boots into 1024x768 as expected, and I can disconnect the monitor and connect the TV and all is well.  

For obvious reasons, this isn't ideal.

Here's my Xorg.conf file:
[http://pastebin.org/1084628](http://pastebin.org/1084628)

The reference to "TV" in the Monitor section is because in my TV book, there's a table of signals for each type of TV.  It says "1024x768 (XGA) (Vertical Frequency (Hz): 60.0) (Horizontal Frequency (kHz): 48.4)" and I tried to setup that bit accordingly.

In any case, can someone do me a solid and put something in there, or take something out of there that forces 1024x768@60.0Hz regardless of what type of monitor is connected?

Thanks!

---

### Post by shaft0 on 2010-09-25
Anyone?

---

