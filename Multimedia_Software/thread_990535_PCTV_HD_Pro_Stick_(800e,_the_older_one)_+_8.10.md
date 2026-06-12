---
title: "PCTV HD Pro Stick (800e, the older one) + 8.10"
date: 2008-11-22
forum: Multimedia Software
---

### Post by slimjim8094 on 2008-11-22
I've got a PCTV HD Pro USB TV Tuner (ATSC and NTSC) and I can't get it to work for the life of me. Even though it's supposed to be supported! Gah.

To avoid any confusion, this is the older 800e version.
```
Bus 005 Device 006: ID 2304:0227 Pinnacle Systems, Inc. [hex] PCTV for Mac, HD Stick
```

It doesn't work in either Kaffeine or Mythtv.

There have been a number of threads hacking it working, but I can't work any of them out. I've tried downloading all kinds of firmware (based on a cue from my dmesg) but can't find the right one.

On trying to use the device:
```
[  152.663613] xc2028 0-0061: Error: firmware xc3028-v27.fw not found.                                                                     
[  153.161690] firmware: requesting xc3028-v27.fw                                                                                          
[  153.163561] xc2028 0-0061: Error: firmware xc3028-v27.fw not found.                                                                     
[  153.665829] firmware: requesting xc3028-v27.fw                                                                                          
[  153.667734] xc2028 0-0061: Error: firmware xc3028-v27.fw not found.                                                                     
[  154.169719] firmware: requesting xc3028-v27.fw                                                                                          
[  154.171830] xc2028 0-0061: Error: firmware xc3028-v27.fw not found.                                                                     
[  154.176874] firmware: requesting xc3028-v27.fw                                                                                          
[  154.178891] xc2028 0-0061: Error: firmware xc3028-v27.fw not found.                                                                     
[  154.677731] firmware: requesting xc3028-v27.fw                                
``` 

I can't actually find the -v27 firmware, and the previous logs indicate that it might even be identifying it wrongly. Here's the whole driver-init:

```
[   14.346183] em28xx v4l2 driver version 0.1.0 loaded                                                                                     
[   14.346730] em28xx new video device (2304:0227): interface 0, class 255                                                                 
[   14.346738] em28xx Doesn't have usb audio class                                                                                         
[   14.346740] em28xx #0: Alternate settings: 8                                                                                            
[   14.346742] em28xx #0: Alternate setting 0, max size= 0                                                                                 
[   14.346744] em28xx #0: Alternate setting 1, max size= 0                                                                                 
[   14.346747] em28xx #0: Alternate setting 2, max size= 1448                                                                              
[   14.346749] em28xx #0: Alternate setting 3, max size= 2048                                                                              
[   14.346751] em28xx #0: Alternate setting 4, max size= 2304                                                                              
[   14.346754] em28xx #0: Alternate setting 5, max size= 2580                                                                              
[   14.346756] em28xx #0: Alternate setting 6, max size= 2892                                                                              
[   14.346758] em28xx #0: Alternate setting 7, max size= 3072                                                                              
[   14.346931] em28xx #0: chip ID is em2882/em2883                                                                                                                                    
[   14.535320] em28xx #0: i2c eeprom 00: 1a eb 67 95 04 23 27 02 d0 12 5c 03 8e 16 a4 1c                                                   
[   14.535333] em28xx #0: i2c eeprom 10: 6a 24 27 57 46 07 01 00 00 00 00 00 00 00 00 00                                                   
[   14.535344] em28xx #0: i2c eeprom 20: 46 00 01 00 f0 10 02 00 b8 00 00 00 5b 1c 00 00                                                   
[   14.535355] em28xx #0: i2c eeprom 30: 00 00 20 40 20 80 02 20 01 01 00 00 00 00 00 00                                                   
[   14.535366] em28xx #0: i2c eeprom 40: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00                                                   
[   14.535377] em28xx #0: i2c eeprom 50: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00                                                   
[   14.535387] em28xx #0: i2c eeprom 60: 00 00 00 00 00 00 00 00 00 00 24 03 50 00 69 00                                                   
[   14.535398] em28xx #0: i2c eeprom 70: 6e 00 6e 00 61 00 63 00 6c 00 65 00 20 00 53 00                                                   
[   14.535409] em28xx #0: i2c eeprom 80: 79 00 73 00 74 00 65 00 6d 00 73 00 00 00 16 03                                                   
[   14.535420] em28xx #0: i2c eeprom 90: 50 00 43 00 54 00 56 00 20 00 38 00 30 00 30 00                                                   
[   14.535430] em28xx #0: i2c eeprom a0: 65 00 00 00 1c 03 30 00 37 00 30 00 35 00 30 00                                                   
[   14.535441] em28xx #0: i2c eeprom b0: 31 00 39 00 39 00 36 00 34 00 35 00 31 00 00 00                                                   
[   14.535452] em28xx #0: i2c eeprom c0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00                                                   
[   14.535462] em28xx #0: i2c eeprom d0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00                                                   
[   14.535473] em28xx #0: i2c eeprom e0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00                                                   
[   14.535483] em28xx #0: i2c eeprom f0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00                                                   
[   14.535495] EEPROM ID= 0x9567eb1a, hash = 0x49e5adbf                                                                                    
[   14.535497] Vendor/Product ID= 2304:0227                                                                                                
[   14.535499] AC97 audio (5 sample rates)                                                                                                 
[   14.535500] 500mA max power                                                                                                             
[   14.535502] Table at 0x27, strings=0x168e, 0x1ca4, 0x246a                                                                               
[   14.550840] iTCO_wdt: Found a ICH7-M TCO device (Version=2, TCOBASE=0x1060)                                                             
[   14.550892] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)                                                                                                                         
[   14.739445] tuner' 0-0061: chip found @ 0xc2 (em28xx #0)                                                                                
[   14.793823] xc2028 0-0061: creating new instance                                                                                        
[   14.793827] xc2028 0-0061: type set to XCeive xc2028/xc3028 tuner                                                                       
[   14.793835] firmware: requesting xc3028-v27.fw                                                                                          
[   14.860526] xc2028 0-0061: Error: firmware xc3028-v27.fw not found.                                                                     
[   14.952583] tvp5150 0-005c: tvp5150am1 detected.                                                                                        
[   15.097321] em28xx #0: V4L2 device registered as /dev/video0 and /dev/vbi0                                                              
[   15.097328] em28xx #0: Found Pinnacle PCTV HD Pro Stick                                                                                 
[   15.097400] usbcore: registered new interface driver em28xx                                                                             
[   15.131445] em28xx-audio.c: probing for em28x1 non standard usbaudio                                                                    
[   15.131447] em28xx-audio.c: Copyright (C) 2006 Markus Rechberger                                                                        
[   15.131822] Em28xx: Initialized (Em28xx Audio Extension) extension                                                                      
[   15.282016] xc2028 0-0061: attaching existing instance                                                                                  
[   15.282020] xc2028 0-0061: type set to XCeive xc2028/xc3028 tuner                                                                       
[   15.282022] em28xx #0/2: xc3028 attached                                                                                                
[   15.282024] DVB: registering new adapter (em28xx #0)                                                                                    
[   15.282027] DVB: registering frontend 0 (LG Electronics LGDT3303 VSB/QAM Frontend)...                                                   
[   15.282374] Successfully loaded em28xx-dvb                                                                                              
[   15.282376] Em28xx: Initialized (Em28xx dvb Extension) extension 
```

If anybody can fix this, that's amazing. I've always liked Myth better, and with the discovery that CS:S works, I'm about to make the switch full-time. Thanks!

---

### Post by slimjim8094 on 2008-11-23
Never mind, I got it working. Turns out I was conflating the two em28xx'es. The one in Ubuntu (and the kernel) is the v4l version, but there's also a 'mcentral.de'.

I was following the wrong firmware instructions. And for anybody else with the same problem, the card is being detected correctly, but the firmware is common among them all.

I never did get kaffeine or dvbscan working, though myth works great. So... it works

---

### Post by 8200 on 2008-12-27
Hi slimjim

I think I have got an similar issue with my terratec cinergy T dvb-t stick.

I have already used it with an upgraded ubuntu 8.04 --> ubuntu 8.10 just buy copying the missing firmware (xc3028-v27.fw) to /lib/firmware.

But now with the fresh install of ubuntu 8.10 I only get an /dev/video0 device and no /dev/dvb.

But I just want to use dvb-t.

Here is my dmesg when plugging the dvb-t stick in:
```
[  252.904065] usb 5-1: new high speed USB device using ehci_hcd and address 3
[  253.045359] usb 5-1: configuration #1 chosen from 1 choice
[  253.047745] em28xx new video device (0ccd:0043): interface 0, class 255
[  253.047759] em28xx Doesn't have usb audio class
[  253.047762] em28xx #0: Alternate settings: 8
[  253.047766] em28xx #0: Alternate setting 0, max size= 0
[  253.047769] em28xx #0: Alternate setting 1, max size= 0
[  253.047773] em28xx #0: Alternate setting 2, max size= 1448
[  253.047776] em28xx #0: Alternate setting 3, max size= 2048
[  253.047780] em28xx #0: Alternate setting 4, max size= 2304
[  253.047783] em28xx #0: Alternate setting 5, max size= 2580
[  253.047786] em28xx #0: Alternate setting 6, max size= 2892
[  253.047789] em28xx #0: Alternate setting 7, max size= 3072
[  253.060471] em28xx #0: em28xx chip ID = 35
[  253.565407] Chip ID is not zero. It is not a TEA5767
[  253.565538] tuner' 0-0060: chip found @ 0xc0 (em28xx #0)
[  253.610157] em28xx #0: i2c eeprom 00: 1a eb 67 95 cd 0c 43 00 c0 12 81 00 6a 24 8e 34
[  253.610181] em28xx #0: i2c eeprom 10: 00 00 06 57 02 0c 00 00 00 00 00 00 00 00 00 00
[  253.610199] em28xx #0: i2c eeprom 20: 44 00 00 00 f0 10 01 00 00 00 00 00 5b 00 00 00
[  253.610216] em28xx #0: i2c eeprom 30: 00 00 20 40 20 80 02 20 01 01 00 00 10 92 c6 49
[  253.610233] em28xx #0: i2c eeprom 40: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
[  253.610250] em28xx #0: i2c eeprom 50: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
[  253.610267] em28xx #0: i2c eeprom 60: 00 00 00 00 00 00 00 00 00 00 24 03 43 00 69 00
[  253.610284] em28xx #0: i2c eeprom 70: 6e 00 65 00 72 00 67 00 79 00 20 00 54 00 20 00
[  253.610301] em28xx #0: i2c eeprom 80: 55 00 53 00 42 00 20 00 58 00 53 00 00 00 34 03
[  253.610318] em28xx #0: i2c eeprom 90: 54 00 65 00 72 00 72 00 61 00 54 00 65 00 63 00
[  253.610335] em28xx #0: i2c eeprom a0: 20 00 45 00 6c 00 65 00 63 00 74 00 72 00 6f 00
[  253.610352] em28xx #0: i2c eeprom b0: 6e 00 69 00 63 00 20 00 47 00 6d 00 62 00 48 00
[  253.610369] em28xx #0: i2c eeprom c0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
[  253.610386] em28xx #0: i2c eeprom d0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
[  253.610403] em28xx #0: i2c eeprom e0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
[  253.610420] em28xx #0: i2c eeprom f0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
[  253.610439] EEPROM ID= 0x9567eb1a, hash = 0x9c79e4df
[  253.610442] Vendor/Product ID= 0ccd:0043
[  253.610445] No audio on board.
[  253.610447] 500mA max power
[  253.610450] Table at 0x06, strings=0x246a, 0x348e, 0x0000
[  253.610454] em28xx #0: 
[  253.610455] 
[  253.610459] em28xx #0: The support for this board weren't valid yet.
[  253.610463] em28xx #0: Please send a report of having this working
[  253.610466] em28xx #0: not to V4L mailing list (and/or to other addresses)
[  253.610468] 
[  253.644818] xc2028 0-0060: creating new instance
[  253.644828] xc2028 0-0060: type set to XCeive xc2028/xc3028 tuner
[  253.644840] firmware: requesting xc3028-v27.fw
[  253.649667] xc2028 0-0060: Loading 80 firmware images from xc3028-v27.fw, type: xc2028 firmware, ver 2.7
[  253.772060] xc2028 0-0060: Loading firmware for type=BASE (1), id 0000000000000000.
[  266.276067] xc2028 0-0060: Loading firmware for type=(0), id 000000000000b700.
[  266.528025] SCODE (20000000), id 000000000000b700:
[  266.528032] xc2028 0-0060: Loading SCODE for type=MONO SCODE HAS_IF_4320 (60008000), id 0000000000008000.
[  266.620710] xc2028 0-0060: Incorrect readback of firmware version.
[  266.796058] xc2028 0-0060: Loading firmware for type=BASE (1), id 0000000000000000.
[  279.296074] xc2028 0-0060: Loading firmware for type=(0), id 000000000000b700.
[  279.548064] SCODE (20000000), id 000000000000b700:
[  279.548076] xc2028 0-0060: Loading SCODE for type=MONO SCODE HAS_IF_4320 (60008000), id 0000000000008000.
[  279.640639] xc2028 0-0060: Incorrect readback of firmware version.
[  280.356136] em28xx #0: V4L2 device registered as /dev/video0 and /dev/vbi0
[  280.356147] em28xx-audio.c: probing for em28x1 non standard usbaudio
[  280.356151] em28xx-audio.c: Copyright (C) 2006 Markus Rechberger
[  280.356871] em28xx #0: Found Terratec Cinergy T XS

```


Thank you!

Regards
Arthur

---

### Post by slimjim8094 on 2009-01-31
I'm by no means an expert on this; the problem I had was strictly a firmware issue (using the wrong one, etc)
I'm concerned by this: > [  266.620710] xc2028 0-0060: Incorrect readback of firmware version.

do you get a bunch of i2c_core errors? In that case, you might have the wrong xc3028-v27.fw

Otherwise, I don't know. I wasn't ever able to get my card to work in ANYTHING (Kaffeine, the various dump-to-mpg included commands...) but only in MythTV. Go figure. My point is, it could be working...

I hope this is at least somewhat useful...

---

