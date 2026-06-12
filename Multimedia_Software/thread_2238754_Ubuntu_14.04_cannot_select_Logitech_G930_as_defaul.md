---
title: "Ubuntu 14.04 cannot select Logitech G930 as default playback device"
date: 2014-08-09
forum: Multimedia Software
---

### Post by alanc-stuart on 2014-08-09
So I recently installed Ubuntu 14.04 and I cannot select my Logitech G930 as the default playback device.
It shows up if I run 'aplay -l', and it also shows in the alsamixer, but in pavucontrol and in the sound settings it doesn't show up.

```
astuart@astuart-GA-970A-D3:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: ALC889 Analog [ALC889 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 1: ALC889 Digital [ALC889 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
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
**card 2: Headset [Logitech G930 Headset], device 0: USB Audio [USB Audio]**
**  Subdevices: 1/1**
[B]  Subdevice #0: subdevice #0
[/B]
```

I'd like to get my sound working so I can make a more permanent move from Windows so any help at this point would be appreciated.

---

### Post by alanc-stuart on 2014-08-14
Bump? Still having issues, the buttons on the headset appear to work, but it seems like Ubuntu is not recognizing it
as an audio device.

-Alan

---

