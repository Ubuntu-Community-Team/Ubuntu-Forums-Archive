---
title: "Openvpn routing issue?"
date: 2009-01-15
forum: Networking &amp; Wireless
---

### Post by Fick3r on 2009-01-15
I am hoping that someone here can help me. I am a complete *nix n00b, that has taken a leap of faith and dumped windoze for good. So, far everything is working out well for me, apart from openvpn.

I have an openvpn server on an NSLU2 that I can connect to without a problem from an XP client. When I try to connect from Linux (Intrepid) I get connected to the server, but I cannot connect to the intertubes (all net traffic should be routed across the tunnel) as I can from an XP client. I can connect to the openvpn server (by it's virtual IP) but nothing else. I believe I have an issue with routing, but don't know how to resolve it.

Before starting VPN route -n gives:

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
94.xxx.xxx.xx   10.33.66.1      255.255.255.255 UGH   0      0        0 wlan0
10.33.66.0      0.0.0.0         255.255.255.0   U     2      0        0 wlan0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlan0
0.0.0.0         10.33.66.1      0.0.0.0         UG    0      0        0 wlan0

After starting VPN route -n gives:

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
10.8.0.5        0.0.0.0         255.255.255.255 UH    0      0        0 tun0
94.xxx.xxx.xx   10.33.66.1      255.255.255.255 UGH   0      0        0 wlan0
10.33.66.0      10.8.0.5        255.255.255.0   UG    0      0        0 tun0
10.33.66.0      0.0.0.0         255.255.255.0   U     2      0        0 wlan0
10.8.0.0        10.8.0.5        255.255.255.0   UG    0      0        0 tun0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlan0
0.0.0.0         10.8.0.5        128.0.0.0       UG    0      0        0 tun0
128.0.0.0       10.8.0.5        128.0.0.0       UG    0      0        0 tun0
0.0.0.0         10.33.66.1      0.0.0.0         UG    0      0        0 wlan0

10.8.0.x = adresses handed out by the openvpn server.
10.33.66.x = my LAN, with my gateway/router at 10.33.66.1

What have I missed? I am sure that it is blindingly obvious to someone here. Any words of wisdom gratefully received. I shall post my configs and log in a follow-up post, if anyone thinks they will be a help.

TIA.

---

