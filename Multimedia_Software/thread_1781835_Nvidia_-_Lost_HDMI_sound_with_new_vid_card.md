---
title: "Nvidia - Lost HDMI sound with new vid card"
date: 2011-06-14
forum: Multimedia Software
---

### Post by evilluc on 2011-06-14
Hello,

The old Nvidia GT220 recently died in my HTPC and I replaced it with a new GT430. Sound over HDMI worked beautifully with the old card (after much trial & error,) but has now stopped working with the new card

I did a dist-upgrade from 10.10 to 11.04 in the process of troubleshooting and am running the included NVIDIA drivers:
```

uname -r
2.6.38-8-generic-pae

``````

cat /proc/driver/nvidia/version
NVRM version: NVIDIA UNIX x86 Kernel Module  270.41.06  Mon Apr 18 14:54:25 PDT 2011
GCC version:  gcc version 4.5.2 (Ubuntu/Linaro 4.5.2-8ubuntu4)

```It looks like the card is being detected:
```

aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: AD198x Analog [AD198x Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: AD198x Digital [AD198x Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```But I'm a little concerned that there are some devices missing? All of the HOWTO's for HDMI sound issues I've seen show multiple NVIDIA devices listed (I think usually 3, 5, 7, & 9?) Mine is only showing #3

I also do not have a valid ELD, which I'm sure is part of the issue. Perhaps this is related to the missing devices?

```

cat /proc/asound/card1/eld*
monitor_present         0
eld_valid               0
monitor_name
connection_type         HDMI
eld_version             [0x0] reserved
edid_version            [0x0] no CEA EDID Timing Extension block present
manufacture_id          0x0
product_id              0x0
port_id                 0x0
support_hdcp            0
support_ai              0
audio_sync_delay        0
speakers                [0xffff] FL/FR LFE FC RL/RR RC FLC/FRC RLC/RRC FLW/FRW FLH/FRH TC FCH
sad_count               0

```I'm not really sure where to go from here. I've tried beating my head on the wall, but that didn't seem to work :) Any advice would be greatly appreciated. Thank you!

EDIT - Forgot to mention that everything appears to be unmuted in alsamixer. When I run "aplay -D plughw:1,3 /usr/share/sounds/alsa/Front_Center.wav" I get no sound. I do however get sound from the headphone jack when I do the same command for the onboard sound card (0,0)

---

### Post by evilluc on 2011-06-14
Well, after completely re-installing alsa (I swear I've done this at least a few times!) it looks like everything is now being properly detected

```

aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: AD198x Analog [AD198x Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: AD198x Digital [AD198x Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 3: HDMI 0 [HDMI 0]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 7: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 8: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 9: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

Device 9 is playing sounds when I use aplay -D, so I think I'm in business

Thank you!

---

