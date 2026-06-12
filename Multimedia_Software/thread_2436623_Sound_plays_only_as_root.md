---
title: "Sound plays only as root"
date: 2020-02-10
forum: Multimedia Software
---

### Post by Neil Smith on 2020-02-10
Sound plays fine as root, but not as a non-root user.

Fresh install of 19.10, but on existing hardware. Sound was working on the previous install, until the upgrade from 18.10 failed and forced the reinstallation.

The sound cards are listed correctly by the non-root user:

```
neil@temujin:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: PCH [HDA Intel PCH], device 0: ALC898 Analog [ALC898 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 1: ALC898 Digital [ALC898 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: NVidia [HDA NVidia], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: NVidia [HDA NVidia], device 7: HDMI 1 [HDMI 1]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: NVidia [HDA NVidia], device 8: HDMI 2 [HDMI 2]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: NVidia [HDA NVidia], device 9: HDMI 3 [HDMI 3]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

(I want to use card 0.)

Various tests, such as speaker-test and aplay, work when run with sudo but not when run with normal permissions.

I seem to in the correct groups:

```
neil@temujin:~$ groups
neil adm cdrom sudo audio dip video plugdev lpadmin pulse pulse-access lxd sambashare
```

pavucontrol shows the devices, and the output visual indicator shows something when Firefox is playing a video (but no sound heard).

Any suggestions?

---

### Post by Neil Smith on 2020-02-11
Colour me stupid. Unplugging and replugging all the connections managed to solve the problem.

---

