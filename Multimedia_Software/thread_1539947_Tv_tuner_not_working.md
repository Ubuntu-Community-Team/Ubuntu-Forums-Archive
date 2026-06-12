---
title: "Tv tuner not working"
date: 2010-07-27
forum: Multimedia Software
---

### Post by lev2580 on 2010-07-27
Hi.  I have an almost noname tv tuner card: Vivanco PCI EASY BG/DK. Lspci says it is Philips Semiconductors SAA7134/SAA7135HL Video Broadcast Decoder (rev 01). Dmesg detected it as a LifeView FlyVIDEO3000. I tried to configure it making the file at /etc/modprobe.d with the options card=2 tuner=5 (I found that also in dmesg). Still TvTime can't find any channels. I also tried using xawtv and scantv, but only managed to find two channels using ntsc somehow, but I have PAL BG/DK. (the card itself works on Windows, but it took me a while to configure the channels properly)  Can anyone help me?

---

### Post by VH-BIL on 2010-07-27
Sounds like an issue of bad signal, are you using an external antenna?

---

### Post by lev2580 on 2010-07-27
Hi. You see, in our place the whole city gets TV from a local head-end with a few antennas, from there distributed to everywhere. The TV and in Windows everything works, though it was better to configure the channels manually, than with autoscan.

---

### Post by VH-BIL on 2010-07-27
If you are able to get a few channels it seems that your hardware and software are working.

---

### Post by lev2580 on 2010-07-27
Sorry, I think things aren't set perfectly. It finds channels in NTSC with tvtime-scanner, but in tvtime these channels are also blue (as every other).

---

