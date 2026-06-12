---
title: "Cisco VPN"
date: 2010-07-10
forum: Networking &amp; Wireless
---

### Post by Ryan2009 on 2010-07-10
Hello

I'm new to Ubuntu.  I would like to connect to my work network through Ubuntu which uses a Cisco VPN IPSec solution.  What is the best way to configure this on 10.4?

Thanks

---

### Post by Steve603z on 2010-07-11
```
sudo apt-get install network-manager-vpnc-gnome
```
right click the network-manager icon in the top panel > edit connections > VPN > add > cisco compatible vpn > create

It's been a while since I've connected Ubuntu to a Cisco VPN, but I remember it took me a little trial and error because some of the wording was different.  But hopefully this helps.

---

