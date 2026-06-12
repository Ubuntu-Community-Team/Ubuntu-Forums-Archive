---
title: "ASUS X550-LB internal and external (unplugged) Microphones swapped over"
date: 2017-12-28
forum: Multimedia Software
---

### Post by b-leigh on 2017-12-28
Hi,

I have seen that this is a pretty common problem with ASUS laptops, but none of the solutions I have found work. However, I have managed to pinpoint the problem more or less

I have an ASUS X550-LB with Xubuntu 16.04 and the internal microphone only works when I swap from the internal microphone to the external (unplugged) microphone in pauvcontrol.

However, after doing this the microphone does not work with the Wire desktop app (presumably because the app is still trying to access the wrong mike)

I have read of solutions by adding lines such as 
```
options snd-hda-intel model=asus-mode3
```

to 

```
/etc/modprobe.d/alsa-base.conf 
```

but none of these work for me

How do I 'reassign' the internal and external mikes so that they are the correct way round?

Preferably a 'one time' solution that I dont have to do every time I boot.

Thanks

Edit: These were asked for in other posts I have read ([for example]("https://ubuntuforums.org/showthread.php?t=1479399")):

```
**uname -a**

Linux leigh-X550LB 4.10.0-42-generic #46~16.04.1-Ubuntu SMP Mon Dec 4 15:57:59 UTC 2017 x86_64 x86_64 x86_64 GNU/Linux

**dpkg -l | grep "alsa"**

ii  alsa-base                                   1.0.25+dfsg-0ubuntu5                         all          ALSA driver configuration files
ii  alsa-utils                                  1.1.0-0ubuntu5                               amd64        Utilities for configuring and using ALSA

**head -n 1 /proc/asound/card*/codec#***

==> /proc/asound/card0/codec#0 <==
Codec: Intel Haswell HDMI

==> /proc/asound/card1/codec#0 <==
Codec: Realtek ALC3236

**inxi -Fx**

Audio:     Card-1 Intel 8 Series HD Audio Controller
           driver: snd_hda_intel bus-ID: 00:1b.0
           Card-2 Intel Haswell-ULT HD Audio Controller
           driver: snd_hda_intel bus-ID: 00:03.0
           Sound: Advanced Linux Sound Architecture v: k4.10.0-42-generic
[B]
arecord -l[/B]

**** List of CAPTURE Hardware Devices ****
card 1: PCH [HDA Intel PCH], device 0: ALC3236 Analog [ALC3236 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0

**aplay -l**

**** List of PLAYBACK Hardware Devices ****
card 0: HDMI [HDA Intel HDMI], device 3: HDMI 0 [HDMI 0]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 1: PCH [HDA Intel PCH], device 0: ALC3236 Analog [ALC3236 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
```

---

