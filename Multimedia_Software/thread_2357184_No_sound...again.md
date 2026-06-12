---
title: "No sound...again"
date: 2017-03-30
forum: Multimedia Software
---

### Post by demiurg on 2017-03-30
Sound (thought HDMI) stopped working on my 16.04.2 LTS. Additionally, these is this:

```
demiurg@borjch-media:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
ALSA lib conf.c:3357:(snd_config_hooks_call) Cannot open shared library libasound_module_conf_pulse.so
ALSA lib control.c:954:(snd_ctl_open_noupdate) Invalid CTL hw:0
aplay: device_list:277: control open (0): No such file or directory
card 1: PCH [HDA Intel PCH], device 0: ALC283 Analog [ALC283 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```
The library in question is there...any ideas?

---

