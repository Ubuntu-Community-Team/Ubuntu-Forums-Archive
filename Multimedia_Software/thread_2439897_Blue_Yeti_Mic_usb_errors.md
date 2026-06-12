---
title: "Blue Yeti Mic usb errors"
date: 2020-04-02
forum: Multimedia Software
---

### Post by colin.williams.seattle on 2020-04-02
plug in mic to any usb port on lenovo w530 using 4.19.0-4-amd64. device does not show up in lsub, arecord -l, pavucontrol, etc.

then from dmesg:

 [1283.964808] usb 1-1.2: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[ 1283.964810] usb 1-1.2: Product: Yeti Stereo Microphone
[ 1283.964812] usb 1-1.2: Manufacturer: Blue Microphones
[ 1284.080671] usb 1-1.3: new low-speed USB device number 83 using ehci-pci
[ 1284.784678] usb 1-1.3: device descriptor read/64, error -32
[ 1285.180674] usb 1-1.3: device descriptor read/64, error -32
[ 1285.992682] usb 1-1.3: new low-speed USB device number 84 using ehci-pci
[ 1286.696672] usb 1-1.3: device descriptor read/64, error -32
[ 1287.092695] usb 1-1.3: device descriptor read/64, error -32
[ 1287.200804] usb 1-1-port3: attempt power cycle
[ 1287.804662] usb 1-1.3: new low-speed USB device number 85 using ehci-pci
[ 1288.220686] usb 1-1.3: device not accepting address 85, error -32
[ 1288.508685] usb 1-1.3: new low-speed USB device number 86 using ehci-pci
[ 1288.924690] usb 1-1.3: device not accepting address 86, error -32
[ 1288.924916] usb 1-1-port3: unable to enumerate USB device
[ 1288.925391] usb 1-1.2: USB disconnect, device number 82
[ 1289.308736] usb 1-1.3: new low-speed USB device number 87 using ehci-pci
[ 1289.596727] usb 1-1.3: device descriptor read/64, error -32
[ 1289.992635] usb 1-1.3: device descriptor read/64, error -32
[ 1290.596683] usb 1-1.3: new low-speed USB device number 88 using ehci-pci
[ 1290.888718] usb 1-1.3: device descriptor read/64, error -32
[ 1291.284673] usb 1-1.3: device descriptor read/64, error -32
[ 1291.392928] usb 1-1-port3: attempt power cycle
[ 1291.996623] usb 1-1.3: new low-speed USB device number 89 using ehci-pci
[ 1292.412691] usb 1-1.3: device not accepting address 89, error -32
[ 1292.700701] usb 1-1.3: new low-speed USB device number 90 using ehci-pci
[ 1293.116718] usb 1-1.3: device not accepting address 90, error -32
[ 1293.116867] usb 1-1-port3: unable to enumerate USB device
[ 1293.340705] usb 1-1.3: new low-speed USB device number 91 using ehci-pci
[ 1293.628679] usb 1-1.3: device descriptor read/64, error -32
[ 1294.028658] usb 1-1.3: device descriptor read/64, error -32
[ 1294.428695] usb 1-1.3: new low-speed USB device number 92 using ehci-pci
[ 1294.716598] usb 1-1.3: device descriptor read/64, error -32
[ 1295.112692] usb 1-1.3: device descriptor read/64, error -32
[ 1295.220836] usb 1-1-port3: attempt power cycle

Could it be related to [https://github.com/torvalds/linux/blame/ac438771ccb4479528594c7e19f2c39cf1814a86/sound/usb/stream.c#L816](https://github.com/torvalds/linux/blame/ac438771ccb4479528594c7e19f2c39cf1814a86/sound/usb/stream.c#L816) ?

Finally a related: [https://askubuntu.com/questions/1027188/external-yeti-michrophone-not-detected-on-ubuntu-18-04](https://askubuntu.com/questions/1027188/external-yeti-michrophone-not-detected-on-ubuntu-18-04)

---

### Post by colin.williams.seattle on 2020-04-04
I tried another usb cable and the microphone is working fine. Lesson learned...

---

### Post by mörgæs on 2020-04-05
Good, please use Thread Tools for marking the thread solved.

---

