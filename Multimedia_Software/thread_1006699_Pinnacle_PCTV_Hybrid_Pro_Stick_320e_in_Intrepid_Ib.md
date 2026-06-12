---
title: "Pinnacle PCTV Hybrid Pro Stick 320e in Intrepid Ibex"
date: 2008-12-09
forum: Multimedia Software
---

### Post by marutinu on 2008-12-09
Hi everybody,

I have problem getting my Pinnacle PCTV Hybrid Pro Stick 320e working under Intrepid. 

I suppose the card is supported - I used it with Ubuntu 7.10, but now I can't get it working under 8.10. 

I have searched the forums and wiki, and even disassembled the casing of the card to peek at the chips inside, and here is what I have found:

1. 
My card uses the XCeive Tuner XC3028

2. 
I need the firmware xc3028-v27.fw - which I already have installed and copied into /lib/firmware

3. 
The card should work with the em28xx driver - which is installed.

4. 
The system can see the card, but it has no effect.

5. 
Under Kaffeine I have no DVB icon.
tvtime informs it cannot open the device /dev/video0 - althought i can see the /dev/video0 and /dev/vbi0 in the directory listing.
Klear says it cannot open DVB device.


Here is the output from lsusb (my card is eMPIA ID ev1a:2881):

Bus 002 Device 003: ID 046d:c501 Logitech, Inc. Cordless Mouse Receiver
Bus 002 Device 002: ID 046d:c517 Logitech, Inc. LX710 Cordless Desktop Laser
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
**Bus 001 Device 005: ID eb1a:2881 eMPIA Technology, Inc. **
Bus 001 Device 002: ID 148f:2573 Ralink Technology, Corp. RT2501USB Wireless Adapter
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

Here is the output form dmesg (the relevant part):


[   82.716051] usb 1-9: new high speed USB device using ehci_hcd and address 5
[   82.870750] usb 1-9: configuration #1 chosen from 1 choice
[B][   83.362770] usbcore: registered new interface driver snd-usb-audio
[   83.571317] Linux video capture interface: v2.00
[   83.693579] em28xx v4l2 driver version 0.1.0 loaded
[   83.695249] em28xx new video device (eb1a:2881): interface 0, class 255
[   83.695266] em28xx Has usb audio class
[   83.695270] em28xx #0: Alternate settings: 8
[   83.695275] em28xx #0: Alternate setting 0, max size= 0
[   83.695279] em28xx #0: Alternate setting 1, max size= 0
[   83.695284] em28xx #0: Alternate setting 2, max size= 1448
[   83.695288] em28xx #0: Alternate setting 3, max size= 2048
[   83.695293] em28xx #0: Alternate setting 4, max size= 2304
[   83.695297] em28xx #0: Alternate setting 5, max size= 2580
[   83.695301] em28xx #0: Alternate setting 6, max size= 2892
[   83.695306] em28xx #0: Alternate setting 7, max size= 3072
[   83.714816] em28xx #0: chip ID is em2882/em2883
[   83.746549] em28xx #0: i2c eeprom 00: 1a eb 67 95 1a eb 81 28 58 12 5c 00 6a 20 6a 00
[   83.746574] em28xx #0: i2c eeprom 10: 00 00 04 57 64 57 00 00 60 f4 00 00 02 02 00 00
[   83.746591] em28xx #0: i2c eeprom 20: 56 00 01 00 00 00 02 00 b8 00 00 00 5b 1e 00 00
[   83.746607] em28xx #0: i2c eeprom 30: 00 00 20 40 20 80 02 20 10 02 00 00 00 00 00 00
[   83.746622] em28xx #0: i2c eeprom 40: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
[   83.746637] em28xx #0: i2c eeprom 50: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
[   83.746652] em28xx #0: i2c eeprom 60: 00 00 00 00 00 00 00 00 00 00 20 03 55 00 53 00
[   83.746668] em28xx #0: i2c eeprom 70: 42 00 20 00 32 00 38 00 38 00 31 00 20 00 56 00
[   83.746683] em28xx #0: i2c eeprom 80: 69 00 64 00 65 00 6f 00 00 00 00 00 00 00 00 00
[   83.746698] em28xx #0: i2c eeprom 90: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
[   83.746714] em28xx #0: i2c eeprom a0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
[   83.746729] em28xx #0: i2c eeprom b0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
[   83.746744] em28xx #0: i2c eeprom c0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
[   83.746759] em28xx #0: i2c eeprom d0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
[   83.746774] em28xx #0: i2c eeprom e0: 5a 00 55 aa 79 55 54 03 00 17 98 01 00 00 00 00
[   83.746790] em28xx #0: i2c eeprom f0: 0c 00 00 01 00 00 00 00 00 00 00 00 00 00 00 00
[   83.746807] EEPROM ID= 0x9567eb1a, hash = 0xb8846b20
[   83.746811] Vendor/Product ID= eb1a:2881
[   83.746815] AC97 audio (5 sample rates)
[   83.746818] USB Remote wakeup capable
[   83.746821] 500mA max power
[   83.746825] Table at 0x04, strings=0x206a, 0x006a, 0x0000
[   83.792652] em28xx #0: found i2c device @ 0xa0 [eeprom]
[   83.797147] em28xx #0: found i2c device @ 0xb8 [tvp5150a]
[   83.799021] em28xx #0: found i2c device @ 0xc2 [tuner (analog)]
[   83.810517] em28xx #0: Your board has no unique USB ID and thus need a hint to be detected.
[   83.810530] em28xx #0: You may try to use card=<n> insmod option to workaround that.
[   83.810536] em28xx #0: Please send an email with this log to:
[   83.810540] em28xx #0: 	V4L Mailing List <video4linux-list@redhat.com>
[   83.810545] em28xx #0: Board eeprom hash is 0xb8846b20
[   83.810549] em28xx #0: Board i2c devicelist hash is 0x27e10080
[   83.810554] em28xx #0: Here is a list of valid choices for the card=<n> insmod option:
[   83.810560] em28xx #0:     card=0 -> Unknown EM2800 video grabber
[   83.810564] em28xx #0:     card=1 -> Unknown EM2750/28xx video grabber
[   83.810569] em28xx #0:     card=2 -> Terratec Cinergy 250 USB
[   83.810573] em28xx #0:     card=3 -> Pinnacle PCTV USB 2
[   83.810578] em28xx #0:     card=4 -> Hauppauge WinTV USB 2
[   83.810582] em28xx #0:     card=5 -> MSI VOX USB 2.0
[   83.810586] em28xx #0:     card=6 -> Terratec Cinergy 200 USB
[   83.810590] em28xx #0:     card=7 -> Leadtek Winfast USB II
[   83.810594] em28xx #0:     card=8 -> Kworld USB2800
[   83.810599] em28xx #0:     card=9 -> Pinnacle Dazzle DVC 90/DVC 100
[   83.810603] em28xx #0:     card=10 -> Hauppauge WinTV HVR 900
[   83.810608] em28xx #0:     card=11 -> Terratec Hybrid XS
[   83.810612] em28xx #0:     card=12 -> Kworld PVR TV 2800 RF
[   83.810616] em28xx #0:     card=13 -> Terratec Prodigy XS
[   83.810620] em28xx #0:     card=14 -> Pixelview Prolink PlayTV USB 2.0
[   83.810625] em28xx #0:     card=15 -> V-Gear PocketTV
[   83.810629] em28xx #0:     card=16 -> Hauppauge WinTV HVR 950
[   83.810634] em28xx #0:     card=17 -> Pinnacle PCTV HD Pro Stick
[   83.810638] em28xx #0:     card=18 -> Hauppauge WinTV HVR 900 (R2)
[   83.810643] em28xx #0:     card=19 -> PointNix Intra-Oral Camera
[   83.810647] em28xx #0:     card=20 -> AMD ATI TV Wonder HD 600
[   83.810652] em28xx #0:     card=21 -> eMPIA Technology, Inc. GrabBeeX+ Video Encoder
[   83.810657] em28xx #0:     card=22 -> Unknown EM2750/EM2751 webcam grabber
[   83.810662] em28xx #0:     card=23 -> Huaqi DLCW-130
[   83.810666] em28xx #0:     card=24 -> D-Link DUB-T210 TV Tuner
[   83.810670] em28xx #0:     card=25 -> Gadmei UTV310
[   83.810674] em28xx #0:     card=26 -> Hercules Smart TV USB 2.0
[   83.810679] em28xx #0:     card=27 -> Pinnacle PCTV USB 2 (Philips FM1216ME)
[   83.810684] em28xx #0:     card=28 -> Leadtek Winfast USB II Deluxe
[   83.810688] em28xx #0:     card=29 -> Pinnacle Dazzle DVC 100
[   83.810693] em28xx #0:     card=30 -> Videology 20K14XUSB USB2.0
[   83.810697] em28xx #0:     card=31 -> Usbgear VD204v9
[   83.810701] em28xx #0:     card=32 -> Supercomp USB 2.0 TV
[   83.810706] em28xx #0:     card=33 -> SIIG AVTuner-PVR/Prolink PlayTV USB 2.0
[   83.810711] em28xx #0:     card=34 -> Terratec Cinergy A Hybrid XS
[   83.810715] em28xx #0:     card=35 -> Typhoon DVD Maker
[   83.810719] em28xx #0:     card=36 -> NetGMBH Cam
[   83.810723] em28xx #0:     card=37 -> Gadmei UTV330
[   83.810727] em28xx #0:     card=38 -> Yakumo MovieMixer
[   83.810732] em28xx #0:     card=39 -> KWorld PVRTV 300U
[   83.810736] em28xx #0:     card=40 -> Plextor ConvertX PX-TV100U
[   83.810740] em28xx #0:     card=41 -> Kworld 350 U DVB-T
[   83.810745] em28xx #0:     card=42 -> Kworld 355 U DVB-T
[   83.810749] em28xx #0:     card=43 -> Terratec Cinergy T XS
[   83.810753] em28xx #0:     card=44 -> Terratec Cinergy T XS (MT2060)
[   83.810758] em28xx #0:     card=45 -> Pinnacle PCTV DVB-T
[   83.810762] em28xx #0:     card=46 -> Compro, VideoMate U3
[   83.810766] em28xx #0:     card=47 -> KWorld DVB-T 305U
[   83.810770] em28xx #0:     card=48 -> KWorld DVB-T 310U
[   83.810774] em28xx #0:     card=49 -> MSI DigiVox A/D
[   83.810778] em28xx #0:     card=50 -> MSI DigiVox A/D II
[   83.810783] em28xx #0:     card=51 -> Terratec Hybrid XS Secam
[   83.810787] em28xx #0:     card=52 -> DNT DA2 Hybrid
[   83.810791] em28xx #0:     card=53 -> Pinnacle Hybrid Pro
[   83.810795] em28xx #0:     card=54 -> Kworld VS-DVB-T 323UR
[   83.810800] em28xx #0:     card=55 -> Terratec Hybrid XS (em2882)
[   83.810804] em28xx #0:     card=56 -> Pinnacle Hybrid Pro (2)
[   83.810809] em28xx #0:     card=57 -> Kworld PlusTV HD Hybrid 330
[   83.810813] em28xx #0:     card=58 -> Compro VideoMate ForYou/Stereo
[   83.992928] tvp5150 5-005c: tvp5150am1 detected.
[   84.141103] em28xx #0: V4L2 device registered as /dev/video0 and /dev/vbi0
[   84.141118] em28xx #0: Found Unknown EM2750/28xx video grabber
[   84.154076] usbcore: registered new interface driver em28xx
[   84.188825] tvp5150 5-005c: tvp5150am1 detected.
[  169.442713] ppdev0: registered pardevice
[  169.492163] ppdev0: unregistered pardevice
[  171.700881] ppdev0: registered pardevice
[  171.748430] ppdev0: unregistered pardevice
[  171.764085] ppdev0: registered pardevice
[  171.812044] ppdev0: unregistered pardevice
[ 1992.488307] cdrom: sr0: mrw address space DMA selected
[ 1992.805328] cdrom: sr0: mrw address space DMA selected
[ 1992.840539] UDF-fs: No VRS found
[ 1992.873276] ISO 9660 Extensions: Microsoft Joliet Level 3
[ 1992.875793] ISOFS: changing to secondary root
[ 5605.624594] tvp5150 5-005c: tvp5150am1 detected.
[/B]
If you've got ideas, please help.

Yours, 

marutinu

---

### Post by NLChris on 2008-12-13
Hey I have the same problem.

I got the analogue part working (without audio) by downloading the missing firmware (using instructions on [http://www.mjmwired.net/kernel/Documentation/video4linux/extract_xc3028.pl](http://www.mjmwired.net/kernel/Documentation/video4linux/extract_xc3028.pl)) and reloading the drivers with the correct card parameter

```

sudo rmmod em28xx-alsa
sudo rmmod em28xx-dvb
sudo rmmod em28xx
sudo modprobe em28xx card=53
sudo modprobe em28xx-dvb
sudo modprobe em28xx-alsa

```

Now I have analogue tv (without sound:( ) but still no DVB-T.

I hope anyone out here knows how to get this card working.

The analogue image quality is perfect but i need to rerun the commands at every reboot now. Far from ideal.

Chris

---

### Post by NLChris on 2008-12-13
I got the DVB-T part working =D

Here is what I did (with some help from google and the em28xx mailinglist)

```

$ sudo aptitude install linux-source
$ cd /usr/src
$ tar xjf linux-source-*.tar.bz2
$ sudo cp linux-source-2.6.27/drivers/media/dvb/dvb-core/*.h linux- headers-2.6.27-9-generic/drivers/media/dvb/dvb-core/ 
$ sudo cp linux-source-2.6.27/drivers/media/dvb/frontends/lgdt330x.h linux-headers-2.6.27-9/drivers/media/dvb/frontends/ 
$ sudo cp linux-source-2.6.27/drivers/media/video/msp3400-driver.h linux-headers-2.6.27-9/drivers/media/dvb/frontends/

```

Then I compilled the V4L-DVB-KERNEL tree from mcentral:
```

$ hg clone http://mcentral.de/hg/~mrec/v4l-dvb-kernel
$ cd v4l-dvb-kernel
$ make
$ sudo make install

```

Now plug in your stick and off you go =D. 

Chris

---

### Post by marutinu on 2008-12-15
Hi Chris and many thanks for the tip. I'll try it out as soon as I find a moment.

Marcin

---

### Post by ourAri on 2009-07-10
> **NLChris said:**
> Hey I have the same problem.

I got the analogue part working (without audio) by downloading the missing firmware (using instructions on [http://www.mjmwired.net/kernel/Documentation/video4linux/extract_xc3028.pl](http://www.mjmwired.net/kernel/Documentation/video4linux/extract_xc3028.pl)) and reloading the drivers with the correct card parameter

```

sudo rmmod em28xx-alsa
sudo rmmod em28xx-dvb
sudo rmmod em28xx
sudo modprobe em28xx card=53
sudo modprobe em28xx-dvb
sudo modprobe em28xx-alsa

```Now I have analogue tv (without sound:( ) but still no DVB-T.

I hope anyone out here knows how to get this card working.

The analogue image quality is perfect but i need to rerun the commands at every reboot now. Far from ideal.

Chris

I followed the instructions on this page to use a Plextor Px-
Av200U together with an anolog camera as a web cam. Using above commands I was able to get video in Cheese program, and it actually looked very good. however, the video is not good in Skype. It's like every other row and column are missing and the picture is not interlaced well. Has anyone tried to do something like this? 
Why can I see a good video in Cheese, but something crappy in skype?

---

### Post by trinacriax on 2009-07-29
Hi to all,

I've a pinnacle 330e and I've also tried to install it on ubuntu 9.04.
I followed the whole procedure, but kaffeine does not show me any dvb icon.

I think that the device is recognized correctly, this is the dmesg when I plugin the device.

```

[ 4180.412281] usb 2-2: new high speed USB device using ehci_hcd and address 9
[ 4180.557094] usb 2-2: configuration #1 chosen from 1 choice
[ 4180.557276] em28xx: New device Pinnacle Systems PCTV 330e @ 480 Mbps (2304:0226, interface 0, class 0)
[ 4180.557286] em28xx #0: Identified as Pinnacle Hybrid Pro (2) (card=56)
[ 4180.557417] em28xx #0: chip ID is em2882/em2883
[ 4180.734101] em28xx #0: i2c eeprom 00: 1a eb 67 95 04 23 26 02 d0 12 5c 03 8e 16 a4 1c
[ 4180.734125] em28xx #0: i2c eeprom 10: 6a 24 27 57 46 07 01 00 00 00 00 00 00 00 00 00
[ 4180.734144] em28xx #0: i2c eeprom 20: 46 00 01 00 f0 10 02 00 b8 00 00 00 5b e0 00 00
[ 4180.734163] em28xx #0: i2c eeprom 30: 00 00 20 40 20 6e 02 20 10 01 00 00 00 00 00 00
[ 4180.734182] em28xx #0: i2c eeprom 40: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
[ 4180.734201] em28xx #0: i2c eeprom 50: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
[ 4180.734220] em28xx #0: i2c eeprom 60: 00 00 00 00 00 00 00 00 00 00 24 03 50 00 69 00
[ 4180.734238] em28xx #0: i2c eeprom 70: 6e 00 6e 00 61 00 63 00 6c 00 65 00 20 00 53 00
[ 4180.734257] em28xx #0: i2c eeprom 80: 79 00 73 00 74 00 65 00 6d 00 73 00 00 00 16 03
[ 4180.734275] em28xx #0: i2c eeprom 90: 50 00 43 00 54 00 56 00 20 00 33 00 33 00 30 00
[ 4180.734294] em28xx #0: i2c eeprom a0: 65 00 00 00 1c 03 30 00 37 00 30 00 34 00 30 00
[ 4180.734313] em28xx #0: i2c eeprom b0: 31 00 38 00 37 00 38 00 36 00 38 00 35 00 00 00
[ 4180.734331] em28xx #0: i2c eeprom c0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
[ 4180.734350] em28xx #0: i2c eeprom d0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
[ 4180.734368] em28xx #0: i2c eeprom e0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
[ 4180.734387] em28xx #0: i2c eeprom f0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
[ 4180.734408] em28xx #0: EEPROM ID= 0x9567eb1a, EEPROM hash = 0xd3b3a5bf
[ 4180.734412] em28xx #0: EEPROM info:
[ 4180.734415] em28xx #0:	AC97 audio (5 sample rates)
[ 4180.734418] em28xx #0:	500mA max power
[ 4180.734422] em28xx #0:	Table at 0x27, strings=0x168e, 0x1ca4, 0x246a
[ 4180.734428] em28xx #0: 
[ 4180.734429] 
[ 4180.734434] em28xx #0: The support for this board weren't valid yet.
[ 4180.734438] em28xx #0: Please send a report of having this working
[ 4180.734441] em28xx #0: not to V4L mailing list (and/or to other addresses)
[ 4180.734444] 
[ 4180.744523] tvp5150 0-005c: chip found @ 0xb8 (em28xx #0)
[ 4180.749881] tuner 0-0061: chip found @ 0xc2 (em28xx #0)
[ 4180.750066] xc2028 0-0061: creating new instance
[ 4180.750071] xc2028 0-0061: type set to XCeive xc2028/xc3028 tuner
[ 4180.750082] usb 2-2: firmware: requesting xc3028-v27.fw
[ 4180.758774] xc2028 0-0061: Loading 80 firmware images from xc3028-v27.fw, type: xc2028 firmware, ver 2.7
[ 4180.804297] xc2028 0-0061: Loading firmware for type=BASE MTS (5), id 0000000000000000.
[ 4181.893914] xc2028 0-0061: Loading firmware for type=MTS (4), id 000000000000b700.
[ 4181.913681] xc2028 0-0061: Loading SCODE for type=MTS LCD NOGD MONO IF SCODE HAS_IF_4500 (6002b004), id 000000000000b700.
[ 4182.100657] em28xx #0: Config register raw data: 0xd0
[ 4182.102896] em28xx #0: AC97 vendor ID = 0xffffffff
[ 4182.104027] em28xx #0: AC97 features = 0x6a90
[ 4182.104033] em28xx #0: Empia 202 AC97 audio processor detected
[ 4182.237444] tvp5150 0-005c: tvp5150am1 detected.
[ 4182.342663] em28xx #0: v4l2 driver version 0.1.2
[ 4182.431110] em28xx #0: V4L2 device registered as /dev/video1 and /dev/vbi0
[ 4182.431118] em28xx-audio.c: probing for em28x1 non standard usbaudio
[ 4182.431122] em28xx-audio.c: Copyright (C) 2006 Markus Rechberger
[ 4182.604567] tvp5150 0-005c: tvp5150am1 detected.

```


and

```

# lsmod |grep em28
em28xx_dvb             19076  0 
em28xx_alsa            17800  0 
em28xx                103088  2 em28xx_dvb,em28xx_alsa
dvb_core              111792  1 em28xx_dvb
snd_pcm                99464  3 em28xx_alsa,snd_hda_intel,snd_pcm_oss
ir_common              61060  1 em28xx
v4l2_common            29056  3 em28xx,tuner,tvp5150
videodev               50464  5 em28xx,tuner,tvp5150,uvcvideo,v4l2_common
videobuf_vmalloc       16004  1 em28xx
videobuf_core          29572  2 em28xx,videobuf_vmalloc
tveeprom               23556  1 em28xx
snd                    78920  12 em28xx_alsa,snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device

```

suggestions?
Thanks

---

### Post by pingnaveen@gmail.com on 2009-10-03
Thanks a ton! I got video working by following your instructions. 
Were you able to get audio? If yes, please let me know.

Thanks...

---

