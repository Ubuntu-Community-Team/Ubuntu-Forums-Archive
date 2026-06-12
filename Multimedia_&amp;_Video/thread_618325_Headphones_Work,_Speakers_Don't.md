---
title: "Headphones Work, Speakers Don't"
date: 2007-11-20
forum: Multimedia &amp; Video
---

### Post by infamousjre on 2007-11-20
So, I've tried just about every howto on the forums and after one killed my GRUB, I'm on a fresh install of 7.04.

My problem is the sound. It works perfectly fine with headphones, but the speakers haven't made a sound yet.

Here's aplay -l
```
**** List of PLAYBACK Hardware Devices ****
card 0: A5451 [ALI 5451], device 0: ALI 5451 [ALI 5451]
  Subdevices: 31/32
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
...
  Subdevice #28: subdevice #28
  Subdevice #29: subdevice #29
  Subdevice #30: subdevice #30
  Subdevice #31: subdevice #31

```

and lspci -v
```
00:08.0 Multimedia audio controller: ALi Corporation M5451 PCI AC-Link Controller Audio Device (rev 02)
        Subsystem: Rioworks Unknown device 2036
        Flags: bus master, medium devsel, latency 64, IRQ 11
        I/O ports at 8400 [size=256]
        Memory at d0008000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>

```

I need music! :guitar:

---

### Post by mts-fi on 2007-11-20
I had problems with my audio too. Only working thing was USB-headset. This thread helped me: [https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/157151](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/157151)

If you are usin your headphones connected with 3.5mm plug, I think this wont help you.

---

### Post by infamousjre on 2007-11-20
upgraded to 7.10... no change, soundwise

---

### Post by hi.johng on 2008-03-06
> **infamousjre said:**
> upgraded to 7.10... no change, soundwise

Just wondering if here has been any further development on this problem?

i also have 7.10:

>   2.6.22-14-generic #1 SMP Tue Feb 12 07:42:25 UTC 2008 i686 GNU/Linux

here's the output from lspci -v

>   00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
          Subsystem: Dell Unknown device 0227

fascinating...

---

