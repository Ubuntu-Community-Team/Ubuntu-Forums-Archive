---
title: "Various apps not working with vid capture (query dumps incl)"
date: 2010-03-18
forum: Multimedia Software
---

### Post by sergep71 on 2010-03-18
Greetings all... 

I'm running Karmic and over the weekend I tried to get vid capture to work thru xawtv and kdenlive and I'm not getting any joy.  Configuration and relevant queries follow:

My Very Funky PC setup:
socket 754 AMD Sempron 3000+ with passive cooling (non AMD64)
Biostar MB with Nforce3 250Gb chipset
1GB PC3200 DDR RAM
34GB SCSI coupled to a AIC789x card
NV31 GPU (FX5600 128MB)
dvd+-R floppy etc etc.

I have a few choices in the vid card dept...

USB: Dazzle Digital Photo Maker (recognized as a Global Village GV-7000)
PCI: WinTV model 38101 (Installed)
PCI Aurora Systems Fuse (excellent Mac card in its day, recognized as a Zoran 36067, not currently installed)

========================================================
dmesg query (snipped down to relevant parts)

[   32.072968] udev: starting version 147 
[   32.148049] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4 
[   32.152022] i2c-adapter i2c-0: nForce2 SMBus adapter at 0x4c00 
[   32.152043] i2c-adapter i2c-1: nForce2 SMBus adapter at 0x4c40 
[   32.575471] nvidia: module license 'NVIDIA' taints kernel. 
[   32.575477] Disabling lock debugging due to kernel taint 
[   32.927999] Linux video capture interface: v2.00 
[   33.029697] gameport: EMU10K1 is pci0000:02:07.1/gameport0, io 0xd800, speed 59659kHz 
[   33.109028] usbvision_probe: Global Village GV-007 (NTSC) found 
[   33.109106] USBVision[0]: registered USBVision Video device /dev/video0 [v4l2] 
[   33.109131] USBVision[0]: registered USBVision VBI device /dev/vbi0 [v4l2] (Not Working Yet!) 
[   33.115077] usbcore: registered new interface driver usbvision 
[   33.115083] USBVision USB Video Device Driver for Linux : 0.9.10 
[   33.150658] Bt87x 0000:02:0a.1: PCI INT A -> Link[APC3] -> GSI 18 (level, low) -> IRQ 18 
[   33.150914] bt87x0: Using board 1, analog, digital (rate 32000 Hz) 
[   33.294887] EMU10K1_Audigy 0000:02:07.0: PCI INT A -> Link[APC4] -> GSI 19 (level, low) -> IRQ 19 
[   33.429554] bttv: driver version 0.9.18 loaded 
[   33.429559] bttv: using 8 buffers with 2080k (520 pages) each for capture 
[   33.429609] bttv: Bt8xx card found (0). 
[   33.429629] bttv 0000:02:0a.0: PCI INT A -> Link[APC3] -> GSI 18 (level, low) -> IRQ 18 
[   33.429639] bttv0: Bt878 (rev 17) at 0000:02:0a.0, irq: 18, latency: 32, mmio: 0xe4000000 
[   33.429672] bttv0: detected: Hauppauge WinTV [card=10], PCI subsystem ID is 0070:13eb 
[   33.429675] bttv0: using: Hauppauge (bt878) [card=10,insmod option] 
[   33.429678] IRQ 18/bttv0: IRQF_DISABLED is not guaranteed on shared IRQs 
[   33.429709] bttv0: gpio: en=00000000, out=00000000 in=00fffffb [init] 
[   33.432194] bttv0: Hauppauge/Voodoo msp34xx: reset line init [5] 
[   33.432232] bt878 #0 [sw]: Test OK 
[   33.475356] tveeprom 3-0050: Hauppauge model 38101, rev B410, serial# 1974546 
[   33.475361] tveeprom 3-0050: tuner model is Philips FI1236 MK2 (idx 10, type 2) 
[   33.475365] tveeprom 3-0050: TV standards NTSC(M) (eeprom 0x08) 
[   33.475368] tveeprom 3-0050: audio processor is None (idx 0) 
[   33.475371] tveeprom 3-0050: has no radio 
[   33.475373] bttv0: Hauppauge eeprom indicates model#38101 
[   33.475376] bttv0: tuner type=2 
[   33.640466] bttv0: audio absent, no audio device found! 
[   33.671316] tuner 3-0061: chip found @ 0xc2 (bt878 #0 [sw]) 
[   33.816641] tuner-simple 3-0061: creating new instance 
[   33.816648] tuner-simple 3-0061: type set to 2 (Philips NTSC (FI1236,FM1236 and compatibles)) 
[   33.817329] bttv0: registered device video1 
[   33.817357] bttv0: registered device vbi1 
[   33.817374] bttv0: PLL: 28636363 => 35468950 .. ok 
[   33.888385] ACPI: PCI Interrupt Link [APC5] enabled at IRQ 16 
[   33.888393] nvidia 0000:01:00.0: PCI INT A -> Link[APC5] -> GSI 16 (level, low) -> IRQ 16 
[   33.888725] NVRM: loading NVIDIA UNIX x86 Kernel Module  173.14.20  Thu Jun 25 19:23:24 PDT 2009 
[   35.283703] saa7115 2-0024: saa7111 found (1f7111d1e200000) @ 0x48 (usbvision #0) 
[   36.741864] agpgart-amd64 0000:00:00.0: AGP 3.0 bridge 
[   36.741881] agpgart-amd64 0000:00:00.0: putting AGP V3 device into 8x mode 
[   36.741912] nvidia 0000:01:00.0: putting AGP V3 device into 8x mode 
[   65.827172] saa7115 2-0024: saa7111 found (1f7111d1e200000) @ 0x48 (usbvision #0) 
[  220.410702] xawtv.bin[2166]: segfault at b6b5b000 ip 00b9d056 sp bff3d0c8 error 4 in libc-2.10.1.so[b28000+13e000] 
[  225.012395] saa7115 2-0024: saa7111 found (1f7111d1e200000) @ 0x48 (usbvision #0) 
[  307.712361] xawtv.bin[2243]: segfault at b6a2d000 ip 00573056 sp bf8a6c08 error 4 in libc-2.10.1.so[4fe000+13e000] 
[  313.386278] saa7115 2-0024: saa7111 found (1f7111d1e200000) @ 0x48 (usbvision #0) 
[  452.289094] xawtv.bin[2252]: segfault at b6a23bd8 ip 00577c8d sp bfa73d20 error 4 in libpthread-2.10.1.so[572000+15000] 
[  482.042077] xawtv.bin[2272]: segfault at b6a8a000 ip 00d96056 sp bfab8648 error 4 in libc-2.10.1.so[d21000+13e000] 
[  612.402618] saa7115 2-0024: saa7111 found (1f7111d1e200000) @ 0x48 (usbvision #0) 
[  624.188037] xawtv.bin[2294]: segfault at b6b59000 ip 00c89056 sp bfed1da8 error 4 in libc-2.10.1.so[c14000+13e000] 
[  647.658745] saa7115 2-0024: saa7111 found (1f7111d1e200000) @ 0x48 (usbvision #0) 
[  649.381777] zapping[2328]: segfault at 47d0000 ip 08105bf8 sp bfe6db40 error 6 in zapping[8048000+137000] 
[  666.125569] saa7115 2-0024: saa7111 found (1f7111d1e200000) @ 0x48 (usbvision #0) 
[  917.679377] saa7115 2-0024: saa7111 found (1f7111d1e200000) @ 0x48 (usbvision #0) 
[ 1025.462508] saa7115 2-0024: saa7111 found (1f7111d1e200000) @ 0x48 (usbvision #0) 
[ 1820.468957] saa7115 2-0024: saa7111 found (1f7111d1e200000) @ 0x48 (usbvision #0) 
[ 1865.116045] usb 1-3: reset high speed USB device using ehci_hcd and address 3
=========================================================
Other queries:

serge@Bracken:~$ xawtv -hwscan
This is xawtv-3.95.dfsg.1, running on Linux/i686 (2.6.31-20-generic)
looking for available devices
port 325-356
    type : Xvideo, image scaler
    name : NV17 Video Texture

port 357-388
    type : Xvideo, image scaler
    name : NV05 Video Blitter

/dev/video0: OK                         [ -device /dev/video0 ]
    type : v4l2
    name : Global Village GV-007 (NTSC)
    flags:  capture  

/dev/video1: OK                         [ -device /dev/video1 ]
    type : v4l2
    name : BT878 video (Hauppauge (bt878))
    flags: overlay capture tuner 
=======================================================
serge@Bracken:~$ lspci | grep Bt878
02:0a.0 Multimedia video controller: Brooktree Corporation Bt878 Video Capture (rev 11)
02:0a.1 Multimedia controller: Brooktree Corporation Bt878 Audio Capture (rev 11)
serge@Bracken:~$ dmesg | grep bttv
[   33.429554] bttv: driver version 0.9.18 loaded
[   33.429559] bttv: using 8 buffers with 2080k (520 pages) each for capture
[   33.429609] bttv: Bt8xx card found (0).
[   33.429629] bttv 0000:02:0a.0: PCI INT A -> Link[APC3] -> GSI 18 (level, low) -> IRQ 18
[   33.429639] bttv0: Bt878 (rev 17) at 0000:02:0a.0, irq: 18, latency: 32, mmio: 0xe4000000
[   33.429672] bttv0: detected: Hauppauge WinTV [card=10], PCI subsystem ID is 0070:13eb
[   33.429675] bttv0: using: Hauppauge (bt878) [card=10,insmod option]
[   33.429678] IRQ 18/bttv0: IRQF_DISABLED is not guaranteed on shared IRQs
[   33.429709] bttv0: gpio: en=00000000, out=00000000 in=00fffffb [init]
[   33.432194] bttv0: Hauppauge/Voodoo msp34xx: reset line init [5]
[   33.475373] bttv0: Hauppauge eeprom indicates model#38101
[   33.475376] bttv0: tuner type=2
[   33.640466] bttv0: audio absent, no audio device found!
[   33.817329] bttv0: registered device video1
[   33.817357] bttv0: registered device vbi1
[   33.817374] bttv0: PLL: 28636363 => 35468950 .. ok
========================================================
serge@Bracken:~$ sudo lsmod | grep videodev
videodev               36736  8 tuner,tvaudio,tda7432,msp3400,bttv,saa7115,usbvision,v4l2_common
v4l1_compat            14336  1 videodev
========================================================
Contents of /etc/modprobe.d/bttv:

# i2c
alias char-major-89 i2c-devb
options i2c-algo-bit bit_test=1
# bttv
alias char-major-81 videodev
alias char-major-81-0 bttv
# My TV Card
options bttv card=10 tuner=2 radio=0 pll=1 adc_crush=0
------------------------------------------------------------------------

I tried using the Fuse but got virtually nowhere--device not showing on ls /dev/video* query, nor is recognized in xawtv or other apps, etc.

I installed the WinTV card and it recognized, but it didn't get signal from it from either Coax or composite from a VCR

Lastly I plugged in the Dazzle DPH and it displays video in xawtv but when I try to record a stream it crashes.  I try to record a stream in kdenlive and it shows garbage.

What I would like is to use the WinTV or Fuse, but will use the Dazzle if I have no other options.

I've installed every conceivable lib related to capture/playback, and have tvtime xawtv, kdenlive, and VLC installed.  I also have kino and stopmotion but I suspect they require 1394 input.

*Should* I install the AMD64 ubuntu? Any preferred libs or apps I should install?

*ANY* help on this would be greatly appreciated.

Thanks. :)

---

