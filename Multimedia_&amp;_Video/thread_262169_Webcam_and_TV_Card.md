---
title: "Webcam and TV Card"
date: 2006-09-21
forum: Multimedia &amp; Video
---

### Post by Plankman on 2006-09-21
Hi. Can someone maybe help.
I've got a Logitech Quickcam Messenger webcam and a Hauppaige PVR 150 tv card. I need to get them both working in Ubuntu. I can get the webcam going, but then the tv card doesn't load all the drivers.

As far as the tv card goes,  I can with some difficulty get the tv card installed, but i can't seem to use it. If I use zapping tv viewer and try to set up the channels it crashes. xawtv doesn't work and neither does kdetv. all i get is static.

If anyone could point me in the right direction it would help a lot.

Thanks

---

### Post by DoctorMO on 2006-09-21
Both tv cards and webcams are counted as video devices normaly available in /dev/video0 ect, this means being compatable with video4linux.

I can get my webcam to come on my tv (tvtime) and send my tv to people via msn (freaky)

So it sounds like you have some hardware which may be getting confuised between what it is. have you tried mod probing the moduals required for each of the devices one by one to find out if there is a modual/driver problem?

---

### Post by macewan on 2006-09-23
I'm using both of the devices you are describing so they do work. Try starting them each from command line and see what errors come back at you.

---

