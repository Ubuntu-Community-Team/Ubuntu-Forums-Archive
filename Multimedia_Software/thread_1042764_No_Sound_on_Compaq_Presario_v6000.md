---
title: "No Sound on Compaq Presario v6000"
date: 2009-01-17
forum: Multimedia Software
---

### Post by aquabug on 2009-01-17
I have a compaq presario v6000 with an AMD Mobile Sempron processor (32-bit), and a Conexant HD Audio card.  When I first started Ubuntu the first half second of the start sound kept repeating over and over again.  I disabled system sounds so it doesn't do it any more, but no other sounds seem to work.

This is what aplay -l shows:
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: CONEXANT Analog [CONEXANT Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: Conexant Digital [Conexant Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

---

### Post by Euforiaz on 2010-01-19
I know this reply might be too late for aquabug but still might help someone else.. my Ubuntu (actually UE 2.4) system with the following specs:
euforiaz@euforiaz-laptop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: CONEXANT Analog [CONEXANT Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: Conexant Digital [Conexant Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

..had apparently all sound drivers working well (I could mute and change the volume high low level bar) but still wouldn't make any sound, I also checked the master volume level with the following command: alsamixer but still no sound until under Sound Preferences (right click the volume icon in the menu bar), under "Hardware" tab for the Profile tag I selected "Analog Stereo Duplex" and the sound just started working, now I'm enjoying X-Rx great music! hope this post helps :D

---

