---
title: "Lucid and Tvtime"
date: 2010-07-26
forum: Multimedia Software
---

### Post by dianemeeks on 2010-07-26
I have a Hauppage 950 tv tuner.  After some fine tuning, it worked fine on Hardy, Intrepid, and Jaunty.  However, I am still unable to get sound in tvtime using Lucid.  I've read a lot of posts that suggest pulse audio is to blame, but has anyone got it working?

---

### Post by rubylaser on 2010-07-26
Try this as a test.  I have have 950q and it works fine for me.
```
tvtime | arecord -D hw:1,0 -r 48000 -c 2 -f S16_LE | aplay -
```

---

### Post by dianemeeks on 2010-07-26
Thanks.  That didn't do the trick, but knowing that someone has theirs working gives me hope.  I was really starting to wonder if I was wasting my time.

---

### Post by rubylaser on 2010-07-26
Have you installed the firmware for your 950?  What does dmesg show you?

---

### Post by rubylaser on 2010-07-26
This section shows you how to do it if you haven't grabbed the newest firmware.
[http://www.linuxtv.org/wiki/index.php/Hauppauge_WinTV-HVR-950Q#Firmware]("http://www.linuxtv.org/wiki/index.php/Hauppauge_WinTV-HVR-950Q#Firmware")

---

### Post by dianemeeks on 2010-07-26
I have installed the firmware, which is a little different for the 950.  Here is the output of dmesg that deals with the tuner.
 12.119495] em28xx #0: i2c eeprom 00: 1a eb 67 95 40 20 13 65 d0 12 5c 03 82 1e 6a 18
[   12.119501] em28xx #0: i2c eeprom 10: 00 00 24 57 66 07 01 00 00 00 00 00 00 00 00 00
[   12.119506] em28xx #0: i2c eeprom 20: 46 00 01 00 f0 10 02 00 b8 00 00 00 5b 1c 00 00
[   12.119511] em28xx #0: i2c eeprom 30: 00 00 20 40 20 80 02 20 01 01 01 01 00 00 00 00
[   12.119516] em28xx #0: i2c eeprom 40: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
[   12.119520] em28xx #0: i2c eeprom 50: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
[   12.119525] em28xx #0: i2c eeprom 60: 00 00 00 00 00 00 00 00 00 00 18 03 34 00 30 00
[   12.119530] em28xx #0: i2c eeprom 70: 32 00 38 00 35 00 30 00 34 00 35 00 35 00 37 00
[   12.119535] em28xx #0: i2c eeprom 80: 00 00 1e 03 57 00 69 00 6e 00 54 00 56 00 20 00
[   12.119539] em28xx #0: i2c eeprom 90: 48 00 56 00 52 00 2d 00 39 00 38 00 30 00 00 00
[   12.119544] em28xx #0: i2c eeprom a0: 84 12 00 00 05 50 1a 7f d4 78 23 b1 fe d0 18 85
[   12.119549] em28xx #0: i2c eeprom b0: ff 00 00 00 04 84 0a 00 01 01 20 77 00 40 ed 19
[   12.119554] em28xx #0: i2c eeprom c0: 1e f0 74 02 01 00 01 79 82 00 00 00 00 00 00 00
[   12.119558] em28xx #0: i2c eeprom d0: 84 12 00 00 05 50 1a 7f d4 78 23 b1 fe d0 18 85
[   12.119563] em28xx #0: i2c eeprom e0: ff 00 00 00 04 84 0a 00 01 01 20 77 00 40 ed 19
[   12.119568] em28xx #0: i2c eeprom f0: 1e f0 74 02 01 00 01 79 82 00 00 00 00 00 00 00
[   12.119574] em28xx #0: EEPROM ID= 0x9567eb1a, EEPROM hash = 0x0aa525dd
[   12.119575] em28xx #0: EEPROM info:
[   12.119576] em28xx #0:	AC97 audio (5 sample rates)
[   12.119577] em28xx #0:	500mA max power
[   12.119578] em28xx #0:	Table at 0x24, strings=0x1e82, 0x186a, 0x0000
[   12.120244] em28xx #0: Identified as Hauppauge WinTV HVR 950 (card=16)
[   12.121057] tveeprom 2-0050: Hauppauge model 65201, rev A1C0, serial# 1972717
[   12.121059] tveeprom 2-0050: tuner model is Xceive XC3028 (idx 120, type 71)
[   12.121061] tveeprom 2-0050: TV standards PAL(B/G) PAL(I) PAL(D/D1/K) ATSC/DVB Digital (eeprom 0xd4)
[   12.121063] tveeprom 2-0050: audio processor is None (idx 0)
[   12.121065] tveeprom 2-0050: has radio
[   12.123281] tvp5150 2-005c: chip found @ 0xb8 (em28xx #0)
[   12.127280] tuner 2-0061: chip found @ 0xc2 (em28xx #0)
[   12.132015] xc2028 2-0061: creating new instance
[   12.132017] xc2028 2-0061: type set to XCeive xc2028/xc3028 tuner
[   12.132024] usb 1-2: firmware: requesting xc3028-v27.fw
[   12.142189] zc3xx: probe sif 0x0007
[   12.142688] zc3xx: probe sensor -> 000f
[   12.142689] zc3xx: Find Sensor PAS106
[   12.143244] gspca: probe ok
[   12.143259] usbcore: registered new interface driver zc3xx
[   12.143261] zc3xx: registered
[   12.150280] xc2028 2-0061: Loading 80 firmware images from xc3028-v27.fw, type: xc2028 firmware, ver 2.7
[   12.199967] sr 4:0:1:0: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   12.199972] sr 4:0:1:0: [sr1] Sense Key : Illegal Request [current] 
[   12.199975] sr 4:0:1:0: [sr1] Add. Sense: Illegal mode for this track
[   12.199981] sr 4:0:1:0: [sr1] CDB: Read(10): 28 00 00 00 00 00 00 00 02 00
[   12.199986] end_request: I/O error, dev sr1, sector 0
[   12.200927] sr 4:0:1:0: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   12.200931] sr 4:0:1:0: [sr1] Sense Key : Illegal Request [current] 
[   12.200933] sr 4:0:1:0: [sr1] Add. Sense: Illegal mode for this track
[   12.200938] sr 4:0:1:0: [sr1] CDB: Read(10): 28 00 00 00 00 00 00 00 02 00
[   12.200943] end_request: I/O error, dev sr1, sector 0
[   12.201762] sr 4:0:1:0: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   12.201765] sr 4:0:1:0: [sr1] Sense Key : Illegal Request [current] 
[   12.201767] sr 4:0:1:0: [sr1] Add. Sense: Illegal mode for this track
[   12.201770] sr 4:0:1:0: [sr1] CDB: Read(10): 28 00 00 00 00 00 00 00 02 00
[   12.201774] end_request: I/O error, dev sr1, sector 0
[   12.210042] xc2028 2-0061: Loading firmware for type=BASE MTS (5), id 0000000000000000.
[   12.440348] r8169: eth0: link down
[   12.440357] r8169: eth0: link down
[   12.441290] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   13.260234] xc2028 2-0061: Loading firmware for type=MTS (4), id 000000000000b700.
[   13.275873] xc2028 2-0061: Loading SCODE for type=MTS LCD NOGD MONO IF SCODE HAS_IF_4500 (6002b004), id 000000000000b700.

---

### Post by rubylaser on 2010-07-26
Your firmware is loading with errors.  

```
[ 12.199967] sr 4:0:1:0: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 12.199972] sr 4:0:1:0: [sr1] Sense Key : Illegal Request [current] 
[ 12.199975] sr 4:0:1:0: [sr1] Add. Sense: Illegal mode for this track
[ 12.199981] sr 4:0:1:0: [sr1] CDB: Read(10): 28 00 00 00 00 00 00 00 02 00
[ 12.199986] end_request: I/O error, dev sr1, sector 0
[ 12.200927] sr 4:0:1:0: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 12.200931] sr 4:0:1:0: [sr1] Sense Key : Illegal Request [current] 
[ 12.200933] sr 4:0:1:0: [sr1] Add. Sense: Illegal mode for this track
[ 12.200938] sr 4:0:1:0: [sr1] CDB: Read(10): 28 00 00 00 00 00 00 00 02 00
[ 12.200943] end_request: I/O error, dev sr1, sector 0
[ 12.201762] sr 4:0:1:0: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 12.201765] sr 4:0:1:0: [sr1] Sense Key : Illegal Request [current] 
[ 12.201767] sr 4:0:1:0: [sr1] Add. Sense: Illegal mode for this track
[ 12.201770] sr 4:0:1:0: [sr1] CDB: Read(10): 28 00 00 00 00 00 00 00 02 00
[ 12.201774] end_request: I/O error, dev sr1, sector 0
```

The firmware package that I linked to covers most of the ivtv in Linux.  You should be able to use those and have it properly load the firmware.  This is what it looks like when it loads correctly.

I just grabbed the section of mine that refers to my PVR-150 (I have 3 tuners in this box).  The firmware, I linked to works for my PVR-150s and my 950q.

```
[   11.026564] ivtv: Start initialization, version 1.4.1
[   11.026653] ivtv0: Initializing card 0
[   11.026656] ivtv0: Autodetected Hauppauge card (cx23416 based)
[   11.026880] ivtv 0000:04:09.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   11.081640] sky2 eth0: enabling interface
[   11.081752] tveeprom 0-0050: Hauppauge model 26582, rev C299, serial# 8454242
[   11.081756] tveeprom 0-0050: tuner model is TCL 2002N 5H (idx 99, type 50)
[   11.081759] tveeprom 0-0050: TV standards NTSC(M) (eeprom 0x08)
[   11.081762] tveeprom 0-0050: audio processor is CX25843 (idx 37)
[   11.081765] tveeprom 0-0050: decoder processor is CX25843 (idx 30)
[   11.081768] tveeprom 0-0050: has no radio
[   11.081772] ivtv0: Autodetected Hauppauge WinTV PVR-150
[   11.082294] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   11.183578] cx25840 0-0044: cx25843-23 found @ 0x88 (ivtv i2c driver #0)
[   11.191325] tuner 0-0061: chip found @ 0xc2 (ivtv i2c driver #0)
[   11.548475] wm8775 0-001b: chip found @ 0x36 (ivtv i2c driver #0)
[   11.643312] tuner-simple 0-0061: creating new instance
[   11.643317] tuner-simple 0-0061: type set to 50 (TCL 2002N)
[   11.644358] IRQ 17/ivtv0: IRQF_DISABLED is not guaranteed on shared IRQs
[   11.650818] ivtv0: Registered device video0 for encoder MPG (4096 kB)
[   11.650853] ivtv0: Registered device video32 for encoder YUV (2048 kB)
[   11.650885] ivtv0: Registered device vbi0 for encoder VBI (1024 kB)
[   11.651060] ivtv0: Registered device video24 for encoder PCM (320 kB)
[   11.651064] ivtv0: Initialized card: Hauppauge WinTV PVR-150
[   11.651142] ivtv: End initialization
[   12.280024] ivtv 0000:04:09.0: firmware: requesting v4l-cx2341x-enc.fw
[   12.344026] ivtv0: Loaded v4l-cx2341x-enc.fw firmware (376836 bytes)
[   12.550156] ivtv0: Encoder revision: 0x02060039
[   12.567505] cx25840 0-0044: firmware: requesting v4l-cx25840.fw
```

---

### Post by dianemeeks on 2010-07-28
Is there anything specific that I should be checking as for the reason the firmware is not loading properly?  I followed the directions from the link you gave me, but I'm still getting errors.  This might sound really stupid, but is it possible it's still trying to use the xc3028 firmware?

---

### Post by rubylaser on 2010-07-29
Yes that is a possibility.  Can you paste in another dmesg, now that you have the newer firmware in place.  Also, I goofed around a little with my 950q last night.  Can you try this line in a terminal to start tvtime, and see if you get audio.
```
tvtime | sox -r 48000 -c 2 -t ossdsp /dev/dsp2 -t ossdsp /dev/dsp
```

---

### Post by dianemeeks on 2010-07-29
Here's the dmesg output.  I also tried the other command but got the following error: sox FAIL formats: no handler for given file type `ossdsp'
   
11.970477] em28xx #0: i2c eeprom 00: 1a eb 67 95 40 20 13 65 d0 12 5c 03 82 1e 6a 18
[   11.970484] em28xx #0: i2c eeprom 10: 00 00 24 57 66 07 01 00 00 00 00 00 00 00 00 00
[   11.970489] em28xx #0: i2c eeprom 20: 46 00 01 00 f0 10 02 00 b8 00 00 00 5b 1c 00 00
[   11.970495] em28xx #0: i2c eeprom 30: 00 00 20 40 20 80 02 20 01 01 01 01 00 00 00 00
[   11.970500] em28xx #0: i2c eeprom 40: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
[   11.970504] em28xx #0: i2c eeprom 50: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
[   11.970509] em28xx #0: i2c eeprom 60: 00 00 00 00 00 00 00 00 00 00 18 03 34 00 30 00
[   11.970514] em28xx #0: i2c eeprom 70: 32 00 38 00 35 00 30 00 34 00 35 00 35 00 37 00
[   11.970519] em28xx #0: i2c eeprom 80: 00 00 1e 03 57 00 69 00 6e 00 54 00 56 00 20 00
[   11.970524] em28xx #0: i2c eeprom 90: 48 00 56 00 52 00 2d 00 39 00 38 00 30 00 00 00
[   11.970529] em28xx #0: i2c eeprom a0: 84 12 00 00 05 50 1a 7f d4 78 23 b1 fe d0 18 85
[   11.970534] em28xx #0: i2c eeprom b0: ff 00 00 00 04 84 0a 00 01 01 20 77 00 40 ed 19
[   11.970539] em28xx #0: i2c eeprom c0: 1e f0 74 02 01 00 01 79 82 00 00 00 00 00 00 00
[   11.970544] em28xx #0: i2c eeprom d0: 84 12 00 00 05 50 1a 7f d4 78 23 b1 fe d0 18 85
[   11.970549] em28xx #0: i2c eeprom e0: ff 00 00 00 04 84 0a 00 01 01 20 77 00 40 ed 19
[   11.970554] em28xx #0: i2c eeprom f0: 1e f0 74 02 01 00 01 79 82 00 00 00 00 00 00 00
[   11.970560] em28xx #0: EEPROM ID= 0x9567eb1a, EEPROM hash = 0x0aa525dd
[   11.970561] em28xx #0: EEPROM info:
[   11.970562] em28xx #0:	AC97 audio (5 sample rates)
[   11.970563] em28xx #0:	500mA max power
[   11.970565] em28xx #0:	Table at 0x24, strings=0x1e82, 0x186a, 0x0000
[   11.971226] em28xx #0: Identified as Hauppauge WinTV HVR 950 (card=16)
[   11.972057] tveeprom 2-0050: Hauppauge model 65201, rev A1C0, serial# 1972717
[   11.972060] tveeprom 2-0050: tuner model is Xceive XC3028 (idx 120, type 71)
[   11.972062] tveeprom 2-0050: TV standards PAL(B/G) PAL(I) PAL(D/D1/K) ATSC/DVB Digital (eeprom 0xd4)
[   11.972065] tveeprom 2-0050: audio processor is None (idx 0)
[   11.972066] tveeprom 2-0050: has radio
[   11.974265] tvp5150 2-005c: chip found @ 0xb8 (em28xx #0)
[   11.978256] tuner 2-0061: chip found @ 0xc2 (em28xx #0)
[   11.982909] xc2028 2-0061: creating new instance
[   11.982912] xc2028 2-0061: type set to XCeive xc2028/xc3028 tuner
[   11.982918] usb 1-2: firmware: requesting xc3028-v27.fw
[   11.990639] zc3xx: probe sif 0x0007
[   11.991137] zc3xx: probe sensor -> 000f
[   11.991139] zc3xx: Find Sensor PAS106
[   11.991691] gspca: probe ok
[   11.991711] usbcore: registered new interface driver zc3xx
[   11.991712] zc3xx: registered
[   11.994221] xc2028 2-0061: Loading 80 firmware images from xc3028-v27.fw, type: xc2028 firmware, ver 2.7
[   12.050033] xc2028 2-0061: Loading firmware for type=BASE MTS (5), id 0000000000000000.
[   12.284230] r8169: eth0: link down
[   12.284238] r8169: eth0: link down
[   12.285048] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   12.926731] vboxdrv: Trying to deactivate the NMI watchdog permanently...
[   12.926734] vboxdrv: Successfully done.
[   12.926736] vboxdrv: Found 4 processor cores.
[   12.926800] VBoxDrv: dbg - g_abExecMemory=ffffffffa03afa20
[   12.926841] vboxdrv: fAsync=0 offMin=0x334 offMax=0x17e4
[   12.927020] vboxdrv: TSC mode is 'synchronous', kernel timer mode is 'normal'.
[   12.927022] vboxdrv: Successfully loaded version 3.1.8 (interface 0x00100001).
[   13.090696] xc2028 2-0061: Loading firmware for type=MTS (4), id 000000000000b700.
[   13.106326] xc2028 2-0061: Loading SCODE for type=MTS LCD NOGD MONO IF SCODE HAS_IF_4500 (6002b004), id 000000000000b700.
[   13.236767] ppdev: user-space parallel port driver
[   13.311377] input: em28xx IR (em28xx #0) as /devices/pci0000:00/0000:00:12.2/usb1/1-2/input/input6
[   13.311592] em28xx #0: Config register raw data: 0xd0
[   13.312338] em28xx #0: AC97 vendor ID = 0xffffffff
[   13.312835] em28xx #0: AC97 features = 0x6a90
[   13.312837] em28xx #0: Empia 202 AC97 audio processor detected
[   13.472223] tvp5150 2-005c: tvp5150am1 detected.
[   13.580982] em28xx #0: v4l2 driver version 0.1.2
[   13.687704] em28xx #0: V4L2 video device registered as /dev/video1
[   13.687707] em28xx #0: V4L2 VBI device registered as /dev/vbi0
[   13.702583] usbcore: registered new interface driver em28xx
[   13.702586] em28xx driver loaded
[   13.705004] em28xx-audio.c: probing for em28x1 non standard usbaudio
[   13.705005] em28xx-audio.c: Copyright (C) 2006 Markus Rechberger
[   13.706175] Em28xx: Initialized (Em28xx Audio Extension) extension
[   13.780497] tvp5150 2-005c: i2c i/o error: rc == -19 (should be 1)
[   13.796052] xc2028 2-0061: attaching existing instance
[   13.796055] xc2028 2-0061: type set to XCeive xc2028/xc3028 tuner
[   13.796057] em28xx #0/2: xc3028 attached
[   13.796059] DVB: registering new adapter (em28xx #0)
[   13.796061] DVB: registering adapter 0 frontend 0 (LG Electronics LGDT3303 VSB/QAM Frontend)...
[   13.796293] Successfully loaded em28xx-dvb
[   13.796295] Em28xx: Initialized (Em28xx dvb Extension) extension
[   13.800373] tvp5150 2-005c: i2c i/o error: rc == -19 (should be 1)
[   13.820749] tvp5150 2-005c: i2c i/o error: rc == -19 (should be 1)
[   13.840876] tvp5150 2-005c: i2c i/o error: rc == -19 (should be 1)
[   13.840878] tvp5150 2-005c: *** unknown tvp0c00 chip detected.
[   13.840880] tvp5150 2-005c: *** Rom ver is 130.0
[   13.901756] tvp5150 2-005c: i2c i/o error: rc == -19 (should be 1)
[   13.920882] tvp5150 2-005c: i2c i/o error: rc == -19 (should be 1)
[   19.295736] r8169: eth0: link up
[   19.296529] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   30.210021] eth0: no IPv6 routers present
[   96.682106] hda-intel: IRQ timing workaround is activated for card #1. Suggest a bigger bdl_pos_adj.
[  112.781212] end_request: I/O error, dev fd0, sector 0
[  124.902350] end_request: I/O error, dev fd0, sector 0
[  290.701043] tvp5150 2-005c: tvp5150am1 detected.
[  290.951185] tvp5150 2-005c: tvp5150am1 detected.
[ 3754.171518] usb 2-5.1.3: USB disconnect, address 8
[ 3756.200588] usb 2-5.1.3: new high speed USB device using ehci_hcd and address 9
[ 3757.553491] usb 2-5.1.3: configuration #1 chosen from 1 choice
[ 3757.553906] scsi8 : SCSI emulation for USB Mass Storage devices
[ 3757.554133] usb-storage: device found at 9
[ 3757.554137] usb-storage: waiting for device to settle before scanning
[ 3762.560413] usb-storage: device scan complete
[ 3762.561482] scsi 8:0:0:0: Direct-Access     Crucial  Gizmo!           1100 PQ: 0 ANSI: 0 CCS
[ 3762.562398] sd 8:0:0:0: Attached scsi generic sg8 type 0
[ 3762.566963] sd 8:0:0:0: [sdg] 15663104 512-byte logical blocks: (8.01 GB/7.46 GiB)
[ 3762.568850] sd 8:0:0:0: [sdg] Write Protect is off
[ 3762.568860] sd 8:0:0:0: [sdg] Mode Sense: 43 00 00 00
[ 3762.568866] sd 8:0:0:0: [sdg] Assuming drive cache: write through
[ 3762.572225] sd 8:0:0:0: [sdg] Assuming drive cache: write through
[ 3762.572238]  sdg: sdg1
[ 3762.716733] sd 8:0:0:0: [sdg] Assuming drive cache: write through
[ 3762.716745] sd 8:0:0:0: [sdg] Attached SCSI removable disk
[ 4706.321154] warning: `VirtualBox' uses 32-bit capabilities (legacy support in use)
[ 8078.312026] tvp5150 2-005c: tvp5150am1 detected.
[ 8078.621454] xc2028 2-0061: Loading firmware for type=BASE MTS (5), id 0000000000000000.
[ 8079.712267] xc2028 2-0061: Loading firmware for type=MTS (4), id 000000000000b700.
[ 8079.728031] xc2028 2-0061: Loading SCODE for type=MTS LCD NOGD MONO IF SCODE HAS_IF_4500 (6002b004), id 000000000000b700.

---

### Post by rubylaser on 2010-07-29
Here's how to fix the sox error...
```
sudo apt-get install libsox-fmt-oss
```

Then try that command again.  And it looks like your firmware is loading correctly now.

---

### Post by dianemeeks on 2010-07-29
Woooooohooooo!  Thank you so much.  I found a solution for the error I got from the last command.  Once I fixed that, I got sound.

---

### Post by rubylaser on 2010-07-29
Great!  I'm glad that you finally got it working.  If you rename this thread as [SOLVED] someone else my benefit from this solution.

---

