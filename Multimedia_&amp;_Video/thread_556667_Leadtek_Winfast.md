---
title: "Leadtek Winfast"
date: 2007-09-21
forum: Multimedia &amp; Video
---

### Post by idtt2s on 2007-09-21
> lspci | grep Video
04:08.0 Multimedia video controller: Conexant CX23880/1/2/3 PCI Video and Audio Decoder (rev 05)
04:08.1 Multimedia controller: Conexant CX23880/1/2/3 PCI Video and Audio Decoder [Audio Port] (rev 05)


I use this to load the drivers
> 
modprobe bttv card=34 tuner=43


There is no video on any TV applications such as kdetv or tvtime.

> 
dmesg
[  252.956759] bttv: driver version 0.9.16 loaded
[  252.956765] bttv: using 8 buffers with 2080k (520 pages) each for capture
[29350.751835] tuner 2-0061: tuner type not set
[29350.892398] tuner 2-0061: tuner type not set

---

### Post by idtt2s on 2007-09-22
Bump

---

### Post by idtt2s on 2007-10-03
Second Bump!

---

### Post by idtt2s on 2007-10-18
Third bump?

---

### Post by ppera on 2007-10-23
This is not a bttv card from what I can see from your lspci output... try cx8800 instead of bttv (skip the card/tuner type, it should autodetect just fine).

---

