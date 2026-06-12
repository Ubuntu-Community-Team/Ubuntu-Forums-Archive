---
title: "Unable to successfully use bluetooth dongle"
date: 2010-08-14
forum: Networking &amp; Wireless
---

### Post by bgugi on 2010-08-14
hello, all. I recently purchased an inexpensive bluetooth dongle for my laptop running lucid 64-bit. the device, however, doesn't seem to want to work in ubuntu. most functions (everything but turning the device OFF) fail, causing gui windows to hang, and i mostly receive messages relating to the device timing out.



before you ask, it is not the device: the dongle works flawlessly in windows 7 after being autodetected and autoinstalled. i attempted to boot from the lucid cd, and the problem persisted.


```
bgugi@OPERATOR:~$ hciconfig
hci0:	Type: USB
	BD Address: 00:1F:81:00:01:1C ACL MTU: 1021:4 SCO MTU: 180:1
	DOWN 
	RX bytes:330 acl:0 sco:0 events:8 errors:0
	TX bytes:24 acl:0 sco:0 commands:14 errors:6

bgugi@OPERATOR:~$ sudo hciconfig hci0 up
Can't init device hci0: Connection timed out (110)
bgugi@OPERATOR:~$ hcitool dev
Devices:
bgugi@OPERATOR:~$ sudo hciconfig hci0 reset
Can't init device hci0: Connection timed out (110)
bgugi@OPERATOR:~$ hcitool hci0 scan
(blank)
```

lsusb snippet
```
Bus 003 Device 002: ID 0a12:0001 Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode)
```

---

### Post by bgugi on 2010-08-15
bump.

---

### Post by bgugi on 2010-08-19
ghetto-solved: by repeatedly plugging in and removing device, it can be forced to work... eventually...

---

### Post by pricetech on 2010-08-20
Sadly, I don't have a solution but rather a question.  What brand / model is your dongle ??  I'm looking to purchase one and at least I'll know what to stay away from.

Thanks

---

### Post by bgugi on 2010-08-22
[http://www.dealextreme.com/details.dx/sku.11866](http://www.dealextreme.com/details.dx/sku.11866)

---

