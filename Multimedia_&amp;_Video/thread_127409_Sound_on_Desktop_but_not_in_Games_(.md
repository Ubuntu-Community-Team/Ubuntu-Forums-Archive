---
title: "Sound on Desktop but not in Games :("
date: 2006-02-08
forum: Multimedia &amp; Video
---

### Post by Eijnuhs on 2006-02-08
First Post and first time running linux ! Great to see this happening community. 

I too, is having some problem with sound right now. When I first installed ubuntu 5.10, I had no problem but now I do have a problem with sound. Sound is actually alright I can hear sound during test on System > Preference > multimedia selector
However, I hear no sound in games..I tried running SolarWoft and I got no sound.. Same goes with PlanetPenguin. You guys got a clue what could be my problem ?

Thank you ! :)

---

### Post by AllenGG on 2006-02-08
Try some other "sounds" first. Load the "CD" player and play a CD, if it works then look elsewhere for your problem. Next, p_rovide more info_ on your system and problem.

---

### Post by Eijnuhs on 2006-02-08
I am running a IBM T43
The sound card as returned by aplay -l is

**** List of PLAYBACK Hardware Devices ****
card 0: ICH6 [Intel ICH6], device 0: Intel ICH [Intel ICH6]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: ICH6 [Intel ICH6], device 4: Intel ICH - IEC958 [Intel ICH6 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

And the sounds I have selected ALSA for source and output.
Well, I installed some codec for playing mp3 but thats all i did so far.
I tried playing a few different format..mp3, mpg, divX and so far they all worked
cept in game. I tried Forzen-Bubble and i cannot enable the sound option at all.

---

### Post by Toddy on 2006-02-09
I find that:

sudo apt-get install libsdl1.2debian-all

fixes the sound problem with games like Frozen-Bubble.

---

### Post by Eijnuhs on 2006-02-09
It worked ! Thanks alot ^^

---

