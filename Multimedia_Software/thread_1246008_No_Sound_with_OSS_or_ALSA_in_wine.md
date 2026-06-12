---
title: "No Sound with OSS or ALSA in wine"
date: 2009-08-21
forum: Multimedia Software
---

### Post by panser on 2009-08-21
Hi,

I have a Acer Revo R3600 with nvidia ION and try to get sound by hdmi in wine. It works perfect with xbmc.

Trying to get Spotify to work with wine. My audio settings that works fine in xbmc is:

```
Audio Output: Digital
Audio Capable Device: plug:hdmi
Passthrough Output Device: hdmi
Downmix: On
```

This is the first time im using linux/ubuntu, so I might miss out som information, please ask me if you need anything else.

```
xbmc@htpc:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: ALC662 Analog [ALC662 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 3: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```


```
xbmc@htpc:~$ cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.18rc3.
```

```
xbmc@htpc:~$ uname -a
Linux htpc 2.6.28-15-generic #49-Ubuntu SMP Tue Aug 18 18:40:08 UTC 2009 i686 GNU/Linux
```

```
xbmc@htpc:~$ cat /etc/*-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=9.04
DISTRIB_CODENAME=jaunty
DISTRIB_DESCRIPTION="Ubuntu 9.04"
```

Winecfg, Audio -> OSS: Wave Out Devices: Generetic 10de NVIDIA MCP7A HDMI
Winecfg, Audio -> OSS: Mixer Devices: Generetic 10de NVIDIA MCP7A HDMI

Winecfg, Audio -> ALSA: Wave Out Devices: dmix:0 (can i change this to hdmi or plug:hdmi?)
Winecfg, Audio -> ALSA: Wave Out Devices: HDA Nvidia

---

