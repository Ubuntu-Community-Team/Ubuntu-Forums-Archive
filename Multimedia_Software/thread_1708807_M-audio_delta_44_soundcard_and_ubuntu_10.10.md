---
title: "M-audio delta 44 soundcard and ubuntu 10.10"
date: 2011-03-17
forum: Multimedia Software
---

### Post by Usuthu on 2011-03-17
Hey all.
 
A warning, I'm a total newbie here having decided I'd had enough of Windows and its seemingly endless wait for my PC to load up etc etc.
 
I installed Ubuntu 10.10 and am amazed at all the awesome software it comes with that works better than anything MS has created.
 
I've got most things working, after learning some lessons (such as exe files are a Windows thing, I never knew that).
 
But, I have no sound through Ubuntu and am not sure how to sort it out.
I read somewhere that, as I have a certain soundcard, I shoudl disable the on-baord sound via BIOS. Tried that, but still no joy.
 
The soundcard I have installed, and which worked through Widows, is a M-AUDIO Delta 44 [http://www.m-audio.com/products/en_us/Delta44.html](http://www.m-audio.com/products/en_us/Delta44.html)
 
Going through 'preferences' and into sound options there is a soundcard mentioned there, but it doesn't appear to be my Delta 44. I've played around with the settings but no joy as yet.
 
When installing it in Windows, I downloaded a driver pack which was very easy, but I can't seem to find one for Linux.
 
Has anyone had any experience with Ubuntu 10.10 desktop edition and this soudncard
?
 
Thanks in advance :-)

---

### Post by lykwydchykyn on 2011-03-17
I have a Delta 44 in a machine at home; I haven't got 10.10 installed (it stays on 10.4), but I've been using it with Ubuntu since sometime around 7.04 without too much trouble.

I believe the driver it uses is snd-ice1712, so you might try: 
```

sudo modprobe snd-ice1712

```
To see if that enables it.  This driver may be blacklisted by default, I'm not sure, but see if the modprobe command gets it working.

You also might want to install the "alsa-tools-gui" package, which will give you the envy24control mixer -- a near clone of the mixer interface you get for the Delta 44 on Windows.

Good luck with it!

---

