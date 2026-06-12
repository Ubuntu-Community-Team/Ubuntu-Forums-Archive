---
title: "ALC 887 audio - no sound"
date: 2011-08-11
forum: Multimedia Software
---

### Post by misterblobby on 2011-08-11
Hi,

I have an ASUS M5A78L-M LX motherboard with ALC887 inbuilt sound. The sound is barely audible unless the speaker volume is all the way up, and then it is very crackly. The BIOS is set up to use AC97 sound instead of HD Audio, which doesn't work either.

I have tried uninstalling and reinstalling ALSA drivers but it didn't really change anything. 

aplay -l comes up with this:

card 0: SB [HDA ATI SB], device 0: ALC887-VD Analog [ALC887-VD Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 1: ALC887-VD Digital [ALC887-VD Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

.... but still very little sound.

Can anyone help?

---

### Post by connellc on 2011-08-11
Go to: [http://ubuntuforums.org/showthread.php?t=205449&highlight=plugins+devices+volume+control+gstreamer+found](http://ubuntuforums.org/showthread.php?t=205449&highlight=plugins+devices+volume+control+gstreamer+found)

---

### Post by misterblobby on 2012-09-05
Long overdue update to this issue:

I tried every fault finding thing I could find, and nothing worked. Then  I tried Windows 7, and that had no sound either, so I took the board  back to the shop.

The replacement board is running what was the  latest bios a couple of months ago, and it hasn't had a problem but is  running windows 7. 

I tried a copy of Ubuntu 11.10 booting off  the disk that I had lying around, and the sound worked on the M5A78LM-LX  and a newer M5A78LM-LX PLUS that has whatever bios came with it.

It  does seem to be a fairly common thing with the sound on these boards  not working. I contacted ASUS about it, and their only comment was to  take it back!

---

