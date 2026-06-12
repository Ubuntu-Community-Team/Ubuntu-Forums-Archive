---
title: "tv-card not working anymore since jaunty jackalope"
date: 2009-06-07
forum: Multimedia Software
---

### Post by skaface on 2009-06-07
Hey there,

as you can guess from the thread-title, i can't get my tv-card working anymore since the upgrade from 8.10 to 9.04.

Card: Medion MD 5044
Chipset: SAA 7134

***/etc/modules***:
> 
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp
saa7134 card=9 audio_clock_override=0x200000


This worked in 9.04 and i think the card initializes correctly at startup because shortly before the desktop comes up, there is a like 1 or 2 sec long noise, which doesn't appear when i remove the saa...-line from ***/etc/modules***.

Unfortunately i can't access the tv-card from any program i've tried so far. kdetv e.g. says at the video-menu the following:
> No Devices Found. Read FAQ at [www.kdetv.org](www.kdetv.org)

[www.kdetv.org](www.kdetv.org) doesn't seem to be the project-homepage anymore, so i certainly can't find the faq there...

Hope, that anybody here can help me get my tv-card up and running again. If any terminal-outputs could help you, just tell me!

thanks,

mik

---

### Post by xc3RnbFO8P on 2009-06-07
Show the output of **dmesg** in Terminal

---

### Post by skaface on 2009-06-07
> **Ringi said:**
> Show the output of **dmesg** in Terminal

Ok, here's the part that seems to be relevant to the tv-card. Please let me know, if something important is missing here:

> 
[   20.775610] Linux video capture interface: v2.00
[   20.821308] saa7130/34: v4l2 driver version 0.2.14 loaded
[   20.821358] saa7134 0000:05:02.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[   20.821364] saa7134[0]: found at 0000:05:02.0, rev: 1, irq: 23, latency: 64, mmio: 0xfeaffc00
[   20.821370] saa7134[0]: subsystem: 1131:0000, board: Medion 5044 [card=9,insmod option]
[   20.821419] saa7134[0]: board init: gpio is 10020
[   20.821421] saa7134[0]: seems there are two different versions of the MD5044
[   20.821422] saa7134[0]: (with the same ID) out there.  If sound doesn't work for
[   20.821423] saa7134[0]: you try the audio_clock_override=0x200000 insmod option.
[   20.886986] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   20.887039] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   20.924238] saa7134[0]: Huh, no eeprom present (err=-5)?
[   21.044120] tuner' 0-0043: chip found @ 0x86 (saa7134[0])
[   21.050103] tda9887 0-0043: creating new instance
[   21.050106] tda9887 0-0043: tda988[5/6/7] found
[   21.092594] All bytes are equal. It is not a TEA5767
[   21.092679] tuner' 0-0060: chip found @ 0xc0 (saa7134[0])
[   21.108599] tuner-simple 0-0060: creating new instance
[   21.108603] tuner-simple 0-0060: type set to 38 (Philips PAL/SECAM multi (FM1216ME MK3))
[   21.164221] saa7134[0]: registered device video0 [v4l2]
[   21.164265] saa7134[0]: registered device vbi0
[   21.164314] saa7134[0]: registered device radio0
[   21.176734] saa7134 ALSA driver for DMA sound loaded
[   21.176764] saa7134[0]/alsa: saa7134[0] at 0xfeaffc00 irq 23 registered as card -2
[   21.412026] lp0: using parport0 (interrupt-driven).


Maybe the output of xawtv and kdetv could be interesting too:

**xawtv**
> 
This is xawtv-3.95.dfsg.1, running on Linux/i686 (2.6.28-12-generic)
xinerama 0: 1680x1050+0+0
WARNING: No DGA direct video mode for this display.
WARNING: couldn't find framebuffer base address, try manual
         configuration ("v4l-conf -a <addr>")
v4l2: WARNING: framebuffer base address mismatch
v4l2: me=(nil) v4l=(nil)
Warning: Cannot convert string "-*-ledfixed-medium-r-*--39-*-*-*-c-*-*-*" to type FontStruct


**kdetv**
> 
kbuildsycoca running...
DCOP Cleaning up dead connections.
X Error: BadAccess (attempt to access private resource denied) 10
  Major opcode:  2
  Minor opcode:  0
  Resource id:  0x13c
Creating vbi proxy client, rev.
$Id: proxy-client.c,v 1.18 2008/02/19 00:35:21 mschimek Exp $
proxy_msg: connect: error 2, No such file or directory
Try to open V4L2 0.20 VBI device, libzvbi interface rev.
  $Id: io-v4l2.c,v 1.37 2008/02/19 00:35:20 mschimek Exp $
Opened /dev/vbi0
libzvbi:io-v4l2k:vbi_capture_v4l2k_new: Try to open V4L2 2.6 VBI device, libzvbi interface rev.
  $Id: io-v4l2k.c,v 1.49 2008/02/19 00:35:20 mschimek Exp $.
libzvbi:io-v4l2k:vbi_capture_v4l2k_new: Opened /dev/vbi0.
libzvbi:io-v4l2k:vbi_capture_v4l2k_new: /dev/vbi0 (Medion 5044) is a v4l2 vbi device,
driver saa7134, version 0x0000020e.
libzvbi:io-v4l2k:vbi_capture_v4l2k_new: Using streaming interface.
libzvbi:io-v4l2k:v4l2_get_videostd: Current scanning system is 525.
libzvbi:io-v4l2k:v4l2_update_services: Querying current vbi parameters...
libzvbi:io-v4l2k:v4l2_update_services: ...success.
libzvbi:print_vfmt: VBI capture parameters supported: 
libzvbi:print_vfmt: VBI capture parameters granted: 
libzvbi:raw_decoder:vbi3_raw_decoder_add_services: No services to add.
libzvbi:io-v4l2k:v4l2_update_services: Nyquist check passed.
libzvbi:io-v4l2k:v4l2_update_services: Request decoding of services 0x60000c7f, strict level -1.
libzvbi:sampling_par:_vbi_sampling_par_permit_service: Service 0x00000001 (Teletext System B 625 Level 1.5) requires videostd_set 0x1, have 0x0.
libzvbi:sampling_par:_vbi_sampling_par_permit_service: Service 0x00000003 (Teletext System B, 625) requires videostd_set 0x1, have 0x0.
libzvbi:sampling_par:_vbi_sampling_par_permit_service: Service 0x00000001 (Teletext System B 625 Level 1.5) requires videostd_set 0x1, have 0x0.
libzvbi:sampling_par:_vbi_sampling_par_permit_service: Service 0x00000003 (Teletext System B, 625) requires videostd_set 0x1, have 0x0.
libzvbi:sampling_par:_vbi_sampling_par_permit_service: Service 0x00000004 (Video Program System) requires videostd_set 0x1, have 0x0.
libzvbi:sampling_par:_vbi_sampling_par_permit_service: Service 0x00000400 (Wide Screen Signalling 625) requires videostd_set 0x1, have 0x0.
libzvbi:sampling_par:_vbi_sampling_par_permit_service: Service 0x00000008 (Closed Caption 625, field 1) requires videostd_set 0x1, have 0x0.
libzvbi:sampling_par:_vbi_sampling_par_permit_service: Service 0x00000010 (Closed Caption 625, field 2) requires videostd_set 0x1, have 0x0.
libzvbi:io-v4l2k:v4l2_update_services: Will capture services 0x00000060, added 0x60 commit=1.
libzvbi:io-v4l2k:v4l2_stream_alloc: Requesting 16 streaming i/o buffers.
libzvbi:io-v4l2k:v4l2_stream_alloc: Mapping 16 streaming i/o buffers.
libzvbi:io-v4l2k:vbi_capture_v4l2k_new: Successfully opened /dev/vbi0 (Medion 5044).
libzvbi:io-v4l2k:v4l2_stream_stop: Suspending stream.


The only think, that strikes my attention here, is the following line from kdetv-output:
> libzvbi:io-v4l2k:vbi_capture_v4l2k_new: Successfully opened /dev/vbi0 (Medion 5044).

Could it be, that it should normally open /dev/video0? If so, how can i tell kdetv to do so?

thanks

---

