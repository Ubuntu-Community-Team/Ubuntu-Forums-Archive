---
title: "No sound with Amarok"
date: 2009-11-09
forum: Multimedia Software
---

### Post by earthmumma on 2009-11-09
Hi,

I'm using 9.10 with Kubuntu. I can get sound for notifications, like when the computer starts. I can listen to sound from you tube, but when I start up Amarok I get a notification stating that "Audio playback device pulseaudio dosn't work, falling back to <blank>"

Pulse is my prime output device, with Nvidia CK804 with ALC850 as secondary.

I've tried to change the order of these devices in system settings, and although all seems to go ahead okay, if I return to system settings, nothing will have changed.

aplay - l gives

> **** List of PLAYBACK Hardware Devices ****
card 0: CK804 [NVidia CK804], device 0: Intel ICH [NVidia CK804]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: CK804 [NVidia CK804], device 2: Intel ICH - IEC958 [NVidia CK804 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


any ideas?

cheers

---

### Post by earthmumma on 2009-11-09
bump.

---

### Post by earthmumma on 2009-11-10
bump

---

### Post by jwest21 on 2010-02-08
Third bump's a charm.

I'm having the same problem except Nvidia has always been my default. Once I open Amarok nothing else I open has sound.

---

