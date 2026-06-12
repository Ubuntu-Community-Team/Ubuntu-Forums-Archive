---
title: "Improving midi playback performance"
date: 2007-11-23
forum: Multimedia &amp; Video
---

### Post by acl123 on 2007-11-23
Hi I am trying to improve the performance quality of midi playback. At the moment it is a little bit jerky, not nice and smooth, which basically makes it useless.

I am using Guitar Pro and Tuxguitar. I have tried using the xmms-midi plugin for xmms, but it has many problems and crashes xmms.

Midi playback is through Timidity.

I have been using Guitar Pro on Windows for 8 or 9 years, so it's very annoying to get such poor performance on a modern machine.

---

### Post by acl123 on 2007-11-26
I just installed UbuntuStudio and the midi playback seems to be much better with Guitar Pro, although still not so good with TuxGuitar. Interesting seeing as though Guitar Pro is running on Wine.
UbuntuStudio is awesome, by the way. Very easy to upgrade from Gutsy and everything seems to be working well.

---

### Post by pb_online on 2007-11-26
I think I have the same problem. I dont have quality sound at ubuntu.

---

### Post by chadliness on 2007-11-29
Have you tried editing the timidity config file? (/etc/timidity/timidity.cfg)  It gives a lot of helpful hints on how to reduce CPU usage.  I enabled all the options under the "Moderate CPU" section and my CPU usage for timidity dropped to around 5% from 50% before!  No noticeable change in the output quality but I'm no audiophile.

---

### Post by pb_online on 2007-11-29
I dont have this folder at /etc

---

