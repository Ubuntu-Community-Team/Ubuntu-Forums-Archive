---
title: "Help needed configuring VLANS"
date: 2010-07-21
forum: Networking &amp; Wireless
---

### Post by Sisco88 on 2010-07-21
im in need of some help trying to configure multiple vlans on my ubuntu desktop.

we have several huawai ma5600t machines that need to be configured by downloading their config trough a tftp server. i currently have a switch configured with 4 vlans and a ubuntu desktop with the same amount of vlans.

the /etc/network/interfaces file looks like this:

```
auto lo
iface lo inet loopback

#VLANS

auto vlan2
auto vlan3
auto vlan4
auto vlan5

# VLAN 2
iface vlan2 inet static
address 10.11.104.1
netmask 255.0.0.0
network 192.0.0.0
mtu 1500
vlan_raw_device eth0

# VLAN 3
iface vlan3 inet static
address 10.11.104.1
netmask 255.0.0.0
network 192.0.0.0
mtu 1500
vlan_raw_device eth0

# VLAN 4
iface vlan4 inet static
address 10.11.104.1
netmask 255.0.0.0
network 192.0.0.0
mtu 1500
vlan_raw_device eth0

# VLAN 5
iface vlan5 inet static
address 10.11.104.1
netmask 255.0.0.0
network 192.0.0.0
mtu 1500
vlan_raw_device eth0
```as you can see each vlan has the same ip address, this is because the huawai machines all have the same ip (10.11.104.2) and are not supposed to be changed.

now this is where i ran into trouble, pinging the server only works from vlan3. when i reconfigured the vlans i was only able to ping the server from the huawai machine on vlan2. with wireshark i can see the ping request reach the server with the correct vlan id's but it doesnt send back a reply to the huawai machine except for on the one working vlan.

this has been bothering me the past few days and cant seem to work it out. i have tried changing network addresses of each vlan interface on the server machine and that also didnt help same for changing the ip addresses of the vlan interfaces.

if anyone could help me with this it would be greatly appreciated.

Sisco

---

