---
title: "ICS Sharing (Description enclosed) issue"
date: 2012-04-24
forum: Networking &amp; Wireless
---

### Post by cwwilson721 on 2012-04-24
Running Ubuntu 11.10 64bit
 My cable modem emitted the "mysterious blue smoke" yesterday, and my local ISP won't have another for a week or so.

My Android phone tethers to this desktop fine.

I need to share my tethered connection to the rest of my home LAN, which connects to my desktop via ethernet. The router is a combo ethernet/wifi.

So, it looks like this:

Phone/Internet > usb0 > Desktop > eth1 > WiFi Router > Other devices

Following instructions at [https://help.ubuntu.com/community/Internet/ConnectionSharing](https://help.ubuntu.com/community/Internet/ConnectionSharing) I get no Internet from the network out, but Desktop still can access Internet. 

(Edited /etc/sysctl.conf to use ```
net.ipv4.ip_forward=1
```

Ideas?

---

### Post by cwwilson721 on 2012-04-29
Figured it out, and made this thread to help others:
[http://ubuntuforums.org/showthread.php?p=11886171#post11886171](http://ubuntuforums.org/showthread.php?p=11886171#post11886171)

---

