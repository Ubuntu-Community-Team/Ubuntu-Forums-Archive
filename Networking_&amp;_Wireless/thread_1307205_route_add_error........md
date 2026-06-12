---
title: "route add error......."
date: 2009-10-30
forum: Networking &amp; Wireless
---

### Post by soumajitpal on 2009-10-30
[I]sudo route add -net 10.0.0.20 netmask 255.255.255.255 gw 10.0.0.100 dev tun0
SIOCADDRT: No such process
[/I]

i am getting such an error when i try to set a gateway to my tunnel ip in my server side vpn.....

any help is appriciated...

---

### Post by Iowan on 2009-10-31
With that netmask, would it still be considered a net?
(would -host work?)

---

### Post by koenn on 2009-10-31
> **soumajitpal said:**
> [I]sudo route add -net 10.0.0.20 netmask 255.255.255.255 gw 10.0.0.100 dev tun0
SIOCADDRT: No such process
[/I]

i am getting such an error when i try to set a gateway to my tunnel ip in my server side vpn.....

any help is appriciated...
This error usually occurs when the device (tun0 in this case) doesn't exist.
Is your tunnel up, and did openvpn create a tun0 device ?

---

