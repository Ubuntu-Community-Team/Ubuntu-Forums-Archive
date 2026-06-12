---
title: "Realtec ALC262 on TYAN S7025 no sound"
date: 2010-07-30
forum: Multimedia Software
---

### Post by Peno on 2010-07-30
Hi guys,

Just thought I would write a short summary on how I got my sound card (Realtec ALC262) working on Ubuntu 10.4 (64bit). This should really work on any other version of Ubuntu since I experienced the same problems of not having any sound on previous versions too.

Okay, so the problem was that my card was detected and all seems fine apart from that there was no sounds whatsoever. When I did:

aplay -l

I'd get:

**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC262 Analog [ALC262 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0

So the sound card was detected by the system. The module that needs to be loaded is snd-hda-intel and [B]I've added this line:

options snd-hda-intel model=hp-rp5700

at the end of 

/etc/modprobe.d/alsa-base.conf which solved the problem.[/B]

I was initially getting bad sound quality with hp_bpc module but then I checked this file to see what models were available by typing this:

zless /usr/share/doc/alsa-base/driver/HD-Audio-Models.txt.gz 

and I got this list, where I tested every single model and the best sound quality was by using: hp-rp5700

fujitsu       Fujitsu Laptop
hp-bpc        HP xw4400/6400/8400/9400 laptops
hp-bpc-d7000  HP BPC D7000
hp-tc-t5735   HP Thin Client T5735
hp-rp5700     HP RP5700
benq          Benq ED8
benq-t31      Benq T31
hippo         Hippo (ATI) with jack detection, Sony UX-90s
hippo_1       Hippo (Benq) with jack detection
sony-assamd   Sony ASSAMD
toshiba-s06   Toshiba S06
toshiba-rx1   Toshiba RX1
tyan          Tyan Thunder n6650W (S2915-E)
ultra         Samsung Q1 Ultra Vista model
lenovo-3000   Lenovo 3000 y410
nec           NEC Versa S9100
basic         fixed pin assignment w/o SPDIF
auto          auto-config reading BIOS (default)

Hope this was helpful to somebody,
Martin Peniak
--
PhD researcher in artificial intelligence
[www.martinpeniak.com](www.martinpeniak.com)

---

### Post by mirix on 2010-10-01
Thanks Peno,

I found exactly the same problem and the same solution with Debian Squeeze 64 bit. 

Regards,

Miro

---

