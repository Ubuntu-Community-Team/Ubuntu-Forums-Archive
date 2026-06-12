---
title: "No sound in 9.04, but device seen in preferences"
date: 2009-09-10
forum: Multimedia Software
---

### Post by technophreak on 2009-09-10
Hi,

I've got no sound on 9.04. My soundcard is detected when i do aplay -l, and here is the result of it:

```

**** List of PLAYBACK Hardware Devices ****
card 0: nForce2 [NVidia nForce2], device 0: Intel ICH [NVidia nForce2]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: nForce2 [NVidia nForce2], device 2: Intel ICH - IEC958 [NVidia nForce2 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Solo1 [ESS ES1938 (Solo-1)], device 0: es-1938-1946 [ESS Solo-1]
  Subdevices: 1/2
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1

```

Also, if I go to System->Preferences->Sound, change my Music and Movies playback device to NVidia nForce2 with ALC655 NVidia nForce2 (OSS), and click Test, I get a beeping noise.

When I watch a YouTube video, I get a crackling noise which goes away if I mute the system volume.

Any ideas?

Thanks

---

### Post by technophreak on 2009-09-11
Anyone got any ideas? I need music :)

---

### Post by sabman83 on 2009-09-14
[http://ubuntuforums.org/showthread.php?t=1224787](http://ubuntuforums.org/showthread.php?t=1224787)

this worked for me

---

