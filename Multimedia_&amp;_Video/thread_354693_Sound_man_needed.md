---
title: "Sound man needed???"
date: 2007-02-06
forum: Multimedia &amp; Video
---

### Post by addisor on 2007-02-06
Running Edgy 6.10 on a Abit NF-M2 mobo and am having a struggle with sound. 

Here's aplay -l 

**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: ALC883 Analog [ALC883 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: ALC883 Digital [ALC883 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

Alsamixer is v1.0.14rc2 
&#9474; Card: HDA NVidia Chip: Realtek ALC883 

CD's and the like play fine, the problem is mic capture for skype and sound recording, there is none!!! just feedback. The headset is fine except the autodetect doesn't work so the monitor speakers still play. when i look for  cat/proc/modules, its empty!!!

Please help, its the last challenge in my self build ubuntu box.

---

### Post by ingo on 2007-02-19
Hm, I remember the same problem with skype. So I opened the mixer, fiddled with the settings for the microphone and everything worked fine...

---

