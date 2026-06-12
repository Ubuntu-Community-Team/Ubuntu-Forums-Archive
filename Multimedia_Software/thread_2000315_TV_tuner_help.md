---
title: "TV tuner help"
date: 2012-06-09
forum: Multimedia Software
---

### Post by gideon793 on 2012-06-09
i have a USB tv tuner card that works fine with vlc in windows. however i have not been able to make it work in ubutu.
the ouptput from lsusb -v is:
```
Bus 001 Device 006: ID eb1a:2860 eMPIA Technology, Inc. 
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  idVendor           0xeb1a eMPIA Technology, Inc.
  idProduct          0x2860 
  bcdDevice            1.00
  iManufacturer           0 
  iProduct                1 
  iSerial                 0 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength          249
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0x80
      (Bus Powered)
    MaxPower              500mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           3
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass      0 
      bInterfaceProtocol    255 
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0001  1x 1 bytes
        bInterval              11
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x82  EP 2 IN
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0000  1x 0 bytes
        bInterval               1
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x84  EP 4 IN
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0000  1x 0 bytes
        bInterval               1
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       1
      bNumEndpoints           3
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass      0 
      bInterfaceProtocol    255 
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0001  1x 1 bytes
        bInterval              11
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x82  EP 2 IN
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0000  1x 0 bytes
        bInterval               1
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x84  EP 4 IN
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0000  1x 0 bytes
        bInterval               1
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       2
      bNumEndpoints           3
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass      0 
      bInterfaceProtocol    255 
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0001  1x 1 bytes
        bInterval              11
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x82  EP 2 IN
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0ad4  2x 724 bytes
        bInterval               1
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x84  EP 4 IN
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0000  1x 0 bytes
        bInterval               1
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       3
      bNumEndpoints           3
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass      0 
      bInterfaceProtocol    255 
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0001  1x 1 bytes
        bInterval              11
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x82  EP 2 IN
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0c00  2x 1024 bytes
        bInterval               1
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x84  EP 4 IN
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0000  1x 0 bytes
        bInterval               1
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       4
      bNumEndpoints           3
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass      0 
      bInterfaceProtocol    255 
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0001  1x 1 bytes
        bInterval              11
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x82  EP 2 IN
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x1300  3x 768 bytes
        bInterval               1
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x84  EP 4 IN
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0000  1x 0 bytes
        bInterval               1
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       5
      bNumEndpoints           3
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass      0 
      bInterfaceProtocol    255 
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0001  1x 1 bytes
        bInterval              11
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x82  EP 2 IN
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x135c  3x 860 bytes
        bInterval               1
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x84  EP 4 IN
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0000  1x 0 bytes
        bInterval               1
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       6
      bNumEndpoints           3
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass      0 
      bInterfaceProtocol    255 
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0001  1x 1 bytes
        bInterval              11
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x82  EP 2 IN
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x13c4  3x 964 bytes
        bInterval               1
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x84  EP 4 IN
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0000  1x 0 bytes
        bInterval               1
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       7
      bNumEndpoints           3
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass      0 
      bInterfaceProtocol    255 
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0001  1x 1 bytes
        bInterval              11
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x82  EP 2 IN
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x1400  3x 1024 bytes
        bInterval               1
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x84  EP 4 IN
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0000  1x 0 bytes
        bInterval               1
```

the out put from dmesg is
```
[ 3264.554408] em28xx #0: disconnecting em28xx #0 video
[ 3264.554413] em28xx #0: V4L2 device vbi0 deregistered
[ 3264.554558] em28xx #0: V4L2 device video0 deregistered
[ 3283.384752] usb 1-1.1: new high-speed USB device number 6 using ehci_hcd
[ 3283.480277] em28xx: New device USB 2860 Device @ 480 Mbps (eb1a:2860, interface 0, class 0)
[ 3283.480435] em28xx #0: chip ID is em2860
[ 3283.610352] em28xx #0: i2c eeprom 00: 1a eb 67 95 1a eb 60 28 c0 00 3e 01 6a 22 00 00
[ 3283.610366] em28xx #0: i2c eeprom 10: 00 00 04 57 4e 03 00 00 60 c0 60 c0 02 02 02 02
[ 3283.610377] em28xx #0: i2c eeprom 20: 16 00 00 02 f0 10 02 00 4a 00 00 00 5b 00 00 00
[ 3283.610389] em28xx #0: i2c eeprom 30: 00 00 20 40 20 80 02 20 10 01 02 01 00 00 00 00
[ 3283.610400] em28xx #0: i2c eeprom 40: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
[ 3283.610411] em28xx #0: i2c eeprom 50: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
[ 3283.610422] em28xx #0: i2c eeprom 60: 00 00 00 00 00 00 00 00 00 00 22 03 55 00 53 00
[ 3283.610434] em28xx #0: i2c eeprom 70: 42 00 20 00 32 00 38 00 36 00 30 00 20 00 44 00
[ 3283.610445] em28xx #0: i2c eeprom 80: 65 00 76 00 69 00 63 00 65 00 00 00 00 00 00 00
[ 3283.610456] em28xx #0: i2c eeprom 90: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
[ 3283.610467] em28xx #0: i2c eeprom a0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
[ 3283.610478] em28xx #0: i2c eeprom b0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
[ 3283.610489] em28xx #0: i2c eeprom c0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
[ 3283.610500] em28xx #0: i2c eeprom d0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
[ 3283.610512] em28xx #0: i2c eeprom e0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
[ 3283.610523] em28xx #0: i2c eeprom f0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
[ 3283.610535] em28xx #0: EEPROM ID= 0x9567eb1a, EEPROM hash = 0x8f597549
[ 3283.610538] em28xx #0: EEPROM info:
[ 3283.610539] em28xx #0:	No audio on board.
[ 3283.610541] em28xx #0:	500mA max power
[ 3283.610544] em28xx #0:	Table at 0x04, strings=0x226a, 0x0000, 0x0000
[ 3283.682472] em28xx #0: found i2c device @ 0x4a [saa7113h]
[ 3283.698549] em28xx #0: found i2c device @ 0xa0 [eeprom]
[ 3283.704907] em28xx #0: found i2c device @ 0xc2 [tuner (analog)]
[ 3283.716125] em28xx #0: Your board has no unique USB ID and thus need a hint to be detected.
[ 3283.716129] em28xx #0: You may try to use card=<n> insmod option to workaround that.
[ 3283.716131] em28xx #0: Please send an email with this log to:
[ 3283.716133] em28xx #0: 	V4L Mailing List <linux-media@vger.kernel.org>
[ 3283.716136] em28xx #0: Board eeprom hash is 0x8f597549
[ 3283.716138] em28xx #0: Board i2c devicelist hash is 0x6bc40080
[ 3283.716141] em28xx #0: Here is a list of valid choices for the card=<n> insmod option:
[ 3283.716144] em28xx #0:     card=0 -> Unknown EM2800 video grabber
[ 3283.716146] em28xx #0:     card=1 -> Unknown EM2750/28xx video grabber
[ 3283.716149] em28xx #0:     card=2 -> Terratec Cinergy 250 USB
[ 3283.716151] em28xx #0:     card=3 -> Pinnacle PCTV USB 2
[ 3283.716154] em28xx #0:     card=4 -> Hauppauge WinTV USB 2
[ 3283.716156] em28xx #0:     card=5 -> MSI VOX USB 2.0
[ 3283.716158] em28xx #0:     card=6 -> Terratec Cinergy 200 USB
[ 3283.716160] em28xx #0:     card=7 -> Leadtek Winfast USB II
[ 3283.716163] em28xx #0:     card=8 -> Kworld USB2800
[ 3283.716165] em28xx #0:     card=9 -> Pinnacle Dazzle DVC 90/100/101/107 / Kaiser Baas Video to DVD maker / Kworld DVD Maker 2
[ 3283.716168] em28xx #0:     card=10 -> Hauppauge WinTV HVR 900
[ 3283.716171] em28xx #0:     card=11 -> Terratec Hybrid XS
[ 3283.716173] em28xx #0:     card=12 -> Kworld PVR TV 2800 RF
[ 3283.716176] em28xx #0:     card=13 -> Terratec Prodigy XS
[ 3283.716178] em28xx #0:     card=14 -> SIIG AVTuner-PVR / Pixelview Prolink PlayTV USB 2.0
[ 3283.716181] em28xx #0:     card=15 -> V-Gear PocketTV
[ 3283.716183] em28xx #0:     card=16 -> Hauppauge WinTV HVR 950
[ 3283.716185] em28xx #0:     card=17 -> Pinnacle PCTV HD Pro Stick
[ 3283.716188] em28xx #0:     card=18 -> Hauppauge WinTV HVR 900 (R2)
[ 3283.716190] em28xx #0:     card=19 -> EM2860/SAA711X Reference Design
[ 3283.716193] em28xx #0:     card=20 -> AMD ATI TV Wonder HD 600
[ 3283.716195] em28xx #0:     card=21 -> eMPIA Technology, Inc. GrabBeeX+ Video Encoder
[ 3283.716198] em28xx #0:     card=22 -> EM2710/EM2750/EM2751 webcam grabber
[ 3283.716201] em28xx #0:     card=23 -> Huaqi DLCW-130
[ 3283.716203] em28xx #0:     card=24 -> D-Link DUB-T210 TV Tuner
[ 3283.716205] em28xx #0:     card=25 -> Gadmei UTV310
[ 3283.716207] em28xx #0:     card=26 -> Hercules Smart TV USB 2.0
[ 3283.716210] em28xx #0:     card=27 -> Pinnacle PCTV USB 2 (Philips FM1216ME)
[ 3283.716212] em28xx #0:     card=28 -> Leadtek Winfast USB II Deluxe
[ 3283.716215] em28xx #0:     card=29 -> EM2860/TVP5150 Reference Design
[ 3283.716217] em28xx #0:     card=30 -> Videology 20K14XUSB USB2.0
[ 3283.716220] em28xx #0:     card=31 -> Usbgear VD204v9
[ 3283.716222] em28xx #0:     card=32 -> Supercomp USB 2.0 TV
[ 3283.716224] em28xx #0:     card=33 -> Elgato Video Capture
[ 3283.716227] em28xx #0:     card=34 -> Terratec Cinergy A Hybrid XS
[ 3283.716229] em28xx #0:     card=35 -> Typhoon DVD Maker
[ 3283.716231] em28xx #0:     card=36 -> NetGMBH Cam
[ 3283.716234] em28xx #0:     card=37 -> Gadmei UTV330
[ 3283.716236] em28xx #0:     card=38 -> Yakumo MovieMixer
[ 3283.716238] em28xx #0:     card=39 -> KWorld PVRTV 300U
[ 3283.716240] em28xx #0:     card=40 -> Plextor ConvertX PX-TV100U
[ 3283.716243] em28xx #0:     card=41 -> Kworld 350 U DVB-T
[ 3283.716245] em28xx #0:     card=42 -> Kworld 355 U DVB-T
[ 3283.716247] em28xx #0:     card=43 -> Terratec Cinergy T XS
[ 3283.716250] em28xx #0:     card=44 -> Terratec Cinergy T XS (MT2060)
[ 3283.716252] em28xx #0:     card=45 -> Pinnacle PCTV DVB-T
[ 3283.716254] em28xx #0:     card=46 -> Compro, VideoMate U3
[ 3283.716257] em28xx #0:     card=47 -> KWorld DVB-T 305U
[ 3283.716259] em28xx #0:     card=48 -> KWorld DVB-T 310U
[ 3283.716261] em28xx #0:     card=49 -> MSI DigiVox A/D
[ 3283.716263] em28xx #0:     card=50 -> MSI DigiVox A/D II
[ 3283.716266] em28xx #0:     card=51 -> Terratec Hybrid XS Secam
[ 3283.716268] em28xx #0:     card=52 -> DNT DA2 Hybrid
[ 3283.716270] em28xx #0:     card=53 -> Pinnacle Hybrid Pro
[ 3283.716273] em28xx #0:     card=54 -> Kworld VS-DVB-T 323UR
[ 3283.716275] em28xx #0:     card=55 -> Terratec Cinnergy Hybrid T USB XS (em2882)
[ 3283.716278] em28xx #0:     card=56 -> Pinnacle Hybrid Pro (330e)
[ 3283.716280] em28xx #0:     card=57 -> Kworld PlusTV HD Hybrid 330
[ 3283.716283] em28xx #0:     card=58 -> Compro VideoMate ForYou/Stereo
[ 3283.716285] em28xx #0:     card=59 -> (null)
[ 3283.716287] em28xx #0:     card=60 -> Hauppauge WinTV HVR 850
[ 3283.716290] em28xx #0:     card=61 -> Pixelview PlayTV Box 4 USB 2.0
[ 3283.716292] em28xx #0:     card=62 -> Gadmei TVR200
[ 3283.716294] em28xx #0:     card=63 -> Kaiomy TVnPC U2
[ 3283.716297] em28xx #0:     card=64 -> Easy Cap Capture DC-60
[ 3283.716299] em28xx #0:     card=65 -> IO-DATA GV-MVP/SZ
[ 3283.716301] em28xx #0:     card=66 -> Empire dual TV
[ 3283.716303] em28xx #0:     card=67 -> Terratec Grabby
[ 3283.716306] em28xx #0:     card=68 -> Terratec AV350
[ 3283.716308] em28xx #0:     card=69 -> KWorld ATSC 315U HDTV TV Box
[ 3283.716310] em28xx #0:     card=70 -> Evga inDtube
[ 3283.716313] em28xx #0:     card=71 -> Silvercrest Webcam 1.3mpix
[ 3283.716315] em28xx #0:     card=72 -> Gadmei UTV330+
[ 3283.716317] em28xx #0:     card=73 -> Reddo DVB-C USB TV Box
[ 3283.716320] em28xx #0:     card=74 -> Actionmaster/LinXcel/Digitus VC211A
[ 3283.716322] em28xx #0:     card=75 -> Dikom DK300
[ 3283.716324] em28xx #0:     card=76 -> KWorld PlusTV 340U or UB435-Q (ATSC)
[ 3283.716327] em28xx #0:     card=77 -> EM2874 Leadership ISDBT
[ 3283.716329] em28xx #0:     card=78 -> PCTV nanoStick T2 290e
[ 3283.716332] em28xx #0:     card=79 -> Terratec Cinergy H5
[ 3283.716334] em28xx #0:     card=80 -> PCTV DVB-S2 Stick (460e)
[ 3283.716336] em28xx #0: Board not discovered
[ 3283.716338] em28xx #0: Identified as Unknown EM2750/28xx video grabber (card=1)
[ 3283.716341] em28xx #0: Your board has no unique USB ID and thus need a hint to be detected.
[ 3283.716344] em28xx #0: You may try to use card=<n> insmod option to workaround that.
[ 3283.716346] em28xx #0: Please send an email with this log to:
[ 3283.716348] em28xx #0: 	V4L Mailing List <linux-media@vger.kernel.org>
[ 3283.716350] em28xx #0: Board eeprom hash is 0x8f597549
[ 3283.716353] em28xx #0: Board i2c devicelist hash is 0x6bc40080
[ 3283.716355] em28xx #0: Here is a list of valid choices for the card=<n> insmod option:
[ 3283.716358] em28xx #0:     card=0 -> Unknown EM2800 video grabber
[ 3283.716360] em28xx #0:     card=1 -> Unknown EM2750/28xx video grabber
[ 3283.716363] em28xx #0:     card=2 -> Terratec Cinergy 250 USB
[ 3283.716365] em28xx #0:     card=3 -> Pinnacle PCTV USB 2
[ 3283.716367] em28xx #0:     card=4 -> Hauppauge WinTV USB 2
[ 3283.716369] em28xx #0:     card=5 -> MSI VOX USB 2.0
[ 3283.716372] em28xx #0:     card=6 -> Terratec Cinergy 200 USB
[ 3283.716374] em28xx #0:     card=7 -> Leadtek Winfast USB II
[ 3283.716376] em28xx #0:     card=8 -> Kworld USB2800
[ 3283.716379] em28xx #0:     card=9 -> Pinnacle Dazzle DVC 90/100/101/107 / Kaiser Baas Video to DVD maker / Kworld DVD Maker 2
[ 3283.716382] em28xx #0:     card=10 -> Hauppauge WinTV HVR 900
[ 3283.716384] em28xx #0:     card=11 -> Terratec Hybrid XS
[ 3283.716387] em28xx #0:     card=12 -> Kworld PVR TV 2800 RF
[ 3283.716389] em28xx #0:     card=13 -> Terratec Prodigy XS
[ 3283.716391] em28xx #0:     card=14 -> SIIG AVTuner-PVR / Pixelview Prolink PlayTV USB 2.0
[ 3283.716394] em28xx #0:     card=15 -> V-Gear PocketTV
[ 3283.716396] em28xx #0:     card=16 -> Hauppauge WinTV HVR 950
[ 3283.716398] em28xx #0:     card=17 -> Pinnacle PCTV HD Pro Stick
[ 3283.716401] em28xx #0:     card=18 -> Hauppauge WinTV HVR 900 (R2)
[ 3283.716403] em28xx #0:     card=19 -> EM2860/SAA711X Reference Design
[ 3283.716406] em28xx #0:     card=20 -> AMD ATI TV Wonder HD 600
[ 3283.716408] em28xx #0:     card=21 -> eMPIA Technology, Inc. GrabBeeX+ Video Encoder
[ 3283.716411] em28xx #0:     card=22 -> EM2710/EM2750/EM2751 webcam grabber
[ 3283.716414] em28xx #0:     card=23 -> Huaqi DLCW-130
[ 3283.716416] em28xx #0:     card=24 -> D-Link DUB-T210 TV Tuner
[ 3283.716418] em28xx #0:     card=25 -> Gadmei UTV310
[ 3283.716420] em28xx #0:     card=26 -> Hercules Smart TV USB 2.0
[ 3283.716423] em28xx #0:     card=27 -> Pinnacle PCTV USB 2 (Philips FM1216ME)
[ 3283.716425] em28xx #0:     card=28 -> Leadtek Winfast USB II Deluxe
[ 3283.716428] em28xx #0:     card=29 -> EM2860/TVP5150 Reference Design
[ 3283.716430] em28xx #0:     card=30 -> Videology 20K14XUSB USB2.0
[ 3283.716432] em28xx #0:     card=31 -> Usbgear VD204v9
[ 3283.716435] em28xx #0:     card=32 -> Supercomp USB 2.0 TV
[ 3283.716437] em28xx #0:     card=33 -> Elgato Video Capture
[ 3283.716439] em28xx #0:     card=34 -> Terratec Cinergy A Hybrid XS
[ 3283.716442] em28xx #0:     card=35 -> Typhoon DVD Maker
[ 3283.716444] em28xx #0:     card=36 -> NetGMBH Cam
[ 3283.716446] em28xx #0:     card=37 -> Gadmei UTV330
[ 3283.716448] em28xx #0:     card=38 -> Yakumo MovieMixer
[ 3283.716450] em28xx #0:     card=39 -> KWorld PVRTV 300U
[ 3283.716453] em28xx #0:     card=40 -> Plextor ConvertX PX-TV100U
[ 3283.716455] em28xx #0:     card=41 -> Kworld 350 U DVB-T
[ 3283.716457] em28xx #0:     card=42 -> Kworld 355 U DVB-T
[ 3283.716459] em28xx #0:     card=43 -> Terratec Cinergy T XS
[ 3283.716462] em28xx #0:     card=44 -> Terratec Cinergy T XS (MT2060)
[ 3283.716464] em28xx #0:     card=45 -> Pinnacle PCTV DVB-T
[ 3283.716466] em28xx #0:     card=46 -> Compro, VideoMate U3
[ 3283.716469] em28xx #0:     card=47 -> KWorld DVB-T 305U
[ 3283.716471] em28xx #0:     card=48 -> KWorld DVB-T 310U
[ 3283.716473] em28xx #0:     card=49 -> MSI DigiVox A/D
[ 3283.716475] em28xx #0:     card=50 -> MSI DigiVox A/D II
[ 3283.716478] em28xx #0:     card=51 -> Terratec Hybrid XS Secam
[ 3283.716480] em28xx #0:     card=52 -> DNT DA2 Hybrid
[ 3283.716482] em28xx #0:     card=53 -> Pinnacle Hybrid Pro
[ 3283.716484] em28xx #0:     card=54 -> Kworld VS-DVB-T 323UR
[ 3283.716487] em28xx #0:     card=55 -> Terratec Cinnergy Hybrid T USB XS (em2882)
[ 3283.716489] em28xx #0:     card=56 -> Pinnacle Hybrid Pro (330e)
[ 3283.716492] em28xx #0:     card=57 -> Kworld PlusTV HD Hybrid 330
[ 3283.716494] em28xx #0:     card=58 -> Compro VideoMate ForYou/Stereo
[ 3283.716497] em28xx #0:     card=59 -> (null)
[ 3283.716499] em28xx #0:     card=60 -> Hauppauge WinTV HVR 850
[ 3283.716501] em28xx #0:     card=61 -> Pixelview PlayTV Box 4 USB 2.0
[ 3283.716503] em28xx #0:     card=62 -> Gadmei TVR200
[ 3283.716506] em28xx #0:     card=63 -> Kaiomy TVnPC U2
[ 3283.716508] em28xx #0:     card=64 -> Easy Cap Capture DC-60
[ 3283.716510] em28xx #0:     card=65 -> IO-DATA GV-MVP/SZ
[ 3283.716512] em28xx #0:     card=66 -> Empire dual TV
[ 3283.716515] em28xx #0:     card=67 -> Terratec Grabby
[ 3283.716517] em28xx #0:     card=68 -> Terratec AV350
[ 3283.716519] em28xx #0:     card=69 -> KWorld ATSC 315U HDTV TV Box
[ 3283.716521] em28xx #0:     card=70 -> Evga inDtube
[ 3283.716523] em28xx #0:     card=71 -> Silvercrest Webcam 1.3mpix
[ 3283.716526] em28xx #0:     card=72 -> Gadmei UTV330+
[ 3283.716528] em28xx #0:     card=73 -> Reddo DVB-C USB TV Box
[ 3283.716530] em28xx #0:     card=74 -> Actionmaster/LinXcel/Digitus VC211A
[ 3283.716533] em28xx #0:     card=75 -> Dikom DK300
[ 3283.716535] em28xx #0:     card=76 -> KWorld PlusTV 340U or UB435-Q (ATSC)
[ 3283.716538] em28xx #0:     card=77 -> EM2874 Leadership ISDBT
[ 3283.716540] em28xx #0:     card=78 -> PCTV nanoStick T2 290e
[ 3283.716542] em28xx #0:     card=79 -> Terratec Cinergy H5
[ 3283.716544] em28xx #0:     card=80 -> PCTV DVB-S2 Stick (460e)
[ 3283.716622] em28xx #0: Config register raw data: 0xc0
[ 3283.716625] em28xx #0: v4l2 driver version 0.1.3
[ 3284.206500] em28xx #0: V4L2 video device registered as video0
[ 3284.206504] em28xx #0: V4L2 VBI device registered as vbi0
[ 3290.328753] [Hardware Error]: Machine check events logged
[ 3888.959632] usb 2-1.2: USB disconnect, device number 4
[ 3892.259176] usb 1-1.4: USB disconnect, device number 5
```

Can anyone help me setup either tvtime or some other program.

---

### Post by davis68nf on 2013-02-05
I had trouble with my tvtime too. HVR-850 sent a video, but there was no audio. The volume was set at 0 and would not move.


 The solution I found was here:
[http://kimbriggs.com/computers/computer-notes/linux-notes/tvtime-volume-notes.file](http://kimbriggs.com/computers/computer-notes/linux-notes/tvtime-volume-notes.file)
 ---------------------------------------
 In a nutshell, type:
  sudo gedit /etc/tvtime/tvtime.xml

and change the line:
  <option name="MixerDevice" value="/dev/mixer:vol"/>


 So, my tvtime.xml now reads:
  <option name="MixerDevice" value="HVR850:vol"/>


 The OLD code used to read:
  <option name="MixerDevice" value="default/Line"/>

---

### Post by BicyclerBoy on 2013-02-05
@davis68nf
Can you please stop spamming the forum.

@OP
If your USB device has not found the trash bin..
Your device looks to be one to the plethora of cheap clones based around Empia
[http://linuxtv.org/wiki/index.php/Em28xx_devices#em2860_based_devices](http://linuxtv.org/wiki/index.php/Em28xx_devices#em2860_based_devices)

The fact your device has iProduct=2860 and not a registered/unique code supports the above..
Because there is no unique usbID the driver has guessed card=1 & this seems to fail.
```
[Hardware Error]: Machine check events logged
```

You might be lucky & find that one of the other suggested models will work.

types 19 25 could be worth trying.

```
sudo modinfo em28xx
sudo rmmod em28xx
sudo modprobe em28xx card=19
```

---

### Post by thesleash on 2013-11-15
the following worked for me

avconv -f video4linux2 -channel 1 -i /dev/video0 -f alsa -i default -b 1200k -ab 128k -vcodec mpeg4 -acodec libmp3lame -vol 105 -r 17 -vf yadif,scale=720:406,scale=iw/1.15:-1 out.avi

if you have a built in webcam, video0 could be video1.

if you are using s-video instead of composite use channel 0.

[http://www.youtube.com/user/TheSleash](http://www.youtube.com/user/TheSleash)

---

### Post by thesleash on 2013-11-15
also, for viewing tvtime worked, you can install it with terminal with the following

sudo apt-get install tvtime

---

### Post by Bucky Ball on 2013-11-15
@davis68nf: While this might be solved for you it is not for the OP. Putting 'SOLVED' at the head of your post is completely misleading (as you could be confused with the OP). 

I have edited your post and removed 'Solved'.

---

### Post by thesleash on 2013-12-02
the following command worked for me.

ffmpeg -f video4linux2 -channel 1 -i /dev/video0 -f alsa -i default -qscale 8 -vol 86 -crf 10 -ar 44100 -threads 1 -vf yadif,scale=720:406,scale=iw/1.075:-1 -y out.mpg

as proof here's a link to one of my youtube channels.

[http://www.youtube.com/user/thesleash](http://www.youtube.com/user/thesleash)

---

