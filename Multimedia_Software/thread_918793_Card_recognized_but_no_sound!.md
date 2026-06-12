---
title: "Card recognized but no sound!"
date: 2008-09-13
forum: Multimedia Software
---

### Post by nightmarestreet on 2008-09-13
Hi guys.

I'm trying to get sound working on my Dell Inspiron Mini 9 laptop.

So far I've just been following the "Comprehensive Sound Problems" thread.

biff@laptop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC268 Analog [ALC268 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

So according to that, my sound card is recognized right?

The guide basically says that sound should be working for me, but I'm not getting *any* sound.

I've tried changing the volume both in gnome and alsamixer and no, it's not muted ;)

Any suggestions guys? Should I file a bugreport?

---

### Post by markbuntu on 2008-09-14
If you are having problems with the HDA card/chip on your laptop you should look here:

[http://ubuntuforums.org/showthread.php?t=616845](http://ubuntuforums.org/showthread.php?t=616845)

There is some specific info for your ALC268 that may be helpful.

---

### Post by nightmarestreet on 2008-09-15
Hey thanks!

I tried setting 

options snd-hda-intel model=dell 

even though it wasn't listed, and I got sound, albeit with a loud hissing noise in the background.

I'll try a few of the others, if not then I'll just wait for it to be fixed in one of the later releases. Good to know that it is actually possible for it to work with linux though.

---

