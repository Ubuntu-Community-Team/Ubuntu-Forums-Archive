---
title: "Sound Problem"
date: 2009-02-08
forum: Multimedia Software
---

### Post by snehasish on 2009-02-08
I have an ASUS P5LD2-VM motherboard with onboard Realtek HD Audio 5.1.
Sound was just fine when I installed and worked with Ubuntu for about a couple of weeks or so. Today when I plugged in my headphones along with my speakers after a reboot, i found a little red cross in the volume manager. After which I couldnt hear anything at all. I went to 
System>preferences>Sound> and tested the playback drivers. The OSS drivers were working. I had to change the audio plugin in audacious and vlc in order to get back the sound. However i dont hear any system sounds (like startup) this is the output of  "aplay-l"
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC882 Analog [ALC882 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC882 Digital [ALC882 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

-Confused

---

### Post by snehasish on 2009-02-11
Thank You for all your help guys. The problem seems to have fixed itself.

-Confused++

---

