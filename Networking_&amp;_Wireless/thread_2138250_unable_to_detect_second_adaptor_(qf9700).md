---
title: "unable to detect second adaptor (qf9700)"
date: 2013-04-23
forum: Networking &amp; Wireless
---

### Post by benobiwan on 2013-04-23
Hi Community,

I bought multiple KY-RD9700 (qf9700 driver is loaded). However, i am not able to insert more than 1 similar adaptor, the interesting thing is that it is assigning the same mac address to the second adaptor, and even in dmesg, i saw eth3 being registered, i do not find the interface using ifconfig. Please help.

beno@beno-laptop:/etc$ dmesg | grep 9700
[  962.149417] eth2: register 'qf9700' at usb-0000:00:1d.0-1.3.2, QF9700 USB Ethernet, 00:e0:4c:53:44:58
[  962.149452] usbcore: registered new interface driver qf9700
[ 1108.246214] eth2: unregister 'qf9700' usb-0000:00:1d.0-1.3.2, QF9700 USB Ethernet
[ 1111.614060] eth2: register 'qf9700' at usb-0000:00:1d.0-1.3.2, QF9700 USB Ethernet, 00:e0:4c:53:44:58
[ 1277.850406] eth3: register 'qf9700' at usb-0000:00:1d.0-1.3.1, QF9700 USB Ethernet, 00:e0:4c:53:44:58

---

