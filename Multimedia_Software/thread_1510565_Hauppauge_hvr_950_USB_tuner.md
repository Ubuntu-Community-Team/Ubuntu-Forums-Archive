---
title: "Hauppauge hvr 950 USB tuner"
date: 2010-06-15
forum: Multimedia Software
---

### Post by ubunterooster on 2010-06-15
How do I watch tv with this?

In dmsg i get (edited for length) ```
[    3.496837] em28xx: New device WinTV HVR-980 @ 480 Mbps (2040:6513, interface 0, class 0)  
 [    3.497344] em28xx #0: chip ID is em2882/em2883  
 [    3.578927] HDA Intel 0000:00:14.2: PCI INT A -> GSI 16 (level, low) -> IRQ 16  
 [    3.702712] em28xx #0: i2c eeprom 00: 1a eb 67 95 40 20 13 65 d0 12 5c 03 82 1e 6a 18  
 [    3.702718] em28xx #0: i2c eeprom 10: 00 00 24 57 66 07 01 00 00 00 00 00 00 00 00 00  
 [    3.702723] em28xx #0: i2c eeprom 20: 46 00 01 00 f0 10 02 00 b8 00 00 00 5b 1c 00 00  
 [    3.702728] em28xx #0: i2c eeprom 30: 00 00 20 40 20 80 02 20 01 01 01 01 00 00 00 00  
 [    3.702732] em28xx #0: i2c eeprom 40: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  
 [    3.702737] em28xx #0: i2c eeprom 50: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  
 [    3.702741] em28xx #0: i2c eeprom 60: 00 00 00 00 00 00 00 00 00 00 18 03 34 00 30 00  
 [    3.702745] em28xx #0: i2c eeprom 70: 32 00 38 00 35 00 32 00 39 00 33 00 38 00 30 00  
 [    3.702750] em28xx #0: i2c eeprom 80: 00 00 1e 03 57 00 69 00 6e 00 54 00 56 00 20 00  
 [    3.702754] em28xx #0: i2c eeprom 90: 48 00 56 00 52 00 2d 00 39 00 38 00 30 00 00 00  
 [    3.702758] em28xx #0: i2c eeprom a0: 84 12 00 00 05 50 1a 7f d4 78 23 b1 fe d0 18 85  
 [    3.702763] em28xx #0: i2c eeprom b0: ff 00 00 00 04 84 0a 00 01 01 20 77 00 40 e4 7a  
 [    3.702767] em28xx #0: i2c eeprom c0: 1e f0 74 02 01 00 01 79 2a 00 00 00 00 00 00 00  
 [    3.702771] em28xx #0: i2c eeprom d0: 84 12 00 00 05 50 1a 7f d4 78 23 b1 fe d0 18 85  
 [    3.702775] em28xx #0: i2c eeprom e0: ff 00 00 00 04 84 0a 00 01 01 20 77 00 40 e4 7a  
 [    3.702780] em28xx #0: i2c eeprom f0: 1e f0 74 02 01 00 01 79 2a 00 00 00 00 00 00 00  
 [    3.702785] em28xx #0: EEPROM ID= 0x9567eb1a, EEPROM hash = 0x8c2726dd  
 [    3.702786] em28xx #0: EEPROM info:  
 [    3.702787] em28xx #0:    AC97 audio (5 sample rates)  
 [    3.702788] em28xx #0:    500mA max power  
 [    3.702790] em28xx #0:    Table at 0x24, strings=0x1e82, 0x186a, 0x0000  
 [    3.703605] em28xx #0: Identified as Hauppauge WinTV HVR 950 (card=16)  
 [    3.707822] tveeprom 0-0050: Hauppauge model 65201, rev A1C0, serial# 1997540  
 [    3.707824] tveeprom 0-0050: tuner model is Xceive XC3028 (idx 120, type 71)  
 [    3.707827] tveeprom 0-0050: TV standards PAL(B/G) PAL(I) PAL(D/D1/K) ATSC/DVB Digital (eeprom 0xd4)  
 [    3.707828] tveeprom 0-0050: audio processor is None (idx 0)  
 [    3.707830] tveeprom 0-0050: has radio  
 [    3.712286] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:14.2/input/input6  
 [    3.717133] tvp5150 0-005c: chip found @ 0xb8 (em28xx #0)  
 [    3.723254] HDA Intel 0000:01:05.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19  
 [    3.723300] HDA Intel 0000:01:05.1: setting latency timer to 64  
 [    3.727171] tuner 0-0061: chip found @ 0xc2 (em28xx #0)  
 [    3.741413] xc2028 0-0061: creating new instance  
 [    3.741417] xc2028 0-0061: type set to XCeive xc2028/xc3028 tuner  
 [    3.741424] usb 2-4: firmware: requesting xc3028-v27.fw  
 [    3.747230] xc2028 0-0061: Error: firmware xc3028-v27.fw not found.  
 [    3.747280] input: em28xx IR (em28xx #0) as /devices/pci0000:00/0000:00:13.2/usb2/2-4/input/input7  
 [    3.747831] em28xx #0: Config register raw data: 0xd0  
 [    3.748664] em28xx #0: AC97 vendor ID = 0xffffffff  
 [    3.749391] em28xx #0: AC97 features = 0x6a90  
 [    3.749393] em28xx #0: Empia 202 AC97 audio processor detected  
 [    3.813092] r8169: eth0: link up  
 [    3.813097] r8169: eth0: link up  
 [    3.910982] tvp5150 0-005c: tvp5150am1 detected.  
 [    4.011227] em28xx #0: v4l2 driver version 0.1.2  
 [    4.118715] em28xx #0: V4L2 video device registered as /dev/video0  
 [    4.118717] em28xx #0: V4L2 VBI device registered as /dev/vbi0  
 [    4.131363] usbcore: registered new interface driver em28xx  
 [    4.131366] em28xx driver loaded  
 [    4.135859] em28xx-audio.c: probing for em28x1 non standard usbaudio  
 [    4.135862] em28xx-audio.c: Copyright (C) 2006 Markus Rechberger  
 [    4.136230] Em28xx: Initialized (Em28xx Audio Extension) extension  
 [    4.155019] ------------[ cut here ]------------  

```

---

### Post by wkulecz on 2010-06-15
You have to download the firmware.  I got it to work to capture on 9.10, from the S-video input, but never could get the digital TV tuner to work.


What documentation exists can be had at:

[http://www.linuxtv.org/wiki/index.php/Main_Page](http://www.linuxtv.org/wiki/index.php/Main_Page)


If you succeed, please reply with your recipe for success.  I don't have time to mess with this any more at the moment.

---

### Post by ubunterooster on 2010-06-15
okay, I'll see what I get and post with any updates. Thanks for the link; I had to start somewhere.

---

### Post by wkulecz on 2010-06-15
They've changed the wiki a good bit since I last looked.  Maybe this will help:

[http://www.linuxtv.org/wiki/index.php/Hauppauge_WinTV-HVR-950Q](http://www.linuxtv.org/wiki/index.php/Hauppauge_WinTV-HVR-950Q)

---

### Post by ubunterooster on 2010-06-15
Looks promising: [http://www.linuxtv.org/wiki/index.php/Hauppauge_WinTV-HVR-950](http://www.linuxtv.org/wiki/index.php/Hauppauge_WinTV-HVR-950)

EDIT: I'm using 950-which is said to differ significantly from 950Q.

---

### Post by ubunterooster on 2010-06-15
stuck :( ```
ubunterooster@ubunterooster-server ~ $ wget http://www.steventoth.net/linux/xc5000/HVR-12x0-14x0-17x0_1_25_25271_WHQL.zip
--2010-06-15 19:54:04--  http://www.steventoth.net/linux/xc5000/HVR-12x0-14x0-17x0_1_25_25271_WHQL.zip
Resolving www.steventoth.net... 97.74.144.190
Connecting to www.steventoth.net|97.74.144.190|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 1545106 (1.5M) [application/zip]
Saving to: `HVR-12x0-14x0-17x0_1_25_25271_WHQL.zip'

100%[=====================================================================================================================================================================>] 1,545,106    782K/s   in 1.9s    

2010-06-15 19:54:06 (782 KB/s) - `HVR-12x0-14x0-17x0_1_25_25271_WHQL.zip' saved [1545106/1545106]

ubunterooster@ubunterooster-server ~ $ unzip -j HVR-12x0-14x0-17x0_1_25_25271_WHQL.zip Driver85/hcw85bda.sys
Archive:  HVR-12x0-14x0-17x0_1_25_25271_WHQL.zip
  inflating: hcw85bda.sys            
ubunterooster@ubunterooster-server ~ $ ./extract_xc3028.pl
bash: ./extract_xc3028.pl: No such file or directory
ubunterooster@ubunterooster-server ~ $ cd /usr/src/linux-headers-2.6.32-22-generic/Documentation/video4linux
ubunterooster@ubunterooster-server /usr/src/linux-headers-2.6.32-22-generic/Documentation/video4linux $ ./extract_xc3028.pl
bash: ./extract_xc3028.pl: Permission denied
ubunterooster@ubunterooster-server /usr/src/linux-headers-2.6.32-22-generic/Documentation/video4linux $ sudo ./extract_xc3028.pl
[sudo] password for ubunterooster: 
sudo: ./extract_xc3028.pl: command not found
ubunterooster@ubunterooster-server /usr/src/linux-headers-2.6.32-22-generic/Documentation/video4linux $ 

```:confused::confused::confused::confused::confused::confused::confused:

---

### Post by xc3RnbFO8P on 2010-06-16
Look at this:
[http://ubuntuforums.org/showpost.php?p=8414166&postcount=6]("http://ubuntuforums.org/showpost.php?p=8414166&postcount=6")

---

