---
title: "How to enable surroud sound over HDMI?"
date: 2012-06-04
forum: Multimedia Software
---

### Post by icedfusion on 2012-06-04
After upgrading my receiver, I now have a lot less spdif optical ports and now many more HDMI ports.

Previously, I followed this guide:
[https://help.ubuntu.com/community/DigitalAC-3Pulseaudio](https://help.ubuntu.com/community/DigitalAC-3Pulseaudio)

to get AC3 over spdif for pass-thru working and everything was good.
I have stereo over HDMI but I cannot seem to get pass-thru working.

Does anyone know what you have to do to route the digital output to the HDMI rather than to the optical out?

I have tried pavucontrol - but hdmi is always digital stereo

Thanks

ice.

output of aplay -l
```

**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: ALC662 rev1 Analog [ALC662 rev1 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: ALC662 rev1 Digital [ALC662 rev1 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

---

### Post by icedfusion on 2012-06-05
Not a hint from anyone? 

Cheers

ice.

---

### Post by annie0716 on 2012-06-05
Try play digital audio through S/PDIF mode, without software decoding.

---

### Post by annie0716 on 2012-06-06
Please refer to the hdmi setting in extra-hdmi.conf and porting it into default.conf.

---

### Post by icedfusion on 2012-06-06
> **annie0716 said:**
> Please refer to the hdmi setting in extra-hdmi.conf and porting it into default.conf.

Thanks for the tips. I saw your post that you made with your issue, but you said you did not have even stereo working. 

I have HDMI Stereo working OK, and I ported some of the profiles from
```

/usr/share/pulseaudio/alsa-mixer/profile-sets/extra-hdmi.conf

```

to this file:
```

/usr/share/pulseaudio/alsa-mixer/profile-sets/default.conf

```

I then restarted pc, but I still can only select HDMI stereo from pavucontrol.

Cheers

ice.

---

