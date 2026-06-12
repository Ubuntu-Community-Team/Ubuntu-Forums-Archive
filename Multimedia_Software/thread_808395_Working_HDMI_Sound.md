---
title: "Working HDMI Sound"
date: 2008-05-26
forum: Multimedia Software
---

### Post by ngk_dk on 2008-05-26
I have read alot of post about people not getting any sound over HDMI, so now that I'm building a home cinema system a wont to know if any body have a setup that works out-of-box. I dos not matter if it a dedicated grafix card or an on-board solution.

---

### Post by Trollslayer on 2008-05-27
This issue is becoming much more common - maybe time for a sticky?
I have an Abit I-F90HD motherboard with ATI X1250 video and Realtek ALC883 HD audio.
There were a few problems:
Mplayer uses and old version of ALSA so it does not recognise the ALC883, VLC uses the current version and is fine (1.0.14 onwards).
You need to set the defautl sound card to HDMI (after checking with [COLOR="Blue"]aplay -l[/COLOR] that it is found, the applet is [COLOR="blue"]asoundconf-gtk[/COLOR]. Then use [COLOR="blue"]alsamixer[/COLOR] to unmute the HDMI output, it works for me.
One thing to note - the X1250 is OK but for complex HD with scaling I find I'm approaching the limit.

---

### Post by ngk_dk on 2008-05-28
Is it correct to assume that if it is a "Realtek ALC883 HD audio" chip, it will work with audio over HDMI for any grafix chip?

---

### Post by Trollslayer on 2008-06-05
No, the routing is handled by the graphics system.
Oh, just found there is a problem when you put it through an AV receiver, something to do with the HDMI switch.

---

