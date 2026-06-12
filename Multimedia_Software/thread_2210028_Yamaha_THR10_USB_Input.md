---
title: "Yamaha THR10 USB Input"
date: 2014-03-08
forum: Multimedia Software
---

### Post by J._D._Trouteater on 2014-03-08
Hi! I'm trying to record from my Yamha THR10 via USB. I have the USB cord physically hooked up, and the good news is that output to the THR10 does work. When I play a movie on my laptop the sound comes out of the Yamaha.

However, recording from the Yamaha does not work. When I look in the Sound Settings GUI's input tab, I do not see the Yahama THR10 as an option. The only available choice is Internal Microphone.

Here are some facts:

```
trouteater@tibius:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: PCH [HDA Intel PCH], device 0: ALC269VB Analog [ALC269VB Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: THR10 [THR10], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

trouteater@tibius:~$ cat /proc/asound/cards
 0 [PCH            ]: HDA-Intel - HDA Intel PCH
                      HDA Intel PCH at 0xf7e10000 irq 44
 1 [THR10          ]: USB-Audio - THR10
                      Yamaha Corporation THR10 at usb-0000:00:14.0-2, high speed
```

I'm using Ubuntu 12.04 LTS 64-bit. I have Audacity and QARecord installed and they seem to work correctly. I just can't get the USB audio input to work. How can I record off of this really cool amp?!

---

### Post by J._D._Trouteater on 2014-03-12
Bump.

---

