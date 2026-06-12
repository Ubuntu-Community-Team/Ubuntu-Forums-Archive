---
title: "Wireless decided to stop working"
date: 2011-06-01
forum: Networking &amp; Wireless
---

### Post by CrazeDIzzleD on 2011-06-01
I assigned a static IP to my laptop running Ubuntu 10.04 64bit, and all was working fine. Then I restarted to do something in Windows and when I came back, the wireless didn't work. And my network-manager icon disappeared from my panel.

I changed it back to DHCP, but it still didn't work. I tried removing the connection and adding a new, and that didn't work either. Running a iwlist wlan0 scan shows my router, but iwconfig says access point: not-associated.

lshw -C network shows the wireless card with no problems (which appears to be an Atheros, by the way) so drivers appear to be okay.

Also, running ifup wlan0 gives me "Ignoring unknown interface wlan0=wlan0"

So what gives, how can I fix this?

---

### Post by CrazeDIzzleD on 2011-06-02
Bump.

---

