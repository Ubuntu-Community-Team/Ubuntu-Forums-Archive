---
title: "Audio problem on  10.04"
date: 2010-06-12
forum: Multimedia Software
---

### Post by realmadridcf on 2010-06-12
Cant figure out the problem with my audio...
Cannot hear any sound from the system
pls help

aplay -l 
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: ALC268 Analog [ALC268 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 6: Si3054 Modem [Si3054 Modem]
  Subdevices: 0/1
  Subdevice #0: subdevice #0

---

### Post by kostkon on 2010-06-12
Did you try to setup your sound in System &#8594; Preferences &#8594; Sound? If no devices are listed in your sound preferences, then try disabling your modem in System &#8594; Administration &#8594; Hardware Drivers, reboot and then check your sound preferences again.

---

### Post by realmadridcf on 2010-06-12
hey thanks a lot 
as soon as removed that software modem ...sound driver came back..
but can you please explain what had happened??? the logic behind it?

---

### Post by lidex on 2010-06-13
> **realmadridcf said:**
> hey thanks a lot 
as soon as removed that software modem ...sound driver came back..
but can you please explain what had happened??? the logic behind it?
The modem driver was grabbing the audio output. You disabled it so sound can now be routed correctly through your audio subsystem to your speakers.

---

