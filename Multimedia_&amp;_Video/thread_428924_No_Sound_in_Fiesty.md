---
title: "No Sound in Fiesty"
date: 2007-04-30
forum: Multimedia &amp; Video
---

### Post by Nihil Videmus on 2007-04-30
I just installed Feisty on a Lenova T60 and nearly everything worked out of the box- except sound;  getting odd errors on media players led me to type /usr/bin/speaker-test which led to this error:
ALSA lib pcm_dmix.c:864:(snd_pcm_dmix_open) unable to open slave
Playback open error: -16,Device or resource busy
being repeated over and over. I'm not sure how much (if anything) this has to do with the fact that amarok froze and now won't launch since the error seems to indicate the device is bieng used by something else...

aplay -l tells me this about my sound card
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: AD198x Analog [AD198x Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: AD198x Digital [AD198x Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

Does this mean that it's recognizing my sound card but there's a driver issue?

Thanks for any help in advance.

---

### Post by anirban.sam on 2007-05-05
Type alsamixer and press enter in a console to launch alsamixer. Disable all ICE devices in alsamixer and unmute all muted. Save settings by typing "sudo alsactl store".

---

### Post by Nihil Videmus on 2007-05-05
The issue has been resovled; I used a few fixes on the forum and had to reboot twice but the sound now works, thanks for the help.

---

