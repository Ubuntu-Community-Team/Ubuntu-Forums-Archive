---
title: "JACK Audio and HDMI"
date: 2013-09-13
forum: Multimedia Software
---

### Post by am6465 on 2013-09-13
Hey, all.

I'm trying use JACK Audio connection kit to direct the sound coming out of some of my applications to one of my video cards. I have everything set up except that when I load the hdmi output into jack, I only get 2-channels and I want 6 channels for 5.1 surround sound. The best explanation I found online is that the channel discovery is messed up because the channels are not listed in sequential order so JACK can't use nmap (or something like that). I haven't found a reliable way of testing this theory so it could be wrong. My adventures to trying to fix it had me trying to re-route using ttables but I don't think I did it correctly and all of the guides I saw were trying to get the hdmi out to just work. On my system, the hdmi works using just alsa or using pulseaudio as the sound server.

Some info on my system:
```

>>lspci
01:00.0 VGA compatible controller: NVIDIA Corporation GT218 [GeForce 210] (rev a2)
01:00.1 Audio device: NVIDIA Corporation High Definition Audio Controller (rev a1)
  ...



>>aplay -l
...
card 5: NVidia [HDA NVidia], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 5: NVidia [HDA NVidia], device 7: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 5: NVidia [HDA NVidia], device 8: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 5: NVidia [HDA NVidia], device 9: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
...

```

---

