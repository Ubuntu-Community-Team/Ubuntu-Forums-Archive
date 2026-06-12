---
title: "Analog TV tuner not working anymore"
date: 2010-06-02
forum: Multimedia Software
---

### Post by jwolansk on 2010-06-02
hello,
I've been searching high and low what might be a problem here. 
The Tuner is Pinnacle PCTV USB2. Yesterday it installed nicely and I had a video in tvtime

I'm using ubuntu 10.04

here is the dump from /var/log/messages from may 31st
```
May 31 17:16:34 d430 kernel: [ 4993.160123] usb 1-5: new high speed USB device using ehci_hcd and address 7
May 31 17:16:35 d430 kernel: [ 4993.329288] usb 1-5: configuration #1 chosen from 1 choice
May 31 17:16:35 d430 kernel: [ 4993.459711] Linux video capture interface: v2.00
May 31 17:16:35 d430 kernel: [ 4993.523637] em28xx: New device Pinnacle Systems GmbH PCTV USB2 PAL/SECAM @ 480 Mbps (2304:0208, interface 0, class 0)
May 31 17:16:35 d430 kernel: [ 4993.523747] em28xx #0: chip ID is em2820 (or em2710)
May 31 17:16:35 d430 kernel: [ 4993.688883] em28xx #0: i2c eeprom 00: 1a eb 67 95 04 23 08 02 10 00 1e 03 98 2a 6a 2e
May 31 17:16:35 d430 kernel: [ 4993.688912] em28xx #0: i2c eeprom 10: 00 00 06 57 6e 00 00 00 8e 00 00 00 07 00 00 00
May 31 17:16:35 d430 kernel: [ 4993.688936] em28xx #0: i2c eeprom 20: 16 00 01 00 00 00 00 00 00 00 00 00 00 00 00 00
May 31 17:16:35 d430 kernel: [ 4993.688960] em28xx #0: i2c eeprom 30: 00 00 20 40 20 80 02 20 10 01 00 00 00 00 00 00
May 31 17:16:35 d430 kernel: [ 4993.688984] em28xx #0: i2c eeprom 40: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
May 31 17:16:35 d430 kernel: [ 4993.689007] em28xx #0: i2c eeprom 50: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
May 31 17:16:35 d430 kernel: [ 4993.689030] em28xx #0: i2c eeprom 60: 00 00 00 00 00 00 00 00 00 00 2e 03 50 00 69 00
May 31 17:16:35 d430 kernel: [ 4993.689054] em28xx #0: i2c eeprom 70: 6e 00 6e 00 61 00 63 00 6c 00 65 00 20 00 53 00
May 31 17:16:35 d430 kernel: [ 4993.689078] em28xx #0: i2c eeprom 80: 79 00 73 00 74 00 65 00 6d 00 73 00 20 00 47 00
May 31 17:16:35 d430 kernel: [ 4993.689101] em28xx #0: i2c eeprom 90: 6d 00 62 00 48 00 00 00 2a 03 50 00 43 00 54 00
May 31 17:16:35 d430 kernel: [ 4993.689125] em28xx #0: i2c eeprom a0: 56 00 20 00 55 00 53 00 42 00 32 00 20 00 50 00
May 31 17:16:35 d430 kernel: [ 4993.689148] em28xx #0: i2c eeprom b0: 41 00 4c 00 2f 00 53 00 45 00 43 00 41 00 4d 00
May 31 17:16:35 d430 kernel: [ 4993.689172] em28xx #0: i2c eeprom c0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
May 31 17:16:35 d430 kernel: [ 4993.689195] em28xx #0: i2c eeprom d0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
May 31 17:16:35 d430 kernel: [ 4993.689219] em28xx #0: i2c eeprom e0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
May 31 17:16:35 d430 kernel: [ 4993.689242] em28xx #0: i2c eeprom f0: 00 00 00 00 00 00 00 00 0c 22 17 56 03 27 37 2c
May 31 17:16:35 d430 kernel: [ 4993.689269] em28xx #0: EEPROM ID= 0x9567eb1a, EEPROM hash = 0x50680af4
May 31 17:16:35 d430 kernel: [ 4993.689273] em28xx #0: EEPROM info:
May 31 17:16:35 d430 kernel: [ 4993.689277] em28xx #0:    AC97 audio (5 sample rates)
May 31 17:16:35 d430 kernel: [ 4993.689282] em28xx #0:    500mA max power
May 31 17:16:35 d430 kernel: [ 4993.689287] em28xx #0:    Table at 0x06, strings=0x2a98, 0x2e6a, 0x0000
May 31 17:16:35 d430 kernel: [ 4993.690398] em28xx #0: Identified as Pinnacle PCTV USB 2 (card=3)
May 31 17:16:35 d430 kernel: [ 4993.708274] input: i2c IR (i2c IR (EM28XX Pinnacle as /devices/virtual/input/input13
May 31 17:16:35 d430 kernel: [ 4993.708541] ir-kbd-i2c: i2c IR (i2c IR (EM28XX Pinnacle detected at i2c-5/5-0047/ir0 [em28xx #0]
May 31 17:16:35 d430 kernel: [ 4993.709220] i2c IR (i2c IR (EM28XX Pinnacle: unknown key: key=0x00 raw=0x00 down=1
May 31 17:16:36 d430 kernel: [ 4994.333106] saa7115 5-0025: saa7113 found (1f7113d0e100000) @ 0x4a (em28xx #0)
May 31 17:16:37 d430 kernel: [ 4995.721459] tuner 5-0043: chip found @ 0x86 (em28xx #0)
May 31 17:16:37 d430 kernel: [ 4995.740098] tda9887 5-0043: creating new instance
May 31 17:16:37 d430 kernel: [ 4995.740106] tda9887 5-0043: tda988[5/6/7] found
May 31 17:16:37 d430 kernel: [ 4995.766376] tuner 5-0063: chip found @ 0xc6 (em28xx #0)
May 31 17:16:37 d430 kernel: [ 4995.792251] tuner-simple 5-0063: creating new instance
May 31 17:16:37 d430 kernel: [ 4995.792261] tuner-simple 5-0063: type set to 37 (LG PAL (newer TAPC series))
May 31 17:16:37 d430 kernel: [ 4995.872748] em28xx #0: Config register raw data: 0x10
May 31 17:16:37 d430 kernel: [ 4995.913566] em28xx #0: AC97 vendor ID = 0xffffffff
May 31 17:16:37 d430 kernel: [ 4995.931607] em28xx #0: AC97 features = 0x6a90
May 31 17:16:37 d430 kernel: [ 4995.931615] em28xx #0: Empia 202 AC97 audio processor detected
May 31 17:16:38 d430 kernel: [ 4996.690087] em28xx #0: v4l2 driver version 0.1.2
May 31 17:16:39 d430 kernel: [ 4998.080350] em28xx #0: V4L2 video device registered as /dev/video0
May 31 17:16:39 d430 kernel: [ 4998.114490] usbcore: registered new interface driver snd-usb-audio
May 31 17:16:39 d430 kernel: [ 4998.115712] usbcore: registered new interface driver em28xx
May 31 17:16:39 d430 kernel: [ 4998.115720] em28xx driver loaded
```
today, when I plug in the tuner it shows only:
```
Jun  2 19:06:49 d430 kernel: [ 3215.040170] usb 1-5: new high speed USB device using ehci_hcd and address 8
Jun  2 19:06:50 d430 kernel: [ 3215.208585] usb 1-5: configuration #1 chosen from 1 choice

```and the /dev/video* is not created

lsusb:
```
Bus 001 Device 008: ID 2304:0208 Pinnacle Systems, Inc. Studio PCTV USB2

```uname -a
```
Linux d430 2.6.32-22-generic #33-Ubuntu SMP Wed Apr 28 13:28:05 UTC 2010 x86_64 GNU/Linux
```
thanks for any hint!

---

