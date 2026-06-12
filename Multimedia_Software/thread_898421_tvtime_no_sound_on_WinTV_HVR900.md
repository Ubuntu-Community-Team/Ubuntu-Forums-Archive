---
title: "tvtime no sound on WinTV HVR900"
date: 2008-08-23
forum: Multimedia Software
---

### Post by tech_cheetah on 2008-08-23
I am using WinTV HVR900 through USB to watch TV on my laptop. I have been able to install drivers for the same using information on this[http://www.2nrds.com/digital-tv-in-linux-with-em28xx-devices]("http://www.2nrds.com/digital-tv-in-linux-with-em28xx-devices") site. Video is coming properly but there is no sound. Right arrow key brings up the volume control, but doesn't increase any volume and volume remains 0.
This is the output of dmesg command :
> [   44.417809] Loading default analogue TV settings: xc3028_BG_PAL_A2_A.i2c.fw
[   44.476934] xc3028-tuner.c: firmware 2.7
[   44.476939] ANALOG TV REQUEST
[   44.482177] em28xx #0: V4L2 VBI device registered as /dev/vbi0
[   44.484018] em28xx #0: V4L2 device registered as /dev/video0
[   44.484021] em28xx #0: Found Hauppauge WinTV HVR Rev. 1.2
[   44.484043] usbcore: registered new interface driver em28xx
[   44.499460] em28xx_audio: no version for "snd_pcm_new" found: kernel tainted.
[   44.526236] em28xx-audio.c: probing for em28x1 non standard usbaudio
[   44.526239] em28xx-audio.c: Copyright (C) 2006 Markus Rechberger
[   44.526317] BUG: unable to handle kernel paging request at virtual address 38326d65
[   44.526321] printing eip: f8ba7743 *pde = 00000000 
[   44.526326] Oops: 0000 [#1] SMP 


---

### Post by tech_cheetah on 2008-08-24
Can anybody plz help me ??

---

### Post by tech_cheetah on 2008-08-27
anybody .. hello there ..   :(

---

### Post by waspbloke on 2008-09-05
Hi there,

this bug might be something to do with your problem:

[https://bugs.launchpad.net/ubuntu/+bug/204578](https://bugs.launchpad.net/ubuntu/+bug/204578)

I have yet to try getting my HVR900 running although I'm glad I found your post as I would have missed an entire step out (the actual v4l drivers - doh!). I am a complete n00b at this so I anticipate much hair being pulled out!

Anyhoo...that bug has a fix if your read through the comments by MarkusRechberger.

Hope it helps!

---

### Post by tech_cheetah on 2008-09-05
I have post my query on the same. Lets see if the developer can help me.

---

### Post by Crafty Kisses on 2008-09-05
Post results of > lspci

---

### Post by tech_cheetah on 2008-09-05
After hell lot of effotrs, dmesg now doesn't seem to show errors, but still no sound in tvtime. Volume remains at 0 :-(

> [ 1401.167216] em28xx v4l2 driver version 0.1.0 loaded
[ 1401.167471] em28xx new video device (2040:6502): interface 0, class 255
[ 1401.167480] em28xx Doesn't have usb audio class
[ 1401.167484] em28xx #0: Alternate settings: 8
[ 1401.167487] em28xx #0: Alternate setting 0, max size= 0
[ 1401.167490] em28xx #0: Alternate setting 1, max size= 0
[ 1401.167494] em28xx #0: Alternate setting 2, max size= 1448
[ 1401.167497] em28xx #0: Alternate setting 3, max size= 2048
[ 1401.167501] em28xx #0: Alternate setting 4, max size= 2304
[ 1401.167504] em28xx #0: Alternate setting 5, max size= 2580
[ 1401.167507] em28xx #0: Alternate setting 6, max size= 2892
[ 1401.167511] em28xx #0: Alternate setting 7, max size= 3072
[ 1401.169185] em28xx #0: chip ID is em2882/em2883
[ 1401.216924] em28xx #0: i2c eeprom 00: 1a eb 67 95 40 20 02 65 d0 12 5c 03 82 1e 6a 18
[ 1401.216945] em28xx #0: i2c eeprom 10: 00 00 24 57 66 07 01 00 00 00 00 00 00 00 00 00
[ 1401.216962] em28xx #0: i2c eeprom 20: 46 00 01 00 f0 10 02 00 b8 00 00 00 5b e0 00 00
[ 1401.216976] em28xx #0: i2c eeprom 30: 00 00 20 40 20 6e 02 20 10 01 01 01 00 00 00 00
[ 1401.216995] em28xx #0: i2c eeprom 40: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
[ 1401.217014] em28xx #0: i2c eeprom 50: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
[ 1401.217032] em28xx #0: i2c eeprom 60: 00 00 00 00 00 00 00 00 00 00 18 03 34 00 30 00
[ 1401.217050] em28xx #0: i2c eeprom 70: 32 00 37 00 32 00 34 00 32 00 36 00 38 00 36 00
[ 1401.217068] em28xx #0: i2c eeprom 80: 00 00 1e 03 57 00 69 00 6e 00 54 00 56 00 20 00
[ 1401.217087] em28xx #0: i2c eeprom 90: 48 00 56 00 52 00 2d 00 39 00 30 00 30 00 00 00
[ 1401.217104] em28xx #0: i2c eeprom a0: 84 12 00 00 05 50 1a 7f d4 78 23 fa fd d0 28 89
[ 1401.217123] em28xx #0: i2c eeprom b0: ff 00 00 00 04 84 0a 00 01 01 20 77 00 40 be d8
[ 1401.217141] em28xx #0: i2c eeprom c0: 0a f0 74 02 01 00 01 79 aa 00 00 00 00 00 00 00
[ 1401.217160] em28xx #0: i2c eeprom d0: 84 12 00 00 05 50 1a 7f d4 78 23 fa fd d0 28 89
[ 1401.217179] em28xx #0: i2c eeprom e0: ff 00 00 00 04 84 0a 00 01 01 20 77 00 40 be d8
[ 1401.217197] em28xx #0: i2c eeprom f0: 0a f0 74 02 01 00 01 79 aa 00 00 00 00 00 00 00
[ 1401.322121] tuner' 3-0061: chip found @ 0xc2 (em28xx #0)
[ 1402.022612] em28xx #0: V4L2 device registered as /dev/video0 and /dev/vbi0
[ 1402.022624] em28xx #0: Found Hauppauge WinTV HVR 900 (R2)
[ 1402.022674] usbcore: registered new interface driver em28xx

Here is lspci output
> --kernel-name="2.6.24-19-generic" --kernel-source=/usr/src/linux-source-2.6.24
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:01.0 PCI bridge: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: nVidia Corporation GeForce 8400M GS (rev a1)
05:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8039 PCI-E Fast Ethernet Controller (rev 14)
07:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
08:09.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
08:09.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
08:09.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
08:09.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
08:09.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)

---

### Post by jacobcolbert on 2008-09-05
Hey, I have the same problem with my HVR-950 with the em28xx drivers. You follow the directions there to make it no longer error? It no longer gives me that error, but still doesn't work. And reboot sometimes freezes if the device is plugged in, though it works when plugged in.

---

### Post by tech_cheetah on 2009-05-02
Ubuntu has updated 2 (8.10 and 9.04) times but this problem is still unresolved. My HVR 900 tv tuner stick still doesn't work in ubuntu.
I don't understand why inspite of so many threads, developers don't fix the hardware issues on priority ?
If the OS doesn't support somebody's hardware, how can he happily adapt to it ?

---

### Post by SunnyRabbiera on 2009-05-02
> **tech_cheetah said:**
> Ubuntu has updated 2 (8.10 and 9.04) times but this problem is still unresolved. My HVR 900 tv tuner stick still doesn't work in ubuntu.
I don't understand why inspite of so many threads, developers don't fix the hardware issues on priority ?
If the OS doesn't support somebody's hardware, how can he happily adapt to it ?

This is no fault of linux developers, the real blame goes to the manufacturers who think about windows and only windows.
Linux is not owned by a bazillion dollar company that can pay off developers to work with just it, instead most linuxes are community supported.
The developers can only do so much

---

### Post by clawed on 2010-03-01
There is a script for getting sound working with tvtime:

[http://www.mail-archive.com/em28xx@mcentral.de/msg00840.html](http://www.mail-archive.com/em28xx@mcentral.de/msg00840.html)

```
#!/bin/bash

channel=0
if [ $# == 1 ] ; then
  channel=1
fi

tvtime -d /dev/video$channel &
sleep 1
arecord -D hw:1,0 -r 32000 -c 2 -f S16_LE | aplay
```

---

### Post by markackerman8@gmail.com on 2010-03-22
I have a hvr950Q and just found that it loaded the drivers out of the box! (Not in OpenSuse!, lots of troubles), anyway a solution for sound in TVtime is to run it with this command:

# tvtime | arecord -D hw:1,0 -r 32000 -c 2 -f S16_LE | aplay -

but there is an annoying delay.  If anyone can suggest a different fix, please tell me.??????:D

---

