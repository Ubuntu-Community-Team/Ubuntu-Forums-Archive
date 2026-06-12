---
title: "Preventing NetworkManager from Rogue dhcp servers"
date: 2012-06-03
forum: Networking &amp; Wireless
---

### Post by debsankha on 2012-06-03
Hello,
In the wireless network of my building, someone has set up a rogue dhcp server. The real network has internal ip addresses in the subnet 10.0.0.0/24. But the rogue server hands out ip's in 192.168.0.0/16 subnet and bogus values for gateways etc.

I have managed to connect my laptop via ethernet by stopping NetworkManager and using dhclient from command line by adding:
```

reject 192.168.0.0/26;

```
to my dhclient.conf

However, I sometimes prefer to use the wlan, and I was unable to do so due to some trouble with wpa_supplicant. I would rather wish to have the problem solved without abandoning Networkmanager. Any ideas?

---

