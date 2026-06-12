---
title: "Configuring UFW with port forwarding"
date: 2013-01-15
forum: Networking &amp; Wireless
---

### Post by rienesl on 2013-01-15
Hi.
3 Networks:
eth3: 192.168.199.DHCP (internet access)
eth8: 192.168.179.1 (source)
tap0: 10.0.10.250 (VPN and here exist a network 10.0.0.X)

Goal: Get a connection to 2 devices from eth8 to eth3 & tap0

Working:
I get internet from devices located in eth8 through eth3
I can ping anything in 192.168.199.X 

Not Working:
I can't ping anything except 10.0.10.250 in 10.0.10.X
None of the port-forwardings seems to work (when trying to connect to 192.168.179.1)

Configuration:
/etc/ufw/before.rules
*nat
: POSTROUTUNG ACCEPT [0:0]
-A POSTROUTING -s 192.168.179.0/24 -o eth3 -j MASQUERADE
-A POSTROUTING -s 192.168.179.0/24 -o tap0 -j MASQUERADE
-A PREROUTING -i eth8 -p tcp --dport 22 -j DNAT --to 10.0.0.10:22
-A PREROUTING -i eth8 -p tcp --dport 3389 -j DNAT --to 192.168.199.127:3389
COMMIT

I have no clue, what I'm doing wrong.:confused:

PS: I had to make a space between : and POSTROUTING because of this:
:POSTROUTING

UPDATE: I  did a init 6 and now the 192.168.199.127:3389 is working. But I still have the problem with the 10.0.0.10:22

---

