---
title: "AverMedia DVD EZMaker 7"
date: 2010-11-26
forum: Multimedia Software
---

### Post by sstt71 on 2010-11-26
Hi!
i successfuly install driver for sabj from avermedia site.
But the video0 does not appear in /dev

```
Linux stur-wm 2.6.31-14-generic-pae #48-Ubuntu SMP Fri Oct 16 15:22:42 UTC 2009 i686 GNU/Linux

$ lsusb
Bus 001 Device 006: ID 07ca:c039 AVerMedia Technologies, Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

$ lsmod | grep h826
h826d                 597512  0 
averusbh826d           87240  1 h826d
dvb_core               87364  1 h826d
videodev               36736  1 h826d
snd_pcm                75488  3 h826d,snd_ens1371,snd_ac97_codec
snd                    59204  9 h826d,snd_ens1371,snd_rawmidi,snd_seq_device,snd_ac97_codec,snd_pcm,snd_timer
```What's wrong?

---

