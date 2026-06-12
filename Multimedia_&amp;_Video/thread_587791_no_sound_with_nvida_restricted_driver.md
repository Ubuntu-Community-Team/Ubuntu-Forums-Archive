---
title: "no sound with nvida restricted driver"
date: 2007-10-23
forum: Multimedia &amp; Video
---

### Post by whazooo on 2007-10-23
Hello!
I have tried to search for an answer to my problem with no luck.

I've installed Ubuntu 7.10 and am loving it.

However I have encountered a little bug.

If I install the nvida restricted driver, I get no sound.
I've checked here, bugtracker and google with no results.

any help with this issue would be appreciated.

here are my system specs:

OS- Ubuntu gutsy 7.10 32bit
MB- asus M2N sli deluxe AM2 
cpu- AMD Athlon 64 X2 3800+
graphics card- GeForce 7600 GS
mem- Corsair 6400C5DHX 800mhz 1GB x 2 DDR2
Any other inf, Please let me know

Thanks
Whazooo

---

### Post by whazooo on 2007-10-23
Once again the power of linux is revealed...
the computer has healed its self...

Last night when doing a  asoundconf list I got nothing with the restricted driver

this morning, After reinstalling the RD I get:

 asoundconf list

Names of available sound cards:
NVidia

 aplay -l

**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: AD198x Analog [AD198x Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: AD198x Digital [AD198x Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

lspci | grep -i audio

00:06.1 Audio device: nVidia Corporation MCP55 High Definition Audio (rev a2)

Thanks 
whazooo

---

