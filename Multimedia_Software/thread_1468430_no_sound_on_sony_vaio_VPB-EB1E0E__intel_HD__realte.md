---
title: "no sound on sony vaio VPB-EB1E0E / intel HD / realtek audio (any version)"
date: 2010-05-01
forum: Multimedia Software
---

### Post by vicious6969 on 2010-05-01
*** solved ***

Not exactly sure but tried several fixes and I'm now getting sound.

Not overly loud but decent enough.  Funnily enough it sounds louder inside a windows virtual machine!

I'm a happy penguin now :P :P


Hi,

I've managed to get everything working including built in webcam on my laptop.The only thing I can't get is sound.  Please help me to complete the last piece of the jigsaw!

I have a Vaio VPC-EB1E0E which has "Intel HD Audio" . sound worked in Windows when I first booted up and used a Realtek Audio driver.

I'm using Kubuntu 10 RC1 - 64 bit (unable to get any earlier version of U/Kubuntu to work - unable to get Fedora to work either).

The closest info I've seen to helping is:

[http://ubuntuforums.org/archive/index.php/t-1434922.html](http://ubuntuforums.org/archive/index.php/t-1434922.html)

I installed it but wasn't sure how to configure and it still didn't work... (no idea what codec etc)

00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 05)
        Subsystem: Sony Corporation Device 9071
        Flags: bus master, fast devsel, latency 0, IRQ 22
        Memory at f6000000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>
        Kernel driver in use: HDA Intel
        Kernel modules: snd-hda-intel


aplay reveals:

ard 0: Intel [HDA Intel], device 0: ALC269 Analog [ALC269 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 3: INTEL HDMI [INTEL HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
andy@andy-laptop:~$ 

Please, please help me to get this working, I'd be soooo grateful!

Thanks

---

### Post by lidex on 2010-05-02
A common problem with a known alsa bug. The bug report states it is fixed in alsa 1.0.23

---

