---
title: "No network with upgrade on Asus EEE900"
date: 2013-05-26
forum: Networking &amp; Wireless
---

### Post by Brian_G_M on 2013-05-26
Hi, I have just upgraded my 5 year old Asus EEE900 netbook to 12.04 LTS. There were a few error messages about losing configuration settings on the way through the upgrade, now I can't access any wifi or cable network. When I go into Network Connections there is nothing showing. When I boot up I see messages "Waiting for network configuration" Then waiting up to 60 seconds more for network configuration. Then it says "Booting system without full network configuration". How do I get my network connections to work? 
Thanks,
Brian

---

### Post by praseodym on 2013-05-26
Open this file:
```

gksu gedit /etc/network/interfaces
```
and remove anything except
```

auto lo
iface lo inet loopback
```and reboot.

---

### Post by Brian_G_M on 2013-05-26
Hey, you're a wizard. Fantastic, thanks, it all works.

---

