---
title: "Sound problem Intel CH5"
date: 2008-11-07
forum: Multimedia Software
---

### Post by LifeNova on 2008-11-07
Hi, having just upgraded to Intrepid I have a problem; no sound is played from any program. I tried booting into Windows XP and it works fine there, but Intrepid doesn't recognize it. On hardy, the sound worked fine. After running ```
aplay -l
``` I got this: 

**** List of PLAYBACK Hardware Devices ****
card 0: ICH5 [Intel ICH5], device 0: Intel ICH [Intel ICH5]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: ICH5 [Intel ICH5], device 4: Intel ICH - IEC958 [Intel ICH5 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

So according to the guide stickied on this forum, my sound card is recognized just fine. However, after running modprobe snd- like the guide says, I receive a message "FATAL: Module snd_ not found."

I tried using the guide to compile a new ALSA driver, got no errors after doing that (using module-assistant), however I ran modprobe snd- again and got the same message.

Thanks in advance :)

---

