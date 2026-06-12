---
title: "Network scanning possible?"
date: 2010-12-10
forum: Networking &amp; Wireless
---

### Post by carfield on 2010-12-10
I am using wireless router WL-520GU, it have a USB port connected to a printer + scanner: "HP Photosmart C4400"

I can print to this printer by pointing CUPS to use network printer at socket://192.168.1.1:9100, can I also get the scanning image from the scanner?

I've installed xsane and sane. And tried to run "xsane hpaio:/net/photosmart_c4400_series?ip=192.168.1.1" according to this page: [https://answers.launchpad.net/hplip/+question/28585](https://answers.launchpad.net/hplip/+question/28585)

As I mentioned in there, the error I get is actually 

Dec 11 02:58:07 (none) xsane: scan/sane/io.c 53: dBus Connection Error (Failed to connect to socket /var/run/dbus/system_bus_socket: No such file or directory)! 
Dec 11 02:58:10 (none) xsane: io/hpmud/jd.c 88: unable to read device-id 

How can I generate /var/run/dbus/system_bus_socket ??

---

