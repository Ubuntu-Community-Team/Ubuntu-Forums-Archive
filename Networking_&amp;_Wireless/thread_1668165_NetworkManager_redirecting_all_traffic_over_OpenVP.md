---
title: "NetworkManager redirecting all traffic over OpenVPN..."
date: 2011-01-15
forum: Networking &amp; Wireless
---

### Post by ownaginatious on 2011-01-15
So I finally got OpenVPN working - and so far, everything works as I would like.

I got it set up in the NetworkManager applet (imported the client.ovpn), but when I connect it sends ALL my traffic through the VPN. I would prefer all accesses to the internet go over my normal default gateway, rather then all the way through to the VPN's default gateway.

When I connect through the command line:

```
openvpn --config client.ovpn
```

I don't have this problem, and accesses to the internet still go over my default gateway on the client side.

Is there a way to make NetworkManager stop forcing absolutely everything over the VPN tunnel? I would prefer to keep using it for this if possible... it keeps the whole process very clean.

Thanks!

EDIT:

Here is my routing table before connecting:

```

Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
3.3.3.0         0.0.0.0         255.255.255.0   U     1      0        0 eth0
0.0.0.0         3.3.3.1         0.0.0.0         UG    0      0        0 eth0

```

Here is my routing table after connecting:

```

Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
10.8.0.5        0.0.0.0         255.255.255.255 UH    0      0        0 tun0
76.10.136.84    3.3.3.1         255.255.255.255 UGH   0      0        0 eth0
10.0.1.0        10.8.0.5        255.255.255.0   UG    0      0        0 tun0
10.8.0.0        10.8.0.5        255.255.255.0   UG    0      0        0 tun0
3.3.3.0         0.0.0.0         255.255.255.0   U     1      0        0 eth0
0.0.0.0         10.8.0.5        0.0.0.0         UG    0      0        0 tun0

```

---

### Post by ownaginatious on 2011-01-16
Ah, figured it out. It turns out it's a 'feature' of NetworkManager.

For anyone reading this in the future, the way to fix it is:

Click NetworkManager applet icon > VPN Connections > Configure VPN... > select VPN network > Edit > IPv4 Settings > Routes... > Check 'Use this connection only for resources on its network'

That will prevent the computer from throwing everything over the VPN line and only connections that must use it.

---

