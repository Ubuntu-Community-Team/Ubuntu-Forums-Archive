---
title: "Elgato EyeTV DTT Deluxe V2 in Ubuntu?"
date: 2009-12-04
forum: Multimedia Software
---

### Post by night-wing on 2009-12-04
Hello.

I got a dvb-t usb-stick "elgato eyetv dtt deluxe v2" as a birthday gift. Sadly, I found nothing about a hint to make this stick work in linux. Drivers and Programs are only for windows and mac os x. Can somebody give me a hint how to make this work in ubuntu?
I've tried all versions including karmic.

Regards
nightwing

---

### Post by night-wing on 2009-12-05
Maybe this helps:

lsusb gives

Bus 006 Device 010: ID 0fd9:002c
Bus 006 Device 009: ID 093a:2510 Pixart Imaging, Inc.
Bus 006 Device 005: ID 04f9:0206 Brother Industries, Ltd
Bus 006 Device 004: ID 13fd:1240 Initio Corporation
Bus 006 Device 003: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 006 Device 002: ID 12d1:1003 Huawei Technologies Co., Ltd. E220 HSDPA Modem / E270 HSDPA/HSUPA Modem
Bus 006 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

Its the first one. But me-tv doesn't find it anyway.

lsusb -v -d 0fd9:002c
Bus 006 Device 011: ID 0fd9:002c
Device Descriptor:
bLength 18
bDescriptorType 1
bcdUSB 2.00
bDeviceClass 255 Vendor Specific Class
bDeviceSubClass 255 Vendor Specific Subclass
bDeviceProtocol 255 Vendor Specific Protocol
bMaxPacketSize0 64
idVendor 0x0fd9
idProduct 0x002c
bcdDevice 1.00
iManufacturer 1 Elgato
iProduct 2 EyeTV DTT Dlx
iSerial 3 000090904020061
bNumConfigurations 1
Configuration Descriptor:
bLength 9
bDescriptorType 2
wTotalLength 39
bNumInterfaces 1
bConfigurationValue 1
iConfiguration 0
bmAttributes 0x80
(Bus Powered)
MaxPower 300mA
Interface Descriptor:
bLength 9
bDescriptorType 4
bInterfaceNumber 0
bAlternateSetting 0
bNumEndpoints 3
bInterfaceClass 255 Vendor Specific Class
bInterfaceSubClass 255 Vendor Specific Subclass
bInterfaceProtocol 255 Vendor Specific Protocol
iInterface 0
Endpoint Descriptor:
bLength 7
bDescriptorType 5
bEndpointAddress 0x01 EP 1 OUT
bmAttributes 2
Transfer Type Bulk
Synch Type None
Usage Type Data
wMaxPacketSize 0x0200 1x 512 bytes
bInterval 0
Endpoint Descriptor:
bLength 7
bDescriptorType 5
bEndpointAddress 0x82 EP 2 IN
bmAttributes 2
Transfer Type Bulk
Synch Type None
Usage Type Data
wMaxPacketSize 0x0200 1x 512 bytes
bInterval 0
Endpoint Descriptor:
bLength 7
bDescriptorType 5
bEndpointAddress 0x83 EP 3 IN
bmAttributes 2
Transfer Type Bulk
Synch Type None
Usage Type Data
wMaxPacketSize 0x0200 1x 512 bytes
bInterval 0
Device Qualifier (for other device speed):
bLength 10
bDescriptorType 6
bcdUSB 2.00
bDeviceClass 255 Vendor Specific Class
bDeviceSubClass 255 Vendor Specific Subclass
bDeviceProtocol 255 Vendor Specific Protocol
bMaxPacketSize0 64
bNumConfigurations 1
cannot read device status, Connection timed out (110)

---

### Post by xc3RnbFO8P on 2009-12-05
Show the output of:
> dmesg

---

### Post by night-wing on 2009-12-05
Hi.

I put it in a "dmesg.txt" and make it an attachment.

---

### Post by xc3RnbFO8P on 2009-12-05
> Bus 006 Device 004: ID 13fd:1240 Initio Corporation
Can you disconnect this and do **dmesg** again, see if it change the output?

---

### Post by night-wing on 2009-12-05
Ok. Did it. But please not, that the elgato dvb-t usb-stick is NOT on the initio USB-Hub but direct on an usb port on the notebook.

---

### Post by xc3RnbFO8P on 2009-12-05
I was hoping for a miracle :)
Is it any change that you can "warm it up" in other OS, Windows?
Then plug it in Ubuntu and do dmesg.

---

### Post by night-wing on 2009-12-05
??? Can you please explain me, what you mean with "warm it up"?

In windows, it works.

---

### Post by xc3RnbFO8P on 2009-12-05
> ??? Can you please explain me, what you mean with "warm it up"?
Just use it in Windows, then disconnect it and plug it in ubuntu and do dmesg.
You can actuality feel it is warm.

---

### Post by night-wing on 2009-12-06
This is not possible, because when I will test it in windows, I will have to restore an system image (by image for linux) and when I did I will have to restore the ubuntu system image. I have no dual boot!

---

### Post by xc3RnbFO8P on 2009-12-06
> sudo modprobe em28xx
> sudo modprobe em28xx-dvb
and do dmesg

---

### Post by night-wing on 2009-12-07
Ok. I did. My new dmesg ist in the attachment.

---

### Post by xc3RnbFO8P on 2009-12-07
Then we try:
> sudo modprobe dvb_core
Last dmesg, you got:
> [  338.895603] Linux video capture interface: v2.00
[  339.260880] em28xx v4l2 driver version 0.1.0 loaded
[  339.261962] usbcore: registered new interface driver em28xx
[  348.088570] Em28xx: Initialized (Em28xx dvb Extension) extension
You need frontend, do (just copy/paste here):
> dmesg | grep dvb
If you have restart the computer:
> sudo modprobe em28xx
sudo modprobe em28xx-dvb
sudo modprobe dvb_core

---

### Post by night-wing on 2009-12-07
Sorry, but this does not change anything.
lsusb still shows no driver beyond the port and me-tv does not recognize any dvb unit.

dmesg grep shows

Em28xx: Initialized (Em28xx dvb Extension) extension

---

### Post by night-wing on 2009-12-08
in linuxtv

[http://www.linuxtv.org/wiki/index.php/Elgato_EyeTV_DTT_deluxe_v2](http://www.linuxtv.org/wiki/index.php/Elgato_EyeTV_DTT_deluxe_v2)

they write, it's unsupported (till now)...

---

