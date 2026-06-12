---
title: "Mic doesn't work in Skype, Viber, Google Chrome. Works in audacity. Help!"
date: 2018-08-28
forum: Multimedia Software
---

### Post by tinypie on 2018-08-28
Hello,
I've been trying to solve this for a few days now and it seems like I have tried everything and nothing works. Not sure what to do anymore, so I'm hoping to get some ideas here.
The mic works in audacity and weirdly AnyDesk also captures mic no problem, but no luck with Skype, Viber or Google Chrome. Had no issues with these programs on archlinux on the same machine.
My skype version is 8.29.0.41, my laptop is Asus X55VD, Ubuntu 18.04.1 LTS. Neither internal mic works, nor plugged in headset's mic.

AlsaInfo: [http://www.alsa-project.org/db/?f=bddf412863fa1e6cfb640ebcb554908fd5a37b1a](http://www.alsa-project.org/db/?f=bddf412863fa1e6cfb640ebcb554908fd5a37b1a)
```
[B]
lspci -v
[/B]     00:1b.0 Audio device: Intel Corporation 7 Series/C216 Chipset Family High Definition Audio Controller (rev 04)
    Subsystem: ASUSTeK Computer Inc. 7 Series/C216 Chipset Family High Definition Audio Controller
    Flags: bus master, fast devsel, latency 0, IRQ 29
    Memory at f7a10000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd_hda_intel

**uname -a**
    Linux my-PC 4.15.0-33-generic #36-Ubuntu SMP Wed Aug 15 16:00:05 UTC 2018 x86_64 x86_64 x86_64 GNU/Linux

**cat /proc/asound/card0/codec* | grep Codec**
    Codec: VIA VT1802
    Codec: Intel PantherPoint HDMI

**aplay -l**
**** List of PLAYBACK Hardware Devices ****
card 0: PCH [HDA Intel PCH], device 0: VT1802 Analog [VT1802 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 2: VT1802 Alt Analog [VT1802 Alt Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

Let me know if you guys need any other information.

Things I've tried so far (hopefully not forgetting anything):
[LIST=1]
[*]Checked if mic is not muted in pavucontrol, GNOME ALSA mixer and alsamixer in terminal. 
[*]Tried adding "options snd-hda-intel model" following model options: auto, laptop-micsense, ref and some other (sorry, cannot remember all). Currently have it on test. 
[*]Tried muting one channel of the mic. 
[*]Purged and reinstalled pulseaudio, alsa-base and alsa-utils. 
[*]Tried installing skype with snap install skype --classic. 
[*]Tried purging pulseaudio and alsa packages, and then installing alsa packages only. 
[/LIST]

Might have forgotten everything I tried, I'm going crazy here.

**EDIT:** Sorry, the issue was on the receiving machine!

---

