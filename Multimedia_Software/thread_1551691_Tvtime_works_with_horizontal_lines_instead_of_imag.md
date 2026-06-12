---
title: "Tvtime works with horizontal lines instead of image"
date: 2010-08-12
forum: Multimedia Software
---

### Post by freestuf69 on 2010-08-12
Using WinFast USB II Deluxe TV tuner card, I managed to get him to partially work, select TV programs after tvtime-scanner ,sound is perfect , but no image . Appear only horizontal lines, i have no idea how to proceed further.:confused: 

lsusb:
```
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 002: ID 04d9:1203 Holtek Semiconductor, Inc. MC Industries Keyboard
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 0458:005c KYE Systems Corp. (Mouse Systems) Enhanced Laser Gaming Device
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 003: ID 0a5c:2151 Broadcom Corp. 
Bus 003 Device 002: ID 08ff:1600 AuthenTec, Inc. AES1600
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 006: ID 0413:6023 Leadtek Research, Inc. EMP Audio Device
Bus 002 Device 005: ID 064e:a103 Suyin Corp. 
Bus 002 Device 004: ID 152e:2507 LG (HLDS) 
Bus 002 Device 003: ID 0409:0058 NEC Corp. HighSpeed Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

dmesg | grep em28xx :
```
[   16.075312] em28xx: New device Leadtek WinFast TV USB II Deluxe @ 480 Mbps (0413:6023, interface 0, class 0)
[   16.075662] em28xx #0: chip ID is em2820 (or em2710)
[   16.283765] em28xx #0: i2c eeprom 00: 1a eb 67 95 13 04 23 60 14 00 1e 03 7c 34 6a 12
[   16.283777] em28xx #0: i2c eeprom 10: 00 00 06 57 00 00 00 00 30 3e b0 60 03 03 03 03
[   16.283787] em28xx #0: i2c eeprom 20: 1e 00 01 01 00 00 00 00 00 00 00 00 00 00 00 00
[   16.283797] em28xx #0: i2c eeprom 30: 00 00 20 40 20 80 02 20 01 01 00 00 00 00 00 00
[   16.283807] em28xx #0: i2c eeprom 40: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
[   16.283816] em28xx #0: i2c eeprom 50: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
[   16.283826] em28xx #0: i2c eeprom 60: 00 00 00 00 00 00 00 00 00 00 12 03 4c 00 65 00
[   16.283836] em28xx #0: i2c eeprom 70: 61 00 64 00 74 00 65 00 6b 00 00 00 34 03 57 00
[   16.283846] em28xx #0: i2c eeprom 80: 69 00 6e 00 46 00 61 00 73 00 74 00 20 00 54 00
[   16.283856] em28xx #0: i2c eeprom 90: 56 00 20 00 55 00 53 00 42 00 20 00 49 00 49 00
[   16.283866] em28xx #0: i2c eeprom a0: 20 00 44 00 65 00 6c 00 75 00 78 00 65 00 00 00
[   16.283876] em28xx #0: i2c eeprom b0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
[   16.283886] em28xx #0: i2c eeprom c0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
[   16.283895] em28xx #0: i2c eeprom d0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
[   16.283905] em28xx #0: i2c eeprom e0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
[   16.283915] em28xx #0: i2c eeprom f0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
[   16.283926] em28xx #0: EEPROM ID= 0x9567eb1a, EEPROM hash = 0xa21de2b2
[   16.283928] em28xx #0: EEPROM info:
[   16.283929] em28xx #0:	AC97 audio (5 sample rates)
[   16.283931] em28xx #0:	USB Self power capable
[   16.283932] em28xx #0:	500mA max power
[   16.283934] em28xx #0:	Table at 0x06, strings=0x347c, 0x126a, 0x0000
[   16.284773] em28xx #0: Identified as Leadtek Winfast USB II Deluxe (card=28)
[   16.284776] em28xx #0: 
[   16.285041] em28xx #0: The support for this board weren't valid yet.
[   16.285220] em28xx #0: Please send a report of having this working
[   16.285395] em28xx #0: not to V4L mailing list (and/or to other addresses)
[   16.664416] saa7115 0-0021: saa7114 found (1f7114d0e000000) @ 0x42 (em28xx #0)
[   19.357151] tuner 0-0043: chip found @ 0x86 (em28xx #0)
[   19.503443] tuner 0-0061: chip found @ 0xc2 (em28xx #0)
[   19.608153] em28xx #0: Config register raw data: 0x14
[   19.633153] em28xx #0: AC97 vendor ID = 0xffffffff
[   19.645279] em28xx #0: AC97 features = 0x6a90
[   19.645282] em28xx #0: Empia 202 AC97 audio processor detected
[   20.200045] em28xx #0: v4l2 driver version 0.1.2
[   21.033160] em28xx #0: V4L2 video device registered as /dev/video1
[   21.045078] em28xx audio device (0413:6023): interface 1, class 1
[   21.045090] em28xx audio device (0413:6023): interface 2, class 1
[   21.045128] usbcore: registered new interface driver em28xx
[   21.045131] em28xx driver loaded

```


Thank you for any little help.

---

