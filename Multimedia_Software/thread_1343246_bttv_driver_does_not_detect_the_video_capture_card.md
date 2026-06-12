---
title: "bttv driver does not detect the video capture card (pico2000)"
date: 2009-12-01
forum: Multimedia Software
---

### Post by sunh11373 on 2009-12-01
Hi

I installed a video capture card (pico2000) and seems the bttv drive cannot detect it.  Can anyone help here?

Here is my configuration:

>> uname -a
Linux home.org 2.6.31-15-generic #50-Ubuntu SMP Tue Nov 10 14:54:29 UTC 2009 i686 GNU/Linux

>> less /etc/modprobe.d/pico2000.conf
alias char-major-89 i2c-devb
options i2c-algo-bit bit_test=1

options videobuf-core debug=1
options videobuf-dma-sg debug=1
options tveeprom debug=1
options btcx-risc debug=1

alias char-major-81 videodev
alias char-major-81-0 bttv
options bttv gbuffers=32 card=77 tuner=4 radio=0 coring=1 full_luma_range=1 chroma_agc=1 combfilter=1 autoload=0 triton1=0 vsfx=0

The boot process does not seem to load the driver bttv and ignores the file "pico2000.conf". So I did manually by

>> sudo modprobe -v bttv 
insmod /lib/modules/2.6.31-15-generic/kernel/drivers/media/video/btcx-risc.ko debug=1
insmod /lib/modules/2.6.31-15-generic/kernel/drivers/media/video/videobuf-core.ko debug=1
insmod /lib/modules/2.6.31-15-generic/kernel/drivers/media/video/videobuf-dma-sg.ko debug=1
insmod /lib/modules/2.6.31-15-generic/kernel/drivers/i2c/algos/i2c-algo-bit.ko bit_test=1
insmod /lib/modules/2.6.31-15-generic/kernel/drivers/media/common/ir-common.ko 
insmod /lib/modules/2.6.31-15-generic/kernel/drivers/media/video/v4l1-compat.ko 
insmod /lib/modules/2.6.31-15-generic/kernel/drivers/media/video/videodev.ko 
insmod /lib/modules/2.6.31-15-generic/kernel/drivers/media/video/v4l2-common.ko 
insmod /lib/modules/2.6.31-15-generic/kernel/drivers/media/video/bt8xx/bttv.ko gbuffers=32 card=77 tuner=4 radio=0 coring=1 full_luma_range=1 chroma_agc=1 combfilter=1 autoload=0 triton1=0 vsfx=0

>> sudo dmesg
[49529.649889] Linux video capture interface: v2.00
[49529.656882] bttv: driver version 0.9.18 loaded
[49529.656884] bttv: using 32 buffers with 2080k (520 pages) each for capture

>> sudo lspci -v
....
08:06.0 Network controller: RaLink RT2760 Wireless 802.11n 1T/2R Cardbus
	Subsystem: RaLink RT2760 Wireless 802.11n 1T/2R Cardbus
	Flags: bus master, slow devsel, latency 32, IRQ 16
	Memory at fdfe0000 (32-bit, non-prefetchable) [size=64K]
	Capabilities: [40] Power Management version 3
	Kernel driver in use: rt2860
	Kernel modules: rt2860sta

[B]08:07.0 Multimedia video controller: Brooktree Corporation Bt879(??) Video Capture (rev 11)
	Flags: medium devsel, IRQ 10
	Memory at fde00000 (32-bit, prefetchable) [disabled] [size=4K]
	Capabilities: [44] Vital Product Data <?>
	Capabilities: [4c] Power Management version 0

08:07.1 Multimedia controller: Brooktree Corporation Bt878 Audio Capture (rev 11)
	Flags: medium devsel, IRQ 10
	Memory at fde01000 (32-bit, prefetchable) [disabled] [size=4K]
	Capabilities: [44] Vital Product Data <?>
	Capabilities: [4c] Power Management version 0
[/B]

08:08.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306 Fire II IEEE 1394 OHCI Link Layer Controller (rev c0) (prog-if 10)
	Subsystem: ASUSTeK Computer Inc. Device 81fe
	Flags: bus master, medium devsel, latency 32, IRQ 18
	Memory at fdfff000 (32-bit, non-prefetchable) [size=2K]
	I/O ports at ac00 [size=128]
	Capabilities: [50] Power Management version 2
	Kernel driver in use: ohci1394
	Kernel modules: firewire-ohci, ohci1394
 ....

>> sudo lspci -n 
...
08:06.0 0280: 1814:0701
[B]08:07.0 0400: 109e:036c (rev 11)
08:07.1 0480: 109e:0878 (rev 11)
[/B]08:08.0 0c00: 1106:3044 (rev c0)
...

There are no error messages at all. But the card is disabled :(

Any help is appreciated.


PS: related post [http://ubuntuforums.org/showthread.php?t=1341621](http://ubuntuforums.org/showthread.php?t=1341621)

---

