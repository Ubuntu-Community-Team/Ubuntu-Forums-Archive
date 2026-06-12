---
title: "No audio after upgrading graphics card"
date: 2016-03-06
forum: Multimedia Software
---

### Post by Tyler_Aschenbrenner on 2016-03-06
I installed an nvidia 980ti and now my audio does not work in Ubuntu 15.04, audio worked fine prior to instillation.  I have followed both guides in the sticky as well as several others found through 
googling. The speakers are plugged in correctly, volume turned up, and i am able to get audio when i boot into windows 10.  I have un-installed and re-installed pulseaudio, alsa, libasound2, and 
dkms (interestingly doing this has made the background in settings transparent).  No audio options are showing up in settings>sound, and only option in pulseaudio volume control is nvidia HDMI 
which is no good given that i am trying to use external speakers with 3.5m jack.  I have also made sure that onboard audio is enabled in my bios. 

I am out of ideas any help is much appreciated.

Output of aplay -l
```
**** List of PLAYBACK Hardware Devices ****
card 1: NVidia [HDA NVidia], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 7: HDMI 1 [HDMI 1]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 8: HDMI 2 [HDMI 2]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 9: HDMI 3 [HDMI 3]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

System Specs:
cpu: intel i7 6700k
gpu: nvidia 980 ti
motherboard: Gigabyte GA-Z170X-UD3
speakers: logitech external

Issue Resolved. Updated system to 15.10

---

