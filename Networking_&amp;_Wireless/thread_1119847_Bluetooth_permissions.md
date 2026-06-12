---
title: "Bluetooth permissions"
date: 2009-04-08
forum: Networking &amp; Wireless
---

### Post by crimson on 2009-04-08
Hi all. I'm having some difficulties with accessing Bluetooth devices under Ubuntu Intrepid (8.10). It appears that only root is allowed to make connections with BlueZ. For example,

```
$ hcitool cc 00:24:xx:xx:xx:xx
Can't create connection: Operation not permitted
$ hcitool info 00:24:xx:xx:xx:xx
Requesting information ...
Can't create connection: Operation not permitted
```

Whereas,

```
$ sudo hcitool info 00:24:xx:xx:xx:xx
```

works fine. Likewise, the Java Bluetooth code I've been working on only works if run as root, which is undesirable.

Now, I can see why some restrictions on access to the Bluetooth hardware would be necessary, but in other cases there is typically a group one can assign users to (e.g. scanner) to give them access to some hardware. However, I've been searching and can't find anything similar for Bluetooth.

Additionally, pairing using the GNOME Bluetooth applet doesn't seem to require root permission. (I wasn't prompted to enter a password.)

Am I missing something? Or is this the way it's supposed to work? And if the latter, is there a way to give permissions to a particular user to let them use the Bluetooth interface? It's a USB dongle, btw, if that makes any difference.

Any help would be much appreciated. Thanks!

---

