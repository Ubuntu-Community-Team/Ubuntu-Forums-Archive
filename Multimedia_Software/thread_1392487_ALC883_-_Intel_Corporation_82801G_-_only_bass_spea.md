---
title: "ALC883 - Intel Corporation 82801G - only bass speaker works"
date: 2010-01-28
forum: Multimedia Software
---

### Post by genux05 on 2010-01-28
Hi all,

I have got kubuntu 9.10 installed with kernel
2.6.31-17-generic #54 SMP Thu Jan 7 10:35:04 GMT 2010 x86_64 GNU/Linux

and have a ACER 9815 WKHi laptop, which has 3 speakers, one underneath the laptop (base speaker) and two on the front.

The problem is that only the base speaker works, the headphone jack works fine but I cannot seem to use the front two speakers, any ideas ?

aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC883 Analog [ALC883 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC883 Digital [ALC883 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

/proc/asound/cards
 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xd2300000 irq 22
 1 [SAA7134        ]: SAA7134 - SAA7134
                      saa7133[0] at 0xd2005000 irq 16

cat /proc/asound/card0/codec#* | grep Codec
Codec: Realtek ALC883
Codec: Conexant ID 2bfa

I am using the HDA Intel (ALC883 Analog) in the Multimeda settings, when I try pulseaudio is does not work and goes back to HDA Intel.

if you want any more information, please just ask..

---

