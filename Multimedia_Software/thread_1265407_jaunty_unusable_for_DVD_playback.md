---
title: "jaunty unusable for DVD playback"
date: 2009-09-13
forum: Multimedia Software
---

### Post by accabrown on 2009-09-13
I have never been able to get DVDs to play back smoothly at full screen under 9.04. I have tried with both ATI (3200) and nvidia (gforce9400) graphics cards, using both standard and proprietary drivers. I have tried mplayer, vlc, totem ... none of them play back DVDs in full screen at anything like acceptable speeds. Every time a character moves, they leave a blurry trail of pixels; from time to time the whole thing hangs up solid.

The same DVDs play flawlessly on a much less powerful mac mini, or of course on any windows machine. 

Is this something specific to ubuntu, or to Jaunty, or is there no linx distribution which plays DVDs at adequate speeds on modest hardware?

---

### Post by VMC on 2009-09-13
Did you read [**Multimedia & Video Howto**]("http://ubuntuforums.org/showthread.php?t=766683"). That worked for me.

---

### Post by accabrown on 2009-09-14
Nope. I have done all that and it's still unworkable. But thanks for answering.

---

### Post by accabrown on 2009-09-15
the problem seems to be that even though I have a decent video card, almost all the work is being done by the cpu. when I run htop to see what's happening, it shows cpu load of between 50 and 70% for totem. This seems absurd

(amd 5200 dual core)

---

