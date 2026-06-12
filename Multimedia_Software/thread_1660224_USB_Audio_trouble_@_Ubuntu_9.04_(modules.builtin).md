---
title: "USB Audio trouble @ Ubuntu 9.04 (modules.builtin?)"
date: 2011-01-05
forum: Multimedia Software
---

### Post by Lyrok on 2011-01-05
Hi guys,

I'm currently using Ubuntu 9.04 on an Overo Fire Gumstix board. I'm new to the OS, but so far everything works well, except for the USB Headset I want to use. It's not recognized when I plug it in (checked via lsusb & dmesg) and the information I got from the ALSA homepage is that the module "snd-usb-audio" is required if one wants to work with USB audio devices under ALSA.

Well, my problem is that I can't find the module in 9.04. The kernel is configured to provide alsa support (which prevents me from compiling the driver myself) and the alsa snd-* modules are present when I search for them (modprobe -l | grep snd), but snd-usb-audio is missing. However, in the file modules.builtin (/lib/modules/2.6.34/modules.builtin), kernel/sound/usb/snd-usb-audio.ko is mentioned.

Can anyone give me a hint on why / if the module is missing, or if it's supposed to be missing,and what I can do get myself a new one? 

Thanks in advance!

---

### Post by cchhrriiss121212 on 2011-01-05
Try puting this in a terminal:
arecord -l && aplay -l

---

### Post by Lyrok on 2011-01-10
Hi Chris,

arecord and aplay only show the onboard soundcard, but not the usb device:

```
**** List of PLAYBACK Hardware Devices ****
card 0: overo [overo], device 0: TWL4030 twl4030-0 []
  Subdevices: 1/1
  Subdevice #0: subdevice #0
**** List of CAPTURE Hardware Devices ****
card 0: overo [overo], device 0: TWL4030 twl4030-0 []
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```/proc/asound/cards and lsusb also don't list the usb device:

```
 0 [overo          ]: twl4030 - overo
                      overo (twl4030)
``````


Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


```

---

