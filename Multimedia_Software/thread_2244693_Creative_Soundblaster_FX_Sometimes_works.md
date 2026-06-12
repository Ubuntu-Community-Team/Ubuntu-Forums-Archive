---
title: "Creative Soundblaster FX Sometimes works"
date: 2014-09-18
forum: Multimedia Software
---

### Post by tonksfx on 2014-09-18
I have a Creative Soundblaster Audigy FX (SB1570)

It works perfectly occasionally - sometimes i'll load up the comp and have sound straight away, sometimes I won't and just get terrible static, its pretty unpredictable but there must be a way i can ensure the right things load up every time?

I'm aiming to have the soundblaster working, as well as the onboard still working (for the front headphone ports if i had to use them).
I've been trying lots of suggestions but not hit on something that loads up every time yet. I also tried stopping the onboard audio from the bios which seemed to help a  little but still didn't guarantee it worked, and of course made all the other audio ports stop working.

sudo aplay -l


**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC1200 Analog [ALC1200 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 3: ALC1200 Digital [ALC1200 Digital]
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
card 2: Creative [HDA Creative], device 0: ALC898 Analog [ALC898 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

and under sudo dmesg

[   13.935780] input: HDA Creative Front Headphone as /devices/pci0000:00/0000:00:1c.1/0000:03:00.0/sound/card2/input26
[   13.935842] input: HDA Creative Line Out CLFE as /devices/pci0000:00/0000:00:1c.1/0000:03:00.0/sound/card2/input25
[   13.935898] input: HDA Creative Line Out Surround as /devices/pci0000:00/0000:00:1c.1/0000:03:00.0/sound/card2/input24
[   13.935952] input: HDA Creative Line Out Front as /devices/pci0000:00/0000:00:1c.1/0000:03:00.0/sound/card2/input23
[   13.936054] input: HDA Creative Line as /devices/pci0000:00/0000:00:1c.1/0000:03:00.0/sound/card2/input22
[   13.936118] input: HDA Creative Rear Mic as /devices/pci0000:00/0000:00:1c.1/0000:03:00.0/sound/card2/input21
[   13.936180] input: HDA Creative Front Mic as /devices/pci0000:00/0000:00:1c.1/0000:03:00.0/sound/card2/input20

---

