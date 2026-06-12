---
title: "Recording from usb turntable"
date: 2022-06-19
forum: Multimedia Software
---

### Post by hornetster on 2022-06-19
Ubuntu 22.04, 8gb ram, Dell E6510 laptop.
Sony PS-LX310BT turntable.
When I connect the turntable, dmesg gives:
```
[ 5210.817568] usb 2-1.2: new full-speed USB device number 30 using ehci-pci
[ 5210.930285] usb 2-1.2: New USB device found, idVendor=08bb, idProduct=29c0, bcdDevice= 1.00
[ 5210.930294] usb 2-1.2: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[ 5210.930297] usb 2-1.2: Product: USB AUDIO  CODEC
[ 5210.930299] usb 2-1.2: Manufacturer: BurrBrown from Texas Instruments
[ 5210.945896] input: BurrBrown from Texas Instruments USB AUDIO  CODEC as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.2/2-1.2:1.3/0003:08BB:29C0.0003/input/input22
[ 5211.006161] hid-generic 0003:08BB:29C0.0003: input,hidraw1: USB HID v1.00 Device [BurrBrown from Texas Instruments USB AUDIO  CODEC] on usb-0000:00:1d.0-1.2/input3
[ 5211.672411] usb 2-1.2: USB disconnect, device number 30
john@Bunt-E6510:~$ 

```

but I get no options to select a different device other than the local audio card mic... Pulse Volume Control sees nothing new..
Audacity also sees nothing else.
Where am I going wrong??
Thanks.

---

