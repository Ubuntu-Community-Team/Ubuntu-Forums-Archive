---
title: "Multiple loopback adapters (lo:*) not coming up on reboot"
date: 2011-12-16
forum: Networking &amp; Wireless
---

### Post by DPJB on 2011-12-16
Hi All,

I have a setup with multiple loopback adapters on 64 bit 10.04 boxes. /etc/network/interfaces snippet:


```
# The loopback network interface
auto lo
iface lo inet loopback

# Non arping interface for monitoring
auto lo:1
iface lo:1 inet static
        address 95.129.xxx.xxx
        netmask 255.255.255.255
        pre-up sysctl -p > /dev/null
```


This all works fine, but I have to manually do a 'ifup lo:1' after each reboot. I could fix this with a little script, but is there a reason why this interface does not come up on boot?

Cheers,

Dirk

---

