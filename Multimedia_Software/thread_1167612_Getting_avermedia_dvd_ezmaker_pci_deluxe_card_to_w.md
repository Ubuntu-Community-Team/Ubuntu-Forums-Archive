---
title: "Getting avermedia dvd ezmaker pci deluxe card to work on ubuntu"
date: 2009-05-23
forum: Multimedia Software
---

### Post by village_idio on 2009-05-23
i'm trying to get an avermedia dvd ezmaker pci deluxe card to work on ubuntu 9.04 in order
to convert some vhs tapes to a digital format.

judging from the dmesg output, everything seems to be okay:

[    8.537121] ivtv:  Start initialization, version 1.4.0
[    8.537227] ivtv0: Initializing card #0
[    8.537233] ivtv0: Autodetected AVerMedia EZMaker PCI Deluxe card (cx23416 based)
[    8.537969] ivtv 0000:01:06.0: PCI INT A -> Link[APC1] -> GSI 16 (level, low) -> IRQ 16
[    8.537977] ivtv0: Unreasonably low latency timer, setting to 64 (was 32)
[    8.591493] cx25840 2-0044: cx25843-24 found @ 0x88 (ivtv i2c driver #0)
[    8.592522] wm8739 2-001a: chip found @ 0x34 (ivtv i2c driver #0)
[    8.597461] ivtv0: Registered device video0 for encoder MPG (4096 kB)
[    8.597503] ivtv0: Registered device video32 for encoder YUV (2048 kB)
[    8.597564] ivtv0: Registered device vbi0 for encoder VBI (1024 kB)
[    8.597603] ivtv0: Registered device video24 for encoder PCM (320 kB)
[    8.597606] ivtv0: Initialized card #0: AVerMedia EZMaker PCI Deluxe
[    8.597640] ivtv:  End initialization
[   14.624025] ivtv 0000:01:06.0: firmware: requesting v4l-cx2341x-enc.fw
[   14.706802] ivtv0: Loaded v4l-cx2341x-enc.fw firmware (376836 bytes)
[   14.904138] ivtv0: Encoder revision: 0x02060039
[   14.919862] cx25840 2-0044: firmware: requesting v4l-cx25840.fw
[   18.107665] cx25840 2-0044: loaded v4l-cx25840.fw firmware (16382 bytes)

however, when i try the standard test: cat /dev/video0 > test.mpg i get a blank file.

any help would be appreciated.

---

### Post by xc3RnbFO8P on 2009-05-23
Try **cat /dev/video0 > /tmp/test.mpg**

---

### Post by village_idio on 2009-05-23
> **Ringi said:**
> Try **cat /dev/video0 > /tmp/test.mpg**

sorry, i made a typo; what i meant to write in my initial post was
cat /dev/vide00 > /tmp/test.mpg

---

### Post by xc3RnbFO8P on 2009-05-23
Try this:
> alias char-major-81 videodev
> alias char-major-81-0 ivtv

---

### Post by village_idio on 2009-05-23
> **Ringi said:**
> Try this:

$ alias char-major-81-0 ivtv
bash: alias: char-major-81-0: not found
bash: alias: ivtv: not found

$ alias char-major-81 videodev
bash: alias: char-major-81: not found
bash: alias: videodev: not found

---

