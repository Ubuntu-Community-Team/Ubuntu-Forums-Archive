---
title: "Trying to get HVR 850 (usb) tuner to play on cable."
date: 2015-03-04
forum: Multimedia Software
---

### Post by jeff116 on 2015-03-04
I have it running on the antenna (broadcast) channels in MeTV.  However when I connect the cable from the cable box all I need it to find is channel 3.  Does not find any channels.  

In the set up channel search screen it shows the device to be "Auvitek AU8522 QAM/8VSB".

When I run lsusb, I get the following:
Bus 002 Device 003: ID 0424:2514 Standard Microsystems Corp. USB 2.0 Hub
**Bus 002 Device 005: ID 2040:7240 Hauppauge WinTV HVR-850**
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 008 Device 002: ID 03f0:0004 Hewlett-Packard DeskJet 895c
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 003: ID 413c:3012 Dell Computer Corp. Optical Wheel Mouse
Bus 004 Device 002: ID 413c:2105 Dell Computer Corp. Model L100 Keyboard
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

If I plug this device into a Win 7 computer... it works on broadcast and cable channels.

Do I have the wrong firmware or drivers loading?
Suggestions?
Thanks for your help !

---

### Post by jeff116 on 2015-03-05
Interesting...  I installed TVTime and the analog channel works, so I know the tuner works.  However, TVTime does not record.  Any suggestions as to how to make it work with other programs?

---

### Post by MartyBuntu on 2015-03-05
Have you tried **Kaffeine**? It works with my Hauppauge card and OTA television recording...

---

### Post by jeff116 on 2015-03-05
Yes.  Did try Kaffeine.  Search and it would not find channels when searching for ntsc....or any other profiles there.

---

### Post by jeff116 on 2015-03-05
Yes.  Did try Kaffeine.  Search and it would not find channels when searching for ntsc....or any other profiles there.

---

### Post by Yellow Pasque on 2015-03-05
The firmware is included in the 'linux-firmware' package, so you shouldn't have to manually download it. It should be at /lib/firmware/dvb-fe-xc5000-1.6.114.fw

Maybe you should check dmesg for similar output, though if you get a picture, I think you'll be okay:
[http://www.linuxtv.org/wiki/index.php/Hauppauge_WinTV-HVR-850#Making_it_Work](http://www.linuxtv.org/wiki/index.php/Hauppauge_WinTV-HVR-850#Making_it_Work)

---

### Post by jeff116 on 2015-03-08
> **Temüjin said:**
> The firmware is included in the 'linux-firmware' package, so you shouldn't have to manually download it. It should be at /lib/firmware/dvb-fe-xc5000-1.6.114.fw

Maybe you should check dmesg for similar output, though if you get a picture, I think you'll be okay:
[http://www.linuxtv.org/wiki/index.php/Hauppauge_WinTV-HVR-850#Making_it_Work](http://www.linuxtv.org/wiki/index.php/Hauppauge_WinTV-HVR-850#Making_it_Work)

It looks like my dmesg output is consistent.... again... it works on the Over air broadcast digital channels... just does not find channel 3, so I can't get it to work when connected to my cable box.... any suggestions?  thanks..

Here is part of my dmesg output...
[    1.726110] usb 2-2: New USB device found, idVendor=2040, idProduct=7240
[    1.726113] usb 2-2: New USB device strings: Mfr=1, Product=2, SerialNumber=10
[    1.726116] usb 2-2: Product: WinTV HVR-850
[    1.726118] usb 2-2: Manufacturer: Hauppauge
[    1.726120] usb 2-2: SerialNumber: 4032673289
.....
[   22.255560] au0828: i2c bus registered
[   22.494351] gpio_ich: GPIO from 184 to 255 on gpio_ich
[   22.622403] tveeprom 7-0050: Hauppauge model 72301, rev B3F0, serial# 6141449
[   22.622406] tveeprom 7-0050: MAC address is 00:0d:fe:5d:b6:09
[   22.622409] tveeprom 7-0050: tuner model is Xceive XC5000 (idx 150, type 76)
[   22.622411] tveeprom 7-0050: TV standards NTSC(M) ATSC/DVB Digital (eeprom 0x88)
[   22.622413] tveeprom 7-0050: audio processor is AU8522 (idx 44)
[   22.622415] tveeprom 7-0050: decoder processor is AU8522 (idx 42)
[   22.622418] tveeprom 7-0050: has no radio, has IR receiver, has no IR transmitter
[   22.622419] hauppauge_eeprom: hauppauge eeprom: model=72301
[   22.627198] au8522 7-0047: creating new instance
[   22.627200] au8522_decoder creating new instance...
[   22.633968] tuner 7-0061: Tuner -1 found with type(s) Radio TV.
[   22.636532] xc5000 7-0061: creating new instance
[   22.641400] xc5000: Successfully identified at address 0x61
[   22.641402] xc5000: Firmware has not been loaded previously
[   23.727876] au8522 7-0047: attaching existing instance
[   23.737650] xc5000 7-0061: attaching existing instance
[   23.742522] xc5000: Successfully identified at address 0x61
[   23.742524] xc5000: Firmware has not been loaded previously
[   23.742527] DVB: registering new adapter (au0828)
[   23.742533] usb 2-2: DVB: registering adapter 0 frontend 0 (Auvitek AU8522 QAM/8VSB Frontend)...
[   23.745096] Registered device AU0828 [Hauppauge HVR850]
[   23.745876] usbcore: registered new interface driver au0828
[   23.934275] usbcore: registered new interface driver snd-usb-audio

---

### Post by jeff116 on 2015-03-09
Actually just got it to work in VLC.  However, there is video, but no audio...  Anyone have suggestions?

---

