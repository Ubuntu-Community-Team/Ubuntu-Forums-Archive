---
title: "WICD 1.7.0 &quot;Bad Passphrase&quot; Error"
date: 2011-08-05
forum: Networking &amp; Wireless
---

### Post by funguygordy on 2011-08-05
I am trying to set everything manually, from the terminal.  I also do not want to use network-manager, so it has been uninstalled and purged.  My wireless PCI is recognized as ra0, so upon login I use
```

ifconfig ra0 up

```
to turn the adapter on.  I have set my nameserver in /etc/resolv.conf to 192.168.0.1.  I have not tried using a static ip, as I am not sure what circumstances call for it.  When I launch WICD I can scan for networks, although there is a large fluctuation in signal strength.  IE I am a room over from my router, and each time I hit scan I get back anywhere from 15%-98% signal.  I am using a WPA passkey, and am absolutely sure that I am entering it correctly.  However, when I try to connect it says I have a "Bad Passphrase."  

From what I have seen some people have gotten it to work by downgrading to 1.6, but this is not an option for me as I am not wire connected.  If it comes down to it I can be, but in any event there must be a way of fixing this without downgrading.

---

