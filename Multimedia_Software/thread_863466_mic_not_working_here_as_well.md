---
title: "mic not working here as well"
date: 2008-07-18
forum: Multimedia Software
---

### Post by guyguyguy on 2008-07-18
Hello there

I read about 100 posts about mic not working, and Im sorry to add another one, but here goes...
hp pavillion dv6000. 
Im using Hardy 8.04.1. Tried both a clean ubuntu install and a clean kubuntu install. Everything works except the mic. 
I tried every possible configuration through alsamixer, kmix and the gnome interface. 
Also tried to correct esd.conf (from -as 2 to -as 1 and also -as 0), didn't work.
Also tried using OSS instead of ALSA, didn't work.
mic worked in winxp :(

Here's the output of arecord -l:
**** List of CAPTURE Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: CONEXANT Analog [CONEXANT Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


Thanks
Guy

---

### Post by guyguyguy on 2008-07-21
SOLVED.
Ok, so obviously instead of fighting with it for a week, I should have just posted here and the problem got magically solved :)

What solved it for me was - I ran kubuntu (8.04) from the live cd and played more with kmix. At the end switching on internal mix solved it, even though the laptop does not have an internal mic.
Anyway, after a reset the mic is now working in my regular 8.04.1 install, and everyone is happy. 

Sorry for anyone who wasted time thinking about this, but maybe for someone else this would turn out helpful.
By the way, the easiest way to test the mic for me was to use arecord and aplay. Saves the need of running grecord and such...

$ arecord | aplay

cheers
guy

---

