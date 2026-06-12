---
title: "em28xx/xc3028, kernel 3.0 and Terratec Cinergy T XS"
date: 2012-01-20
forum: Multimedia Software
---

### Post by jubantu on 2012-01-20
Hi there,

I'm using Ubuntu 11.10 with kernel 3.0.0-15 and I was trying to get my Terratec Cinergy T XS DVB-T USB-Stick up and running. I read everywhere that this card should work out of the box, see [here]("http://linux.terratec.de/tv_en.html").

I tried everything I could find via google but I had no luck. I even compiled and installed v4l-dvb from source etc... The card is being recognized but I never get the dvb device creation.

Does anyone have some suggestions how to make this work?

lsusb:
```
Bus 002 Device 008: ID 0ccd:0043 TerraTec Electronic GmbH Cinergy T XS
```

dmesg:
```
[11657.208290] usb 2-1.2: USB disconnect, device number 7
[11657.208405] em28xx #1: disconnecting em28xx #1 video
[11657.208415] em28xx #1: V4L2 device video2 deregistered
[11657.208664] xc2028 18-0061: destroying instance
[11660.031592] usb 2-1.2: new high speed USB device number 8 using ehci_hcd
[11660.131859] em28xx: New device TerraTec Electronic GmbH Cinergy T USB XS @ 480 Mbps (0ccd:0043, interface 0, class 0)
[11660.131869] em28xx: Video interface 0 found
[11660.131874] em28xx: DVB interface 0 found
[11660.132005] em28xx #1: chip ID is em2870
[11660.262622] em28xx #1: i2c eeprom 00: 1a eb 67 95 cd 0c 43 00 c0 12 5c 00 9e 24 6a 34
[11660.262645] em28xx #1: i2c eeprom 10: 00 00 06 57 02 0c 00 00 00 00 00 00 00 00 00 00
[11660.262664] em28xx #1: i2c eeprom 20: 44 00 00 00 f0 10 01 00 00 00 00 00 5b 00 00 00
[11660.262681] em28xx #1: i2c eeprom 30: 00 00 20 40 20 80 02 20 01 01 00 00 00 00 00 00
[11660.262700] em28xx #1: i2c eeprom 40: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
[11660.262717] em28xx #1: i2c eeprom 50: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
[11660.262735] em28xx #1: i2c eeprom 60: 00 00 00 00 00 00 00 00 00 00 34 03 54 00 65 00
[11660.262752] em28xx #1: i2c eeprom 70: 72 00 72 00 61 00 54 00 65 00 63 00 20 00 45 00
[11660.262770] em28xx #1: i2c eeprom 80: 6c 00 65 00 63 00 74 00 72 00 6f 00 6e 00 69 00
[11660.262788] em28xx #1: i2c eeprom 90: 63 00 20 00 47 00 6d 00 62 00 48 00 00 00 24 03
[11660.262806] em28xx #1: i2c eeprom a0: 43 00 69 00 6e 00 65 00 72 00 67 00 79 00 20 00
[11660.262824] em28xx #1: i2c eeprom b0: 54 00 20 00 55 00 53 00 42 00 20 00 58 00 53 00
[11660.262842] em28xx #1: i2c eeprom c0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
[11660.262859] em28xx #1: i2c eeprom d0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
[11660.262877] em28xx #1: i2c eeprom e0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
[11660.262894] em28xx #1: i2c eeprom f0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
[11660.262915] em28xx #1: EEPROM ID= 0x9567eb1a, EEPROM hash = 0xbfdf1b96
[11660.262919] em28xx #1: EEPROM info:
[11660.262922] em28xx #1:	No audio on board.
[11660.262925] em28xx #1:	500mA max power
[11660.262930] em28xx #1:	Table at 0x06, strings=0x249e, 0x346a, 0x0000
[11660.264080] em28xx #1: Identified as Terratec Cinergy T XS (card=43)
[11660.264088] em28xx #1: 
[11660.264090] 
[11660.264094] em28xx #1: The support for this board weren't valid yet.
[11660.264098] em28xx #1: Please send a report of having this working
[11660.264102] em28xx #1: not to V4L mailing list (and/or to other addresses)
[11660.264105] 
[11660.269281] tuner 18-0061: Tuner -1 found with type(s) Radio TV.
[11660.269309] xc2028 18-0061: creating new instance
[11660.269317] xc2028 18-0061: type set to XCeive xc2028/xc3028 tuner
[11660.273505] xc2028 18-0061: Loading 80 firmware images from xc3028-v27.fw, type: xc2028 firmware, ver 2.7
[11660.319392] xc2028 18-0061: Loading firmware for type=BASE (1), id 0000000000000000.
[11661.055631] [UFW BLOCK] IN=wlan0 OUT= MAC=8c:a9:82:af:1c:06:00:04:0e:f3:ad:25:08:00 SRC=192.168.178.1 DST=192.168.178.27 LEN=60 TOS=0x00 PREC=0x00 TTL=64 ID=45525 DF PROTO=TCP SPT=2727 DPT=14013 WINDOW=5840 RES=0x00 SYN URGP=0 
[11661.342740] xc2028 18-0061: Loading firmware for type=(0), id 000000000000b700.
[11661.358973] SCODE (20000000), id 000000000000b700:
[11661.358983] xc2028 18-0061: Loading SCODE for type=MONO SCODE HAS_IF_4320 (60008000), id 0000000000008000.
[11661.482834] em28xx #1: v4l2 driver version 0.1.3
[11661.530820] xc2028 18-0061: Loading firmware for type=BASE F8MHZ (3), id 0000000000000000.
[11662.554241] (0), id 00000000000000ff:
[11662.554251] xc2028 18-0061: Loading firmware for type=(0), id 0000000100000007.
[11662.570465] xc2028 18-0061: Loading SCODE for type=MONO SCODE HAS_IF_5320 (60008000), id 0000000f00000007.
[11662.699312] em28xx #1: V4L2 video device registered as video2

```

uname -a:
```
Linux 3.0.0-15-generic x86_64 x86_64 x86_64 GNU/Linux
```

---

### Post by vning on 2012-03-04
Hi,

I have the same trouble with em28xx/xc3028 but my USB key is DNT DA2 Hybrid (card=52) 

lsub gives :
Bus 002 Device 006: ID eb1a:2881 eMPIA Technology, Inc. EM2881 Video Controller

uname -a gives :
3.0.0-16-generic-pae #28-Ubuntu SMP Fri Jan 27 19:24:01 UTC 2012 i686 i686 i386 GNU/Linux

I have tested solution from this post : [https://wiki.edubuntu.org/em28xx](https://wiki.edubuntu.org/em28xx) but nothing more append when plugging USB key : no DVB-T device.

Also tested this post : [http://linuxtv.org/wiki/index.php/Xceive_XC3028/XC2028](http://linuxtv.org/wiki/index.php/Xceive_XC3028/XC2028), --> failed after compilation error ... 

Here is tail -f  /var/log/kernel.log :

```
Mar  4 14:25:42 vning-Precision-M6600 kernel: [ 8085.923027] usb 2-1.2: new high speed USB device number 8 using ehci_hcd
Mar  4 14:25:42 vning-Precision-M6600 kernel: [ 8086.019027] em28xx: New device USB 2881 Video @ 480 Mbps (eb1a:2881, interface 0, class 0)
Mar  4 14:25:42 vning-Precision-M6600 kernel: [ 8086.019182] em28xx #0: chip ID is em2882/em2883
Mar  4 14:25:42 vning-Precision-M6600 kernel: [ 8086.179482] em28xx #0: i2c eeprom 00: 1a eb 67 95 1a eb 81 28 58 12 5c 00 6a 20 6a 00
Mar  4 14:25:42 vning-Precision-M6600 kernel: [ 8086.179532] em28xx #0: i2c eeprom 10: 00 00 04 57 64 56 00 00 60 f4 00 00 02 02 00 00
Mar  4 14:25:42 vning-Precision-M6600 kernel: [ 8086.179555] em28xx #0: i2c eeprom 20: 56 00 01 00 00 00 01 00 b8 00 00 00 5b 1e 00 00
Mar  4 14:25:42 vning-Precision-M6600 kernel: [ 8086.179576] em28xx #0: i2c eeprom 30: 00 00 20 40 20 80 02 20 10 02 00 00 00 00 00 00
Mar  4 14:25:42 vning-Precision-M6600 kernel: [ 8086.179598] em28xx #0: i2c eeprom 40: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
Mar  4 14:25:42 vning-Precision-M6600 kernel: [ 8086.179619] em28xx #0: i2c eeprom 50: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
Mar  4 14:25:42 vning-Precision-M6600 kernel: [ 8086.179639] em28xx #0: i2c eeprom 60: 00 00 00 00 00 00 00 00 00 00 20 03 55 00 53 00
Mar  4 14:25:42 vning-Precision-M6600 kernel: [ 8086.179660] em28xx #0: i2c eeprom 70: 42 00 20 00 32 00 38 00 38 00 31 00 20 00 56 00
Mar  4 14:25:42 vning-Precision-M6600 kernel: [ 8086.179682] em28xx #0: i2c eeprom 80: 69 00 64 00 65 00 6f 00 00 00 00 00 00 00 00 00
Mar  4 14:25:42 vning-Precision-M6600 kernel: [ 8086.179703] em28xx #0: i2c eeprom 90: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
Mar  4 14:25:42 vning-Precision-M6600 kernel: [ 8086.179724] em28xx #0: i2c eeprom a0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
Mar  4 14:25:42 vning-Precision-M6600 kernel: [ 8086.179744] em28xx #0: i2c eeprom b0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
Mar  4 14:25:42 vning-Precision-M6600 kernel: [ 8086.179765] em28xx #0: i2c eeprom c0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
Mar  4 14:25:42 vning-Precision-M6600 kernel: [ 8086.179786] em28xx #0: i2c eeprom d0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
Mar  4 14:25:42 vning-Precision-M6600 kernel: [ 8086.179807] em28xx #0: i2c eeprom e0: 5a 00 55 aa 1f 76 52 03 00 17 08 01 00 00 00 00
Mar  4 14:25:42 vning-Precision-M6600 kernel: [ 8086.179828] em28xx #0: i2c eeprom f0: 0a 00 00 01 00 00 00 00 00 00 00 00 00 00 00 00
Mar  4 14:25:42 vning-Precision-M6600 kernel: [ 8086.179854] em28xx #0: EEPROM ID= 0x9567eb1a, EEPROM hash = 0x22a0fe20
Mar  4 14:25:42 vning-Precision-M6600 kernel: [ 8086.179858] em28xx #0: EEPROM info:
Mar  4 14:25:42 vning-Precision-M6600 kernel: [ 8086.179862] em28xx #0:    AC97 audio (5 sample rates)
Mar  4 14:25:42 vning-Precision-M6600 kernel: [ 8086.179865] em28xx #0:    USB Remote wakeup capable
Mar  4 14:25:42 vning-Precision-M6600 kernel: [ 8086.179869] em28xx #0:    500mA max power
Mar  4 14:25:42 vning-Precision-M6600 kernel: [ 8086.179874] em28xx #0:    Table at 0x04, strings=0x206a, 0x006a, 0x0000
Mar  4 14:25:42 vning-Precision-M6600 kernel: [ 8086.180958] em28xx #0: Identified as DNT DA2 Hybrid (card=52)
Mar  4 14:25:42 vning-Precision-M6600 kernel: [ 8086.180962] em28xx #0: 
Mar  4 14:25:42 vning-Precision-M6600 kernel: [ 8086.180964] 
Mar  4 14:25:42 vning-Precision-M6600 kernel: [ 8086.180968] em28xx #0: The support for this board weren't valid yet.
Mar  4 14:25:42 vning-Precision-M6600 kernel: [ 8086.180973] em28xx #0: Please send a report of having this working
Mar  4 14:25:42 vning-Precision-M6600 kernel: [ 8086.180977] em28xx #0: not to V4L mailing list (and/or to other addresses)
Mar  4 14:25:42 vning-Precision-M6600 kernel: [ 8086.180979] 
Mar  4 14:25:42 vning-Precision-M6600 kernel: [ 8086.184427] tvp5150 0-005c: chip found @ 0xb8 (em28xx #0)
Mar  4 14:25:42 vning-Precision-M6600 kernel: [ 8086.251094] tvp5150 0-005c: tvp5150am1 detected.
Mar  4 14:25:42 vning-Precision-M6600 kernel: [ 8086.258084] tuner 0-0061: Tuner -1 found with type(s) Radio TV.
Mar  4 14:25:42 vning-Precision-M6600 kernel: [ 8086.258119] xc2028 0-0061: creating new instance
Mar  4 14:25:42 vning-Precision-M6600 kernel: [ 8086.258123] xc2028 0-0061: type set to XCeive xc2028/xc3028 tuner
Mar  4 14:25:42 vning-Precision-M6600 kernel: [ 8086.261636] xc2028 0-0061: Loading 80 firmware images from xc3028-v27.fw, type: xc2028 firmware, ver 2.7
Mar  4 14:25:42 vning-Precision-M6600 kernel: [ 8086.306266] xc2028 0-0061: Loading firmware for type=BASE (1), id 0000000000000000.
Mar  4 14:25:43 vning-Precision-M6600 kernel: [ 8087.215653] xc2028 0-0061: Loading firmware for type=(0), id 000000000000b700.
Mar  4 14:25:43 vning-Precision-M6600 kernel: [ 8087.229845] SCODE (20000000), id 000000000000b700:
Mar  4 14:25:43 vning-Precision-M6600 kernel: [ 8087.229864] xc2028 0-0061: Loading SCODE for type=MONO SCODE HAS_IF_4320 (60008000), id 0000000000008000.
Mar  4 14:25:43 vning-Precision-M6600 kernel: [ 8087.353138] em28xx #0: Config register raw data: 0x58
Mar  4 14:25:43 vning-Precision-M6600 kernel: [ 8087.353988] em28xx #0: AC97 vendor ID = 0xffffffff
Mar  4 14:25:43 vning-Precision-M6600 kernel: [ 8087.354362] em28xx #0: AC97 features = 0x6a90
Mar  4 14:25:43 vning-Precision-M6600 kernel: [ 8087.354369] em28xx #0: Empia 202 AC97 audio processor detected
Mar  4 14:25:43 vning-Precision-M6600 kernel: [ 8087.497651] em28xx #0: v4l2 driver version 0.1.2
Mar  4 14:25:43 vning-Precision-M6600 kernel: [ 8087.544690] xc2028 0-0061: Loading firmware for type=BASE F8MHZ (3), id 0000000000000000.
Mar  4 14:25:44 vning-Precision-M6600 kernel: [ 8088.449684] (0), id 00000000000000ff:
Mar  4 14:25:44 vning-Precision-M6600 kernel: [ 8088.449694] xc2028 0-0061: Loading firmware for type=(0), id 0000000100000007.
Mar  4 14:25:44 vning-Precision-M6600 kernel: [ 8088.463618] xc2028 0-0061: Loading SCODE for type=MONO SCODE HAS_IF_5320 (60008000), id 0000000f00000007.
Mar  4 14:25:44 vning-Precision-M6600 kernel: [ 8088.658693] em28xx #0: V4L2 video device registered as video0
Mar  4 14:25:44 vning-Precision-M6600 kernel: [ 8088.658701] em28xx #0: V4L2 VBI device registered as vbi0
Mar  4 14:25:44 vning-Precision-M6600 kernel: [ 8088.659384] em28xx audio device (eb1a:2881): interface 1, class 1
```

any idea or suggestion ?

Thanks

---

### Post by vning on 2012-03-04
after adding in /etc/modules :
```
em28xx
em28xx-dvb
em28xx-audio
```
then reboot, dmesg gives :

```
[   61.747934] usb 2-1.2: new high speed USB device number 5 using ehci_hcd
[   61.840677] em28xx: New device @ 480 Mbps (eb1a:2881, interface 0, class 0)
[   61.840763] em28xx #0: chip ID is em2882/em2883
[   61.999844] em28xx #0: i2c eeprom 00: 1a eb 67 95 1a eb 81 28 58 12 5c 00 6a 20 6a 00
[   61.999870] em28xx #0: i2c eeprom 10: 00 00 04 57 64 56 00 00 60 f4 00 00 02 02 00 00
[   61.999893] em28xx #0: i2c eeprom 20: 56 00 01 00 00 00 01 00 b8 00 00 00 5b 1e 00 00
[   61.999908] em28xx #0: i2c eeprom 30: 00 00 20 40 20 80 02 20 10 02 00 00 00 00 00 00
[   61.999913] em28xx #0: i2c eeprom 40: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
[   61.999919] em28xx #0: i2c eeprom 50: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
[   61.999924] em28xx #0: i2c eeprom 60: 00 00 00 00 00 00 00 00 00 00 20 03 55 00 53 00
[   61.999929] em28xx #0: i2c eeprom 70: 42 00 20 00 32 00 38 00 38 00 31 00 20 00 56 00
[   61.999934] em28xx #0: i2c eeprom 80: 69 00 64 00 65 00 6f 00 00 00 00 00 00 00 00 00
[   61.999940] em28xx #0: i2c eeprom 90: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
[   61.999945] em28xx #0: i2c eeprom a0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
[   61.999950] em28xx #0: i2c eeprom b0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
[   61.999955] em28xx #0: i2c eeprom c0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
[   61.999961] em28xx #0: i2c eeprom d0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
[   61.999966] em28xx #0: i2c eeprom e0: 5a 00 55 aa 1f 76 52 03 00 17 08 01 00 00 00 00
[   61.999971] em28xx #0: i2c eeprom f0: 0a 00 00 01 00 00 00 00 00 00 00 00 00 00 00 00
[   61.999977] em28xx #0: EEPROM ID= 0x9567eb1a, EEPROM hash = 0x22a0fe20
[   61.999979] em28xx #0: EEPROM info:
[   61.999979] em28xx #0:    AC97 audio (5 sample rates)
[   61.999980] em28xx #0:    USB Remote wakeup capable
[   61.999981] em28xx #0:    500mA max power
[   61.999983] em28xx #0:    Table at 0x04, strings=0x206a, 0x006a, 0x0000
[   62.001038] em28xx #0: Identified as DNT DA2 Hybrid (card=52)
[   62.001046] em28xx #0: 
[   62.001047] 
[   62.001052] em28xx #0: The support for this board weren't valid yet.
[   62.001056] em28xx #0: Please send a report of having this working
[   62.001060] em28xx #0: not to V4L mailing list (and/or to other addresses)
[   62.001063] 
[   62.027645] tvp5150 0-005c: chip found @ 0xb8 (em28xx #0)
[   62.091749] tvp5150 0-005c: tvp5150am1 detected.
[   62.096479] i2c-core: driver [tuner] using legacy suspend method
[   62.096481] i2c-core: driver [tuner] using legacy resume method
[   62.098874] tuner 0-0061: Tuner -1 found with type(s) Radio TV.
[   62.135054] xc2028 0-0061: creating new instance
[   62.135057] xc2028 0-0061: type set to XCeive xc2028/xc3028 tuner
[   62.153719] xc2028 0-0061: Loading 80 firmware images from xc3028-v27.fw, type: xc2028 firmware, ver 2.7
[   62.198885] xc2028 0-0061: Loading firmware for type=BASE (1), id 0000000000000000.
[   63.096585] xc2028 0-0061: Loading firmware for type=(0), id 000000000000b700.
[   63.110344] SCODE (20000000), id 000000000000b700:
[   63.110359] xc2028 0-0061: Loading SCODE for type=MONO SCODE HAS_IF_4320 (60008000), id 0000000000008000.
[   63.233253] em28xx #0: Config register raw data: 0x10
[   63.234356] em28xx #0: AC97 vendor ID = 0xffffffff
[   63.234728] em28xx #0: AC97 features = 0x6a90
[   63.234735] em28xx #0: Empia 202 AC97 audio processor detected
[   63.377802] em28xx #0: v4l2 driver version 0.1.2
[   63.424732] xc2028 0-0061: Loading firmware for type=BASE F8MHZ (3), id 0000000000000000.
[   64.322490] (0), id 00000000000000ff:
[   64.322500] xc2028 0-0061: Loading firmware for type=(0), id 0000000100000007.
[   64.336377] xc2028 0-0061: Loading SCODE for type=MONO SCODE HAS_IF_5320 (60008000), id 0000000f00000007.
[   64.526014] em28xx #0: V4L2 video device registered as video0
[   64.526016] em28xx #0: V4L2 VBI device registered as vbi0
[   64.526018] em28xx_dvb: This device does not support the extension
[   64.526611] em28xx audio device (eb1a:2881): interface 1, class 1
[   64.526632] em28xx audio device (eb1a:2881): interface 2, class 1
[   64.588129] usbcore: registered new interface driver snd-usb-audio
```

maybe a bad driver ?

---

