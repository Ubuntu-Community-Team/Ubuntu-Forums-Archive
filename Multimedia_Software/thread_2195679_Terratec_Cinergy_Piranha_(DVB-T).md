---
title: "Terratec Cinergy Piranha (DVB-T)"
date: 2013-12-25
forum: Multimedia Software
---

### Post by epek on 2013-12-25
Hello!
Yet another Stick...

Bus 003 Device 008: ID 187f:0010 Siano Mobile Silicon Stallar Board
Typo in 'Stellar'? Where shall I report this to?

[ 4638.922193] usb 3-4: new full-speed USB device number 9 using xhci_hcd
[ 4638.939285] usb 3-4: New USB device found, idVendor=187f, idProduct=0010
[ 4638.939293] usb 3-4: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[ 4638.939296] usb 3-4: Product: SMS 1000
[ 4638.939299] usb 3-4: Manufacturer: Siano
[ 4638.940128] smsusb_probe: line: 486: rom interface 0 is not used
[ 4638.940428] smsusb_probe: line: 455: interface number is 0 expecting 1

It seems nothing changed since:
[http://ubuntuforums.org/archive/index.php/t-1309831.html](http://ubuntuforums.org/archive/index.php/t-1309831.html)

Suggestions?

Thanks!

Edit:
[https://bugzilla.kernel.org/show_bug.cgi?id=60645](https://bugzilla.kernel.org/show_bug.cgi?id=60645)
It seems that this error was fixed in kernel 3.10, but: I am running 3.11.0-12-generic. Could there be another regression?

---

