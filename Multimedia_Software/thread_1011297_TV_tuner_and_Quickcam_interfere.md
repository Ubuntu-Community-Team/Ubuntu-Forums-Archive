---
title: "TV tuner and Quickcam interfere"
date: 2008-12-14
forum: Multimedia Software
---

### Post by mkljun on 2008-12-14
Hi!

I'm trying to set up a TV tuner and a webcam on Ubuntu 8.10 (kernel 2.6.27-7-generic). 

A webcam is Logitech Quickcam:
```
mkljun@MD3K:~$ lsusb
Bus 002 Device 002: ID 046d:08f6 Logitech, Inc. Quickcam Messenger Plus
```

Tv tuner is:
```
mkljun@MD3K:~$ lspci
00:08.0 Multimedia video controller: Brooktree Corporation Bt878 Video Capture (rev 11)
00:08.1 Multimedia controller: Brooktree Corporation Bt878 Audio Capture (rev 11)
```

My problem is that only one device is set up at boot time for the TV tuner (I can watch TV with TV time). Webcam has no device attached to it.

```
mkljun@MD3K:~$ ls /dev/vid*
/dev/video0
```

Below is a list of loaded kernel modules and both Bttv and Quickcam are loaded:

```
mkljun@MD3K:~$ lsmod 
Module                  Size  Used by
quickcam               81188  0
video                  25104  0 
output                 11008  1 video
tuner_simple           22288  1 
tuner_types            21888  1 tuner_simple
tuner                  33096  0 
tvaudio                30780  0 
bttv                  171028  0 
ir_common              48132  1 bttv
compat_ioctl32          9344  1 bttv
i2c_algo_bit           14340  1 bttv
v4l2_common            19840  3 tuner,tvaudio,bttv
videobuf_dma_sg        20612  1 bttv
videobuf_core          26628  2 bttv,videobuf_dma_sg
snd_ac97_codec        111652  1 snd_intel8x0
btcx_risc              12552  1 bttv
tveeprom               20228  1 bttv
i2c_core               31892  8 tuner_simple,tea5767,tuner,tvaudio,bttv,i2c_algo_bit,v4l2_common,tveeprom
videodev               41344  3 quickcam,tuner,bttv
v4l1_compat            22404  1 videodev
usbcore               148848  6 quickcam,snd_usb_audio,snd_usb_lib,ohci_hcd,ehci_hcd
```

If I compile the driver for webcam manually it always interferes with TV tuner. Here's the part where it brakes:

```
mkljun@MD3K:~/qc/qc-usb-messenger-1.8$ ./quickcam.sh
...
[ 3165.927010] bttv0: PLL can sleep, using XTAL (28636363).
[ 3165.929127] bttv0: PLL: 28636363 => 35468950 .. ok
[ 4626.912879] usbcore: deregistering interface driver quickcam
[ 4626.961925] quickcam: QuickCam USB camera found (driver version QuickCam USB 0.6.6 $Date: 2006/11/04 08:38:14 $)
[ 4626.961943] quickcam: Kernel:2.6.27-7-generic bus:2 class:FF subclass:FF vendor:046D product:08F6
[ 4626.972805] usbcore: registered new interface driver quickcam
[ 5393.272042] bttv0: timeout: drop=22 irq=33028/62503, risc=2d715024, bits: HSYNC OFLOW FDSR
[ 5437.948043] bttv0: timeout: drop=179 irq=36327/65814, risc=2d7e4024, bits: HSYNC OFLOW FDSR
[ 5475.716045] bttv0: timeout: drop=232 irq=39946/69458, risc=2d7e3024, bits: HSYNC OFLOW FDSR
[ 5489.440030] bttv0: timeout: drop=299 irq=40926/70441, risc=292ed034, bits: HSYNC OFLOW FDSR
[ 5509.248031] bttv0: timeout: drop=355 irq=42559/72074, risc=2bf49024, bits: HSYNC OFLOW FDSR
[!] The QuickCam driver failed to load!
...
```

Anyway, the webcam is not working but it used to work on a PC with 7.10 withouth TV tuner. Is there a way to set up the device manually or something similar?

Thans for the answer!

lp mk

PS : dmesg gives me this at the startup

```
...
[   13.647135] Linux video capture interface: v2.00
[   13.713840] quickcam: QuickCam USB camera found (driver version QuickCam USB 0.6.6 $Date: 2006/11/04 08:38:14 $)
[   13.713849] quickcam: Kernel:2.6.27-7-generic bus:2 class:FF subclass:FF vendor:046D product:08F6
[   13.722061] usbcore: registered new interface driver quickcam
[   14.054082] usbcore: registered new interface driver snd-usb-audio
[   14.264356] Intel ICH 0000:00:02.7: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[   14.563267] bttv: driver version 0.9.17 loaded
[   14.563273] bttv: using 8 buffers with 2080k (520 pages) each for capture
[   14.592050] intel8x0_measure_ac97_clock: measured 54212 usecs
[   14.592056] intel8x0: clocking to 48000
[   14.595878] bttv: Bt8xx card found (0).
[   14.595911] bttv 0000:00:08.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[   14.595927] bttv0: Bt878 (rev 17) at 0000:00:08.0, irq: 19, latency: 64, mmio: 0xcfffe000
[   14.595953] bttv0: detected: Terratec TValue Radio [card=66], PCI subsystem ID is 153b:1135
[   14.595958] bttv0: using: Terratec TValueRadio [card=66,autodetected]
[   14.596064] bttv0: gpio: en=00000000, out=00000000 in=00feefff [init]
[   14.596212] bttv0: tuner type=5
[   14.596218] bttv0: i2c: checking for MSP34xx @ 0x80... not found
[   14.596811] bttv0: i2c: checking for TDA9875 @ 0xb0... not found
[   14.597397] bttv0: i2c: checking for TDA7432 @ 0x8a... not found
[   14.895728] input: PC Speaker as /devices/platform/pcspkr/input/input4
[   14.994512] All bytes are equal. It is not a TEA5767
[   14.994628] tuner' 0-0060: chip found @ 0xc0 (bt878 #0 [sw])
[   15.026584] tuner-simple 0-0060: creating new instance
[   15.026591] tuner-simple 0-0060: type set to 5 (Philips PAL_BG (FI1216 and compatibles))
[   15.036739] bttv0: registered device video0
[   15.036886] bttv0: registered device vbi0
[   15.037040] bttv0: registered device radio0
[   15.037077] bttv0: PLL: 28636363 => 35468950 .. ok

```

---

