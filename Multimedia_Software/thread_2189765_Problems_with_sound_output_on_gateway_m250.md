---
title: "Problems with sound output on gateway m250"
date: 2013-11-23
forum: Multimedia Software
---

### Post by thatredbird on 2013-11-23
I recently switched over to Lubuntu from windows xp, so there is quite a bit of a learning curve on using the terminal.  I have been all over the community forums and I have tried a couple of things to fix the issue. downloaded xfce4-mixer, tried to run sound tests and the like. here is some of the responses from the system when i was trying to fix it.

when I used alsamixer to try to change sound card it appeared to be adjustable

when I entered  a speaker test(speaker-test -Dplughw:03 -c6) I get 
ALSA lib pcm_hw:c1667:(_snd_pcm_hw_open) Invalid value for card

when i enter aplay -l I get

**** List of PLAYBACK Hardware Devices ****
card 0: ICH6 [Intel ICH6], device 0: Intel ICH [Intel ICH6]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: ICH6 [Intel ICH6], device 4: Intel ICH - IEC958 [Intel ICH6 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


I am wondering if there is a resource that I can look to attempt to correct my issues, thanks for your time.

redbird

---

