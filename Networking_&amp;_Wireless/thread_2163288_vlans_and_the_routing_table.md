---
title: "vlans and the routing table"
date: 2013-07-17
forum: Networking &amp; Wireless
---

### Post by imlepid on 2013-07-17
I setup an ubuntu 12.04 system with vlan tagging where each vlan has a static IP address.  To do this I used the "vlan" package as detailed on the help page [https://wiki.ubuntu.com/vlan](https://wiki.ubuntu.com/vlan)

Here's my /etc/network/interfaces config I had originally (first two octets replaced by x.y):

```

auto lo
iface lo inet loopback

auto vlan4
iface valn4 inet static
address x.y.4.76
netmask 255.255.252.000
network x.y.4.0
broadcast x.y.7.255
gateway x.y.4.1
vlan_raw_device eth0

auto vlan240
iface vlan240 inet static
address x.y.240.242
netmask 255.255.255.248
gateway x.y.240.241
vlan_raw_device eth0

auto vlan136
iface vlan136 inet static
address x.y.240.142
netmask 255.255.255.248                                                                                 
gateway x.y.240.141                                                                                 
vlan_raw_device eth0     

```

When I had this the routing table ([FONT=Courier New]route -n[/FONT]) had a default route through vlan4 but I needed the default route to be via vlan136, so I removed vlan4 because I didn't really need it anyway.

However, when I did removed vlan4 from the config the default route was via vlan240.  That worked ok, but I'd prefer default to be vlan136.  I can manually manipulate the routing table using [FONT=Courier New]route add[/FONT] and [FONT=Courier New]route delete[/FONT] but what logic is used to select default?  I though it might be the lowest network (or vlan) but that's not the case.

Another question, running [FONT=Courier New]/etc/init.d/networking restart[/FONT] didn't seem to regenerate the routing table.  I ended up rebooting to get the new table.  What command can I run to fully "refresh" the network settings as if I had booted fresh.

Many thanks.

---

### Post by Rsxhawk on 2013-08-07
Are you trying to run multiple vlans on your machine over one physical interface, that's what it looks like as each entry as "raw device eth0" specified.  Can I ask why you're doing this or what you're trying to accomplish?  Is the switch this machine plugged into even capable of handling traffic from all these vlans?  You're tagging the traffic from the server with a specific vlan-tag, so when it enters the switch port, that switch will have to know what to do with that frame/packet i.e. a trunk port.  But I think what you're trying to figure out, is how do you make your server route the traffic appropriately to each vlan interface?  My only answer to that would be to make your route table entries as specific as possible where you say all traffic from network x.y.240.142 will go out interface vlan136.  I'm not familiar with this kind of setup on a linux box using vlan interfaces...I've only seen real life examples using multiple physical interfaces on unix servers.

---

