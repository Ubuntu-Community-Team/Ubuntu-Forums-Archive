---
title: "Sound no longer works"
date: 2009-04-28
forum: Multimedia Software
---

### Post by kroberge on 2009-04-28
Yes I've searched the forums and I've found and read a number of posts with the same title.  So I'll tell you what I know at this point.

(1) Installed Xubuntu, sound worked automatically.

(2) Sound stopped working for no "apparent" reason.

(3) However it still functions under XP (dual boot) and it works on SliTaz distro (LiveCD: 30MB!!) automatically.

Question 1: Can I use SliTaz to get useful info to help me get sound working in Xubuntu again?

Question 2: Its got to be something weird, since Slitaz gets it and its  tiny, why isn't Xubuntu getting it anymore?  What changed?  

(4) I uninstalled the alsa-base and alsa-utils and linux-sound-base and reinstalled them also.  That didn't help.  

(5) when I  run alsamixer nothing is muted.  

I'm befuddled?

Thanks in advance,

Kevin

---

### Post by kroberge on 2009-04-28
Okay, so I solved the problem, apparently.  I took a screen shot of my alsa-mixer while in Slitaz because it looked different than the alsa-mixer settings in Xubuntu.

What I did was to mute "Line", "Line Jack" and "CD" while leaving on Master, Master M, Headphone and PCM.  

For whatever reason that worked.  Does anyone know why?

Thanks,

Kevin

---

