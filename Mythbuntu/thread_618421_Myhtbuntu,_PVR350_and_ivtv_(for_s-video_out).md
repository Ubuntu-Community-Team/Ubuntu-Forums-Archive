---
title: "Myhtbuntu, PVR350 and ivtv (for s-video out)"
date: 2007-11-20
forum: Mythbuntu
---

### Post by yosemite610 on 2007-11-20
It would seem that everything is working on this system **except** for mythtv playing video out through the s-video out.

Using
```
sudo /sbin/rmmod saa7127
sudo /sbin/modprobe saa7127 test_image=1
```
Will display the color bars on my tv, but playing files from mythtv results in them being displayed only on the desktop (RGB Monitor).

dmesg:
```
[   26.016000] ivtv:  ==================== START INIT IVTV ====================
[   26.016000] ivtv:  version 1.0.0 (2.6.22-14-generic SMP mod_unload 586 ) loading
[   26.016000] ivtv0: Autodetected Hauppauge card (cx23415 based)
[   26.016000] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 5
[   26.016000] PCI: setting IRQ 5 as level-triggered
[   26.016000] ACPI: PCI Interrupt 0000:00:0d.0[A] -> Link [LNKC] -> GSI 5 (level, low) -> IRQ 5
[   26.016000] ivtv0: Unreasonably low latency timer, setting to 64 (was 32)
[   26.188000] Linux agpgart interface v0.102 (c) Dave Jones
[   28.124000] input: PC Speaker as /class/input/input2
[   28.964000] input: ImPS/2 Generic Wheel Mouse as /class/input/input3
[   28.968000] parport_pc 00:09: reported by Plug and Play ACPI
[   28.968000] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,EPP,ECP,DMA]
[   29.060000] pnp: Device 01:01.01 activated.
[   29.076000] gameport: NS558 PnP Gameport is pnp01:01.01/gameport0, io 0x201, speed 736kHz
[   29.248000] ivtv0: loaded v4l-cx2341x-enc.fw firmware (3457952928 bytes)
[   29.552000] ivtv0: loaded v4l-cx2341x-dec.fw firmware (3432091864 bytes)
[   29.816000] ivtv0: Encoder revision: 0x02050032
[   29.816000] ivtv0: Recommended firmware version is 0x02060039.
[   29.824000] ivtv0: Decoder revision: 0x02020023
[   29.916000] tveeprom 1-0050: The eeprom says no radio is present, but the tuner type
[   29.916000] tveeprom 1-0050: indicates otherwise. I will assume that radio is present.
[   29.916000] tveeprom 1-0050: Hauppauge model 48132, rev K268, serial# 8207945
[   29.916000] tveeprom 1-0050: tuner model is LG TAPE H001F MK3 (idx 68, type 47)
[   29.916000] tveeprom 1-0050: TV standards NTSC(M) (eeprom 0x08)
[   29.916000] tveeprom 1-0050: audio processor is MSP4448 (idx 27)
[   29.916000] tveeprom 1-0050: decoder processor is SAA7115 (idx 19)
[   29.916000] tveeprom 1-0050: has radio, has IR receiver, has no IR transmitter
[   29.916000] ivtv0: Autodetected Hauppauge WinTV PVR-350
[   30.244000] saa7115 1-0021: saa7115 found (1f7115d0e100000) @ 0x42 (ivtv i2c driver #0)
[   30.476000] saa7127 1-0044: saa7129 found @ 0x88 (ivtv i2c driver #0)
[   30.560000] ivtv0: i2c hardware 0x00000008 (msp3400) not found for command 0xc008561c!
[   30.564000] ivtv0: i2c hardware 0x00000008 (msp3400) not found for command 0x4008646d!
[   30.672000] ivtv0: i2c hardware 0x00000008 (msp3400) not found for command 0xc008561c!
[   30.672000] ivtv0: i2c hardware 0x00000008 (msp3400) not found for command 0xc008561c!
[   30.688000] pnp: Device 01:01.00 activated.
[   30.688000] pnp: Device 01:01.00 disabled.
[   30.688000] snd-opl3sa2-pnpbios: probe of 01:01.00 failed with error -2
[   30.692000] pnp: Device 01:01.00 activated.
[   30.800000] ivtv0: i2c hardware 0x00000008 (msp3400) not found for command 0xc008561c!
[   30.800000] ivtv0: Registered device video0 for encoder MPEG (4 MB)
[   30.800000] ivtv0: Registered device video32 for encoder YUV (2 MB)
[   30.800000] ivtv0: Registered device vbi0 for encoder VBI (1 MB)
[   30.800000] ivtv0: Registered device video24 for encoder PCM audio (1 MB)
[   30.800000] ivtv0: Registered device radio0 for encoder radio
[   30.800000] ivtv0: Registered device video16 for decoder MPEG (1 MB)
[   30.800000] ivtv0: Registered device vbi8 for decoder VBI (1 MB)
[   30.800000] ivtv0: Registered device vbi16 for decoder VOUT
[   30.800000] ivtv0: Registered device video48 for decoder YUV (1 MB)
[   31.068000] ivtv0: loaded v4l-cx2341x-init.mpg firmware (3432095056 bytes)
[   31.256000] ivtv0: Initialized Hauppauge WinTV PVR-350, card #0
[   31.256000] ivtv:  ====================  END INIT IVTV  ====================
```

lspci:
```
00:00.0 Host bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX Host bridge (rev 03)
00:01.0 PCI bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge (rev 03)
00:07.0 ISA bridge: Intel Corporation 82371AB/EB/MB PIIX4 ISA (rev 02)
00:07.1 IDE interface: Intel Corporation 82371AB/EB/MB PIIX4 IDE (rev 01)
00:07.2 USB Controller: Intel Corporation 82371AB/EB/MB PIIX4 USB (rev 01)
00:07.3 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ACPI (rev 02)
00:0b.0 Ethernet controller: 3Com Corporation 3c905B 100BaseTX [Cyclone] (rev 30)
00:0d.0 Multimedia video controller: Internext Compression Inc iTVC15 MPEG-2 Encoder (rev 01)
01:00.0 VGA compatible controller: nVidia Corporation NV5 [RIVA TNT2 Ultra] (rev 11)
```

 lsmod | grep ivtv:
```
ivtv_fb                19104  0
ivtv                  134928  2 ivtv_fb
i2c_algo_bit            7428  3 cx88xx,bttv,ivtv
cx2341x                13316  1 ivtv
tveeprom               16784  3 cx88xx,bttv,ivtv
videodev               29312  4 cx8800,cx88xx,bttv,ivtv
v4l2_common            18432  9 cx8800,cx88xx,bttv,msp3400,saa7115,tuner,ivtv,cx2341x,videodev
v4l1_compat            15364  3 bttv,ivtv,videodev
i2c_core               26112  10 cx88xx,bttv,lirc_i2c,msp3400,saa7115,tuner,ivtv,i2c_algo_bit,i2c_piix4,tveeprom
```

Also: I have the PVR350 out defined in setup/video/playback.

Any suggestions? Insight? Quaalude's? :confused:

---

### Post by superm1 on 2007-11-20
Per bug [https://bugs.edge.launchpad.net/ubuntu/gutsy/+source/mythtv/+bug/158562](https://bugs.edge.launchpad.net/ubuntu/gutsy/+source/mythtv/+bug/158562)

Please activate gutsy proposed and you should get the newer mythtv that includes the fix for this.

---

### Post by yosemite610 on 2007-11-21
> **superm1 said:**
> Per bug [https://bugs.edge.launchpad.net/ubuntu/gutsy/+source/mythtv/+bug/158562](https://bugs.edge.launchpad.net/ubuntu/gutsy/+source/mythtv/+bug/158562)

Please activate gutsy proposed and you should get the newer mythtv that includes the fix for this.

Thank you... I'm going to start over as I had MythBuntu 7.10 and was using their weekly updates, and frankly had tried so many fixes I think I've lost any sense of reference. Hope that makes sense...

So I'm starting with Ubuntu (non-myth) and then setting up ivtv, then mythtv...

Will report back.

*Edit: Can't install from 7.10 liveCD (display/desktop is corrupted regardless of what resolution/video-safe/etc.). Installing 7.04 liveCD, updating, then 7.10.*

---

### Post by yosemite610 on 2007-11-27
Well, I tried:
install 7.04, patch, upgrade to 7.10, patch, install MythTV, test. Then enable proposed, patch, test. All failed (same behavior; I can get color bars to display but nothing else).
Repeated above except instead of MythTV I installed MythBuntu, test, enable proposed, patch, test. All failed (Get color bars but no video).

Due to concerns for my sanity, I have dropped further attempts at getting s-video out to work on the PVR350, now using NVTV and the s-video out on my video card. I haven't quite gotten the config working (not dual-head so I need to find comfortable medium for resolution that works well on both) but at least I can play videos out through s-video...

---

