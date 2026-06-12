---
title: "twinhan DVB-T USB 7047 model not detected"
date: 2008-03-27
forum: Multimedia &amp; Video
---

### Post by rgunn on 2008-03-27
having no luck at with this twinhan 7047 usb tuner (DVB-T usb stick ). I cant find many references to it either but it must be fairly close to a 7045 twinhan model ?

Can anyone give me some instructions as to how I might get this working ?

thx

lsusb identiifies it as

Bus 005 Device 002: ID 13d3:3216 IMC Networks
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0
  bDeviceProtocol         0
  bMaxPacketSize0        64
  idVendor           0x13d3 IMC Networks
  idProduct          0x3216
  bcdDevice            1.00
  iManufacturer           1 Generic
  iProduct                2 7047
  iSerial                 3 00000000
  bNumConfigurations      1

---

### Post by rgunn on 2008-03-27
just found out its an unsupported device in v4l as per

[http://www.linuxtv.org/wiki/index.php/DVB-T_USB_Devices#TwinHan.2FAzureWave_AD-TU200_.287047.29_DVB-T](http://www.linuxtv.org/wiki/index.php/DVB-T_USB_Devices#TwinHan.2FAzureWave_AD-TU200_.287047.29_DVB-T)

oh well :-(

---

