---
title: "Network manager connection does not allow incoming traffic on eht0"
date: 2012-01-12
forum: Networking &amp; Wireless
---

### Post by scuba on 2012-01-12
I use an openvpn connection in network manager on a server behind a router. It all works well in and out on interface tap0 as the default connection. It does also work well connecting to and from the local network (192.168.0.0).

My problem is that connecting from the outside of the router on the local interface (not the vpn tunnel), the connection does not work (http or ssh). And yes the ports are forwarded.

I'd guess that some routing is needed but I cannot figure out how, any tip would be appreciated.

```
$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         X.X.X.X         0.0.0.0         UG    0      0        0 tap0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth1
X.X.X.X         0.0.0.0         255.255.255.0   U     0      0        0 tap0
X.X.X.X         192.168.0.1     255.255.255.255 UGH   0      0        0 eth1
192.168.0.0     0.0.0.0         255.255.255.0   U     1      0        0 eth1
```

X.X.X.X -> VPN adresses

---

### Post by jonobr on 2012-01-12
Hello

If there is an LZO compression setting in the NM applet, could you try to toggle that to see if helps.

---

### Post by scuba on 2012-01-12
> **jonobr said:**
> Hello

If there is an LZO compression setting in the NM applet, could you try to toggle that to see if helps.

Thanks for the reply. LZO compression is toggled (on), and as I understand it is a requirement for my provider.

On a other note i don't really se what the vpn compression has to do with the local network (I mean even if it did, the internal network still works)?

---

### Post by scuba on 2012-01-13
Solved by routing from host external IP through the local gateway. Will report a bug about it since it should be added automaticly when using a VPN.

```
$ route add -host Y.Y.Y.Y gw 192.168.0.1 dev eth1
```

---

### Post by jonobr on 2012-01-13
Odd, I agree, it should be added automatically,

thanks for posting the solution back

---

