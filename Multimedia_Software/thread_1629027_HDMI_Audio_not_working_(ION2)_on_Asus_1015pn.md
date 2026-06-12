---
title: "HDMI Audio not working (ION2) on Asus 1015pn"
date: 2010-11-23
forum: Multimedia Software
---

### Post by Eduardo Ribeiro on 2010-11-23
Hi there,

I bought the Asus 1015pn netbook, that comes with a ION2 with HDMI output. After install Ubuntu 10.10 on it, I've got everything working, except for the AUDIO over HDMI. 

I can see the NVIDIA ION2 sound card on Alsamixer and all the channels are um-muted. 
That's the return that I've got on aplay -l :

card 0: Intel [HDA Intel], device 0: ALC259 Analog [ALC259 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 3: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 7: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 8: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 9: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

Any Ideia of what should I do?
Tks,
Eduardo

---

### Post by mtron on 2011-01-23
hello! 

Get and install the latest nvidia binary drivers from the x-swat ppa [https://launchpad.net/~ubuntu-x-swat/+archive/x-updates](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates)

- open a terminal and type
```
aplay -l
```

you will get a list of Playback devices containing the analog HDA Intel on card0 and a number of NVidia HDMI devices on card1. Test with aplay which of the devices is the good one in your case (here it's device 8 on card 1)

- now add your hw device string to pulseaudio 

```
sudo gedit /etc/pulse/default.pa
```

> load-module module-alsa-sink device=hw:1,8

and restart pulseaudio or reboot your system. Now open the sound Preferences, Hardware Tab and check that the "HDMI Output" profile is enabled.

---

