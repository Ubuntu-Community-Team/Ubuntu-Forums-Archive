---
title: "HUAWEI E1630 HSDPA USB Modem drops connectivity"
date: 2011-01-17
forum: Networking &amp; Wireless
---

### Post by sanjayak on 2011-01-17
Hi All,

I recently got a HUAWEI E1630 HSDPA USB Modem and it was working fine until recently. Recently it starts to drop the connection and in /var/log/messages I can see a pppd error "Protocol-Reject for unsupported protocol xxxx". The protocol number is random. Only way to resume is to unplug and replug the device. The happens very frequently and hence the device is not usable.

To isolate the service provider end, I use the same SIM on a PROLINK HSDPA USB Modem and it works fine. Also I use a different SIM from another service provider in this device and the issue still exists.

I am on Kubuntu 10.10 with all the updates to date. Should I report a bug?

Appreciate any support to rectify this.

---

### Post by sanjayak on 2011-05-20
The issue is discussed here [http://forum.huawei.com/jive4/thread.jspa?threadID=323666&tstart=0&orderStr=26](http://forum.huawei.com/jive4/thread.jspa?threadID=323666&tstart=0&orderStr=26). A circuit like this ([http://www.acomelectronics.com/GeorgeVita/e170fix_foto.html](http://www.acomelectronics.com/GeorgeVita/e170fix_foto.html)) can be used to fix this issue at hardware level.

However, I just use a cheap USB hub which gave the required power stability and now the USB Modem works fine.

---

