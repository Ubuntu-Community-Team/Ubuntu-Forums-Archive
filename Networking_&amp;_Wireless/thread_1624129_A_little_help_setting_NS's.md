---
title: "A little help setting NS's"
date: 2010-11-17
forum: Networking &amp; Wireless
---

### Post by miki86 on 2010-11-17
Hi everybody.
Im new Ubuntu user and i could use a little help with setting my nameservers on my new vps which i have reinstalled at least three times today :).

I've been busting my head all day with this.
As soon as i change /etc/resolv.conf and put my ip addresses i cant ping anything externaly, and my domain still doesn't work.

And there is one more thing that's been bothering me, im not an expert in networking but the gateway should actually be server address right?

```
root@server:/# route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.0.2.1       0.0.0.0         255.255.255.255 UH    0      0        0 venet0
0.0.0.0         192.0.2.1       0.0.0.0         UG    0      0        0 venet0
```

Thanks in advance.

---

### Post by uncaspi on 2010-11-18
The gw is the router address right.

---

