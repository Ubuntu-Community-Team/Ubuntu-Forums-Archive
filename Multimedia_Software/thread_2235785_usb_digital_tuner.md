---
title: "usb digital tuner"
date: 2014-07-22
forum: Multimedia Software
---

### Post by coral3 on 2014-07-22
hi, I have an avertv twinstar, I have the firmware for it in /lib/firmware but when I plug it in dmesg reports this:

[ 1820.312206] usb 2-1.2.1.1: New USB device found, idVendor=07ca, idProduct=0825
[ 1820.312218] usb 2-1.2.1.1: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[ 1820.312224] usb 2-1.2.1.1: Product: A825
[ 1820.312229] usb 2-1.2.1.1: Manufacturer: AVerMedia TECHNOLOGIES, Inc.
[ 1820.312234] usb 2-1.2.1.1: SerialNumber: 0000000000000
[ 1820.315579] usb 2-1.2.1.1: dvb_usb_af9035: prechip_version=00 chip_version=03 chip_type=3802
[ 1820.316048] usb 2-1.2.1.1: dvb_usb_v2: found a 'AVerMedia Twinstar (A825)' in cold state
[ 1820.316097] usb 2-1.2.1.1: Direct firmware load failed with error -2
[ 1820.316103] usb 2-1.2.1.1: Falling back to user helper
[ 1820.319191] usb 2-1.2.1.1: dvb_usb_v2: Did not find the firmware file 'dvb-usb-af9035-02.fw'. Please see linux/Documentation/dvb/ for more details on firmware-problems. Status -2
[ 1820.319217] dvb_usb_af9035: probe of 2-1.2.1.1:1.0 failed with error -2
[ 1820.320701] usb 2-1.2.1.4: USB disconnect, device number 13
[ 1820.541138] usb 2-1.2.1.4: new low-speed USB device number 16 using ehci-pci
[ 1820.637975] usb 2-1.2.1.4: New USB device found, idVendor=0c45, idProduct=7401
[ 1820.637987] usb 2-1.2.1.4: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[ 1820.637994] usb 2-1.2.1.4: Product: USB Device
[ 1820.637998] usb 2-1.2.1.4: Manufacturer: SONiX

what am I missing?

---

### Post by Bucky Ball on 2014-07-23
*Thread moved to **Multimedia & Video**.*

This:

```
[ 1820.316097] usb 2-1.2.1.1: Direct firmware load failed with error -2
[ 1820.316103] usb 2-1.2.1.1: Falling back to user helper
[ 1820.319191] usb 2-1.2.1.1: dvb_usb_v2: Did not find the firmware file 'dvb-usb-af9035-02.fw'. Please see linux/Documentation/dvb/ for more details on firmware-problems. Status -2
[ 1820.319217] dvb_usb_af9035: probe of 2-1.2.1.1:1.0 failed with error -2
```

Not finding the firmware. Curious to how you installed this. Where did you get the driver from and this firmware?

---

### Post by coral3 on 2014-07-23
nevermind, I found this and it did the trick

[http://linuxtv.org/wiki/index.php/TerraTec_Cinergy_T_Stick#Method_Z](http://linuxtv.org/wiki/index.php/TerraTec_Cinergy_T_Stick#Method_Z)

working perfect now thanks :-)

---

