---
title: "No Sound in Center Speakers."
date: 2009-04-03
forum: Multimedia Software
---

### Post by tinhed on 2009-04-03
I have an ASUS M2A-VM Motherboard with the Realtek ALC883 Onboard Audio. I have connected it to Creative T6100 5.1 speakers.The problem is that the center speakers give only a hissing and no sound. Front,Rear and subwoofers work just fine.

I have tried lots of techniques given in this forum ( aplay,.asoundrc, daemon.conf,even oss) and nothing seems to work. Nothing is Muted. No Luck wth ALSA or Pulseaudio. I am using Ubuntu 8.10.

Sound Works Perfectly in Windows. Interestingly if i swap the left surrond connector with the center speaker on the subwoofer, the center starts working fine and the left one starts hissing. The same is the case with front,left and right surrond. It seems no sound is coming out of the center speaker port.

Any Idea Sirs what i should do. Will upgrading to  ALSA 1.0.19 help. Is there a problem with jack sensing.

Any help will be greatly appreciated. Thanks in advance

---

### Post by Cresho on 2009-04-03
test your speakers in terminal

speaker-test -Dplug:surround40 -c4 -l1 -twav
speaker-test -Dplug:surround51 -c6 -l1 -twav
speaker-test -Dplug:surround71 -c8 -l1 -twav

each one checks for diff hardware configs.

---

### Post by tinhed on 2009-04-03
> **Cresho said:**
> test your speakers in terminal

speaker-test -Dplug:surround40 -c4 -l1 -twav
speaker-test -Dplug:surround51 -c6 -l1 -twav
speaker-test -Dplug:surround71 -c8 -l1 -twav

each one checks for diff hardware configs.

The first Test shows that all four channels are working. The second test fails on center and LXE. Rest Channels are fine. I double checked. Nothing is muted.

---

### Post by Cresho on 2009-04-03
open alsamixer in terminal and check to see if the levels are low.  then in sound manager check to see if alsa is not the default audio manager

---

### Post by tinhed on 2009-04-04
> **Cresho said:**
> open alsamixer in terminal and check to see if the levels are low.  then in sound manager check to see if alsa is not the default audio manager

Tried that. ALSA is the default manager and all volumes are maximum. I wonder whether i should try out OSS4 as ALSA does not seem to be working.

---

### Post by Cresho on 2009-04-04
I remember having the same issue so I stuck in my audigy soundcard back into my pc.  I figured it takes the load off the cpu anyway.  I never tried to figure out why I was having problem with it for a second reason.  I think my motherboard was defective and in windows, it features an autodetect type connection and also my rear speakers where shut off.  I wish i could help more.

---

