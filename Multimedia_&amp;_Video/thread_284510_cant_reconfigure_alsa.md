---
title: "cant reconfigure alsa"
date: 2006-10-25
forum: Multimedia &amp; Video
---

### Post by pontifex3 on 2006-10-25
hi, i have breezy badger completely updated, and my sound has always worked fine until the day before yesterday, i loaded ubuntu with the live cd and the sound worked fine so i know its not a hardware problem, the aplay -l outputs

jjara@geburah:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: nForce3 [NVidia nForce3], device 0: Intel ICH [NVidia nForce3]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: nForce3 [NVidia nForce3], device 2: Intel ICH - IEC958 [NVidia nForce3 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
jjara@geburah:~$ 

i think that means its fine, so i tried unmuting everything in the alsamixer and it still didn't work, i also removed all sound packages (sudo  apt-get --purge remove linux-sound-base alsa-base alsa-utils) reinstalled them, checked the alsamixer again and i still cant get it working

any ideas?
thanks

---

### Post by pontifex3 on 2006-10-25
never mind, i just ran the live cd and copied all configuration files that had to do with sound and its working just fine now :D

---

