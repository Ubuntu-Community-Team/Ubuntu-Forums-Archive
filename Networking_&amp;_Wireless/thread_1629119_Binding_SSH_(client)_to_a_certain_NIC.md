---
title: "Binding SSH (client) to a certain NIC"
date: 2010-11-23
forum: Networking &amp; Wireless
---

### Post by eroomydna on 2010-11-23
I connect to my corporate LAN(dhcp) using a wired connection and also connect to a WLAN(dhcp) without various constraints applied by the wired connection. 

In short my wired connection blocks outbound ssh traffic to my server at home. My WLAN connection is pretty lax so ssh connections to my home webserver can be made using the wireless connection.

Can I route ssh to that particular ip via my wireless connection?

---

### Post by eroomydna on 2010-11-23
I've found out myself! Typically 20 minutes after posting!

Add a route

sudo route add -net {destination ip} netmask 255.255.255.255 gw {gateway ip} dev wlan0

Worked like a charm!

---

