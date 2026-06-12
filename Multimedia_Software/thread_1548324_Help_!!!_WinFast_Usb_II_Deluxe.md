---
title: "Help !!! WinFast Usb II Deluxe"
date: 2010-08-08
forum: Multimedia Software
---

### Post by freestuf69 on 2010-08-08
Hi all, I tried to make it work tv tuner but without success, posting listings below to lsusb, dmesg. It seems that the driver is loaded but tvtime says no signal.
If anyone has an idea how to go further.

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
Bus 002 Device 005: ID 0413:6023 Leadtek Research, Inc. EMP Audio Device
Bus 002 Device 004: ID 064e:a103 Suyin Corp. 
Bus 002 Device 003: ID 0409:0058 NEC Corp. HighSpeed Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

dmesg | grep em28xx:
```
[   19.226127] em28xx: New device Leadtek WinFast TV USB II Deluxe @ 480 Mbps (0413:6023, interface 0, class 0)
[   19.227890] em28xx #0: chip ID is em2820 (or em2710)
[   19.496063] em28xx #0: board has no eeprom
[   19.572022] em28xx #0: preparing read at i2c address 0x60 failed (error=-19)
[   19.644029] em28xx #0: Identified as Leadtek Winfast USB II (card=7)
[   20.589229] em28xx #0: Config register raw data: 0x14
[   20.613240] em28xx #0: AC97 vendor ID = 0xffffffff
[   20.624112] em28xx #0: AC97 features = 0x6a90
[   20.624114] em28xx #0: Empia 202 AC97 audio processor detected
[   21.048113] em28xx #0: v4l2 driver version 0.1.2
[   21.964139] em28xx #0: V4L2 video device registered as /dev/video1
[   21.964159] em28xx audio device (0413:6023): interface 1, class 1
[   21.964172] em28xx audio device (0413:6023): interface 2, class 1
[   21.964196] usbcore: registered new interface driver em28xx
[   21.964199] em28xx driver loaded

```

Thank you to everyone, I am new to this wonderful operating system.

---

