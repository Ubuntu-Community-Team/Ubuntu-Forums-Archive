---
title: "VPN disconnected: resolve.conf not refreshed"
date: 2012-06-05
forum: Networking &amp; Wireless
---

### Post by cwall on 2012-06-05
I connect to VPN using vpnc. When VPN disconnects, either via time out or the session limit is reached, VPN is terminated, but resolve.conf continues to contain references to my VPN network.

resolv.conf before VPN is connected:

```
nameserver 127.0.0.1
search mylocalnetwork
```

resolv.conf after VPN is connected and remains once VPN is lost:

```
nameserver X.X.X.X
nameserver X.X.X.Z
nameserver 127.0.0.1
search internal.mycompany.com mylocalnetwork
```

In 10.04, when VPN lost, I'd run this script to refresh resolve.conf:
```
7$ cat bin/refreshResolvconf.sh 
#!/bin/bash
#if [ -e /etc/resolvconf/run/interface/tun0 -a "`pidof vpnc`" == "" ]; then /sbin/resolvconf -d tun0; fi
if [ -e /etc/resolvconf/run/interface/tun0 -a "`pidof vpnc`" == "" ]
then 
/sbin/resolvconf -d tun0;
echo "Refreshed resolv.conf"
fi
```

But, resolveconf changed in 12.04 changed, so this script is no longer applicable.

To resolve, I manually edit resolve.conf or turn off/on my connection via "gnome-control-center network".

Anyone else have the same problem? How can resolv.conf be updated post-VPN disconnect?

---

### Post by zahltag on 2012-08-09
same issue here .... bump

---

