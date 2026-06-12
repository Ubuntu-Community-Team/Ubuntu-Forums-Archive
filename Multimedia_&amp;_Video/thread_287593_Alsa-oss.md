---
title: "Alsa-oss"
date: 2006-10-29
forum: Multimedia &amp; Video
---

### Post by odbod on 2006-10-29
Basically, I want to have the multiple sounds at once thing. It works, but then OSS takes over everything else. But when I have alsa-oss around, it helps me with that, but in skype, I hear tons of chipping here and there, and then everything else is fine. But, when I open firefox or even terminal(!!!) I hear a chip like it's allowing use of sound to it or something like..

Any solutions?

---

### Post by bignickel on 2006-10-29
What do you need OSS for?  As of Skype 1.3 it can use ALSA as well.  I remember having massive problems with sound on the old version.  Although the sounds of you opening a terminal are kind of weird.  Have you tried turning off ESD?  System -> Preferences -> Sound or killall esd to stop it temporarily.

---

### Post by odbod on 2006-10-29
Alsa gives me problems all by itself in skype only. Like, it will tell me that there is a problem with the sound device.

Now I have a asound.conf and a /etc/esound/esd.conf  file

"ALSA-OSS" is supposed to help out. In reality, all it really does for me is yes, help me, but cause chipping noises during anything.

---

