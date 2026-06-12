---
title: "VPN web traffic client routing trouble."
date: 2009-08-14
forum: Networking &amp; Wireless
---

### Post by T3kG33k on 2009-08-14
I'm having some trouble trying to figure out what's going on with my openvpn routing.  When I enter the route command i receive this:

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
T3kN37          192.168.5.5     255.255.255.255 UGH   0      0        0 tun0
192.168.5.5     *               255.255.255.255 UH    0      0        0 tun0
c-69-180-153-91 10.42.1.1       255.255.255.255 UGH   0      0        0 eth0
10.22.32.0      *               255.255.255.0   U     2      0        0 eth1
192.168.5.0     192.168.5.5     255.255.255.0   UG    0      0        0 tun0
10.42.0.0       *               255.255.224.0   U     1      0        0 eth0
link-local      *               255.255.0.0     U     1000   0        0 eth1
default         10.42.1.1       0.0.0.0         UG    0      0        0 eth0

This is while I'm connected to my openvpn which does authenticate and it does work.

However,  When browsing the internet on my laptop websites like imgur.com are still being filtered out.  My tunnel is encrypted and I'm connecting via wired.  i'm also using firefox.

Does anyone have ideas why my http traffice doesn't seem to be re-routed to through my vpn to my DNS at home. :confused:

EDIT:  I'm testing this in my lab with a small filter that I've built.  I'm trying to better my understanding of OpenVPN and any assitance would be greatly appreciated.

---

### Post by T3kG33k on 2009-08-17
](*,)]bump

---

