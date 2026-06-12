---
title: "sdptool causes kernel crash in Xubuntu 12.04 Precise Pangolin"
date: 2012-07-27
forum: Networking &amp; Wireless
---

### Post by regexp on 2012-07-27
Hi all!
I've just installed Xubuntu 12.04 Precise Pangolin on my old Asus EeePC 900 and updated it to newest kernel by standart package manager - so it is 3.2.0-27 now.
 
[COLOR=royalblue]uname -a[/COLOR]
[COLOR=royalblue]Linux pulsar 3.2.0-27-generic #43-Ubuntu SMP Fri Jul 6 14:46:35 UTC 2012 i686 i686 i386 GNU/Linux[/COLOR]
 
I have USB Bluetooth adapter, the cheapest one from my local electronics store - [FONT=Arial][SIZE=2]Qumo Bluetooth USB Adapter, ClassII - 25m, V.2.0 + EDR[/SIZE][/FONT]
[IMG]http://caub.ru/images/catalog/gil/1165785.jpg[/IMG]
 
dmesg output related:
[COLOR=royalblue][ 84.468040] usb 3-1: new full-speed USB device number 3 using uhci_hcd[/COLOR]
lsusb output related:
[COLOR=royalblue]Bus 003 Device 003: ID 0a12:0001 Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode)[/COLOR]
 
[COLOR=black]System works fine except kernel crash (see a photo of crash dump screen in attachment to this message ), very easy reproducible by [COLOR=royalblue]sdptool browse[/COLOR] command - 3rd or 4th run of this command causes the kernel crash.
 
Any ideas on this?
Thanks! :-)))
 
[/COLOR]

---

### Post by DieterM75 on 2013-01-24
Exactly same problems here, except it is Ubuntu and with kernel 3.7.
Pairing devices works, but if you try to open a serial connection or transmit a file, the system fails hard.

Device is: 0a12:0001

Also interesting: it sometimes takes some time to get the dongle registered correctly, so that no timeout errors occur in dmesg output.

```

[  133.402031] Bluetooth: hci0 command 0x0c12 tx timeout
[  134.403230] Bluetooth: hci0 command 0x0c01 tx timeout
[  135.404337] Bluetooth: hci0 command 0x1002 tx timeout
[  136.405443] Bluetooth: hci0 command 0x0c45 tx timeout
[  137.406596] Bluetooth: hci0 command 0x1004 tx timeout

```

---

