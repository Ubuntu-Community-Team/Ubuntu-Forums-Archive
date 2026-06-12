---
title: "No video with xf86-video-ati"
date: 2008-01-08
forum: Multimedia &amp; Video
---

### Post by heffalump on 2008-01-08
I haven't touched Linux since Red Hat, about 7 or 8 years ago. Be gentle!

I started with using Ubuntu to setup a media center via MythTV. Vesa drivers were automatically used on my CRT monitor. Once I got it all settled, I plugged my TV into the S-Video port on my ATI All-In-Wonder Radeon (32MB). It worked fine. However, it wasn't using ATI drivers, like it was supposed to. Trying to switch over to ati drivers (with only the TV connected) caused X to return that Radeon's driver couldn't find any valid modes.

I found this ilnk:
[http://www.phoronix.com/scan.php?pag...item=806&num=1](http://www.phoronix.com/scan.php?pag...item=806&num=1)

I re-attached the box to a CRT monitor. I got up to entering xrandr commands (no noticed errors, up to this point) & was told that "S-Video" wasn't an option by the terminal. I figured I had to reboot after switching over to ATI drivers. I rebooted and, after seeing the Ubuntu load bar complete, the video signal ceased. My monitor signaled it was no video & not just a black screen.

My questions are:
1) First and foremost, what's the most likely cause of this problem?
2) How can I tell if the newly built drivers actually built correctly and installed? Is there any way to check driver versions?

My video card is an ATI All-In-Wonder Radeon 32MB. According to lspci, it is a Radeon 7200 (R100)

If you need me to cough up any extra info (logs, etc) please elaborate on how I can get them here.
__________________

---

