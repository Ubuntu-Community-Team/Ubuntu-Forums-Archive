---
title: "Sebrent TV/FM (saa1730) card troubles"
date: 2008-03-10
forum: Multimedia &amp; Video
---

### Post by mrpixels0 on 2008-03-10
Well I am back  to ask for some help with this card, Normally I would have found the answer by now but unfortunately I have not had that much luck. Below is all the relevant info on my card:

Linux Version: Ubuntu 7.10 (fresh install, with restricted Nvidia driver active)

Dmesg output:

[  419.036726] saa7134 ALSA driver for DMA sound unloaded
[  419.074676] saa7130/34: v4l2 driver version 0.2.14 loaded
[  419.075003] saa7130[0]: found at 0000:01:01.0, rev: 1, irq: 23, latency: 64, mmio: 0xdddffc00
[  419.075010] saa7130[0]: subsystem: 1131:0000, board: :Zolid Xpert TV7134 [card=43,insmod option]
[  419.075016] saa7130[0]: board init: gpio is c04000
[  419.225356] tuner 0-0043: chip found @ 0x86 (saa7130[0])
[  419.225827] tda9887 0-0043: tda988[5/6/7] found @ 0x43 (tuner)
[  419.241335] tuner 0-0060: All bytes are equal. It is not a TEA5767
[  419.241339] tuner 0-0060: chip found @ 0xc0 (saa7130[0])
[  419.242229] tuner 0-0060: type set to 17 (Philips NTSC_M (MK2))
[  419.242233] tuner 0-0060: type set to 17 (Philips NTSC_M (MK2))
[  419.245851] saa7130[0]: Huh, no eeprom present (err=-5)?
[  419.253978] saa7130[0]: registered device video1 [v4l2]
[  419.254418] saa7130[0]: registered device vbi1
[  419.284504] saa7134 ALSA driver for DMA sound loaded
[  419.284539] saa7130[0]/alsa: saa7130[0] at 0xdddffc00 irq 23 registered as card -2
[  480.223571] saa7134 ALSA driver for DMA sound unloaded
[  480.272357] saa7130/34: v4l2 driver version 0.2.14 loaded
[  480.272718] saa7130[0]: found at 0000:01:01.0, rev: 1, irq: 23, latency: 64, mmio: 0xdddffc00
[  480.272727] saa7130[0]: subsystem: 1131:0000, board: :Zolid Xpert TV7134 [card=43,insmod option]
[  480.272736] saa7130[0]: board init: gpio is c04000
[  480.421954] tuner 0-0043: chip found @ 0x86 (saa7130[0])
[  480.422260] tda9887 0-0043: tda988[5/6/7] found @ 0x43 (tuner)
[  480.437937] tuner 0-0060: All bytes are equal. It is not a TEA5767
[  480.437942] tuner 0-0060: chip found @ 0xc0 (saa7130[0])
[  480.438405] tuner 0-0060: type set to 42 (Philips 1236D ATSC/NTSC dual in)
[  480.438410] tuner 0-0060: type set to 42 (Philips 1236D ATSC/NTSC dual in)
[  480.441625] saa7130[0]: Huh, no eeprom present (err=-5)?
[  480.449790] saa7130[0]: registered device video1 [v4l2]
[  480.450067] saa7130[0]: registered device vbi1
[  480.472951] saa7134 ALSA driver for DMA sound loaded
[  480.473269] saa7130[0]/alsa: saa7130[0] at 0xdddffc00 irq 23 registered as ca

lspci output:

01:01.0 Multimedia controller: Philips Semiconductors SAA7130 Video Broadcast Decoder (rev 01)

here is what I am using my /etc/modprobe.d/saa1734 config file:

alias char-major-81 videodev
alias char-major-81-0 saa7134
options saa7134 card=43 tuner=42 video_nr=1 vbi_nr=1 radio_nr=1

so far I have tried all of the philips tuners that support FM / NTSC and the same with card types I have tried the Sbrent SBT TV/FM as well as the Lifeview 3000 TV/FM Gold seris card numbers.

I have been to Gentoo's wiki, Linuxtv and a kernel wiki with some info about this card everything around the net says this card works with tv and radio and I have followed all the instructions nothing seems to work at all, if anyone has had this card working please tell me how you went about it please.

I would really be in your debt.

Thanks for taking time to read and help me.

MP0

Edit New Info: 

I got the tv card and the radio working (I.E. tv has great picture and radio get a good signal but no sound output).
Now I got an error report that says :2008-03-10T00:19:59 AlsaSound::readPlaybackMixerVolume: error while reading volume from hwplug:0,0.
it seems even with a pass through cable connected to line out of tvcard to line in on sound card won't work because I guess the software can't make
a connection to the saa1734 pcm Hardware ?.

---

### Post by mrpixels0 on 2008-03-13
Gonna give this a bump, I have tried compiling VL4 from the repositories, but I think I narrowed the problem down to my HDA Intel onboard sound system not being compatible with my TV/FM card since the card cannot get a mixer it can use from the OSS side of things or Alsa for that matter. So i am gonna try another sound card and disable the onboard and see if that helps.

In the mean time if some one knows how to fix this problem using onboard Audio I would be open to suggestions and would like any input the community might have.

thanks for reading and sorry about the bump.

MP0

well I have Finally Solved the problem and now everything is working and I will post an Exact how to for this TV/FM card so if another person has it they won't have to go crazy trying to figure out how to get it going. :)

---

