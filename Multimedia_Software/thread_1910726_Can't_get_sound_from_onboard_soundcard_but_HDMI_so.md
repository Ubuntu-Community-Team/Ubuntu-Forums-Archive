---
title: "Can't get sound from onboard soundcard but HDMI sound works fine.`"
date: 2012-01-17
forum: Multimedia Software
---

### Post by strider3700 on 2012-01-17
I've got onboard sound and an nvidia card with HDMI out.   I managed to get sound going out of the nvidia for my XBMC setup but I can't get my onboard sound to actually do anything. I want XBMC to the hdmi and everything else to be local.   I'm still running ubuntu 10.10 if that matters.

 aplay -l lists
```

**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: VT1818S Analog [VT1818S Analog]
  Subdevices: 2/2
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
card 0: SB [HDA ATI SB], device 1: VT1818S Digital [VT1818S Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 3: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 0/1
  Subdevice #0: subdevice #0

```
when I try to test it I get
```
  aplay plughw:0,0 aplay -D plughw:0,0 /usr/share/sounds/alsa/Front_Center.wav 
plughw:0,0: No such file or directory

```

When I check the sound preferences it lists HDMI and internal audio for devices under hardware and output.  Changing to internal just means no sound at all.  

THis used to mostly work then suddenly stopped about 3 months ago I believe.  The only issue I used to have was sometimes youtube would have no sound until I reloaded the page.

---

