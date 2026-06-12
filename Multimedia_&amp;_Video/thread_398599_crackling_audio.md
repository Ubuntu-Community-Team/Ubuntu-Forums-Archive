---
title: "crackling audio"
date: 2007-04-01
forum: Multimedia &amp; Video
---

### Post by eggdeng on 2007-04-01
On a fresh install of Edgy, I am getting persistent crackling when I try to play most types of sound files. My set up is as follows:

lspci output:
VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 30)

cat /proc/asound/cards
0 [V8233 ]: VIA8233 - VIA 8233
VIA 8233 with VIA1612A at 0x1800, irq 11
1 [modem ]: VIA82XX-MODEM - VIA 82XX modem
VIA 82XX modem at 0xe000, irq 11

cat/proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.12rc1

I have played around with all the device settings and am beginning to think it must be a codec problem. (I installed codecs with automatix2 to begin with, but then installed gxine and gxineplugin.)

The curious thing is that if I play back a particular .avi file (xViD ffmpeg)  before anything else, it seems, sometimes at least, to somehow clean the tubes & I can then play back most .mp3 and even .ram files without problems.

---

### Post by eggdeng on 2007-04-01
This tuned out to be a known problem with VIA VT8233, documented at
[http://www.mail-archive.com/alsa-user@lists.sourceforge.net/msg08159.html](http://www.mail-archive.com/alsa-user@lists.sourceforge.net/msg08159.html)
The fix is to add the option ```
options snd-via82xx index=0 dxs_support=2
``` to the end of /etc/modprobe.d/alsa-base.

---

