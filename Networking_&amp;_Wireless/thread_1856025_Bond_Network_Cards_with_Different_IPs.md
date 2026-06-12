---
title: "Bond Network Cards with Different IPs"
date: 2011-10-07
forum: Networking &amp; Wireless
---

### Post by smcc-wks on 2011-10-07
Hello Community,
 
Is it possible to bond 3 network cards, all with different IP addresses as one virtual/bonded NIC? We have 3 VLANs that we would like to combine into one virtual NIC for use with Free Opensource Ghost. Each VLAN has a different IP ranged and they do not talk to each other. I have read into ifenslave but that seems to be for link aggregation/trunking for increased throughput. We just want a Gigabit link to each VLAN.
 
Thank you in advance, 
 
SMCC

---

### Post by karlson on 2011-10-07
> **smcc-wks said:**
> Hello Community,
 
Is it possible to bond 3 network cards, all with different IP addresses as one virtual/bonded NIC? We have 3 VLANs that we would like to combine into one virtual NIC for use with Free Opensource Ghost. Each VLAN has a different IP ranged and they do not talk to each other. I have read into ifenslave but that seems to be for link aggregation/trunking for increased throughput. We just want a Gigabit link to each VLAN.
 
Thank you in advance, 
 
SMCC

Why would you want to bond them together?

---

### Post by smcc-wks on 2011-10-07
Because FOG can only use 1 interface which is why we want all 3 NICs to be aliased as one NIC.  To FOG it will look like one NIC but traffic will be broadcast from the one bonded NIC to all 3 VLANs.

---

### Post by drdos2006 on 2011-10-07
Check these out, did a search on "bridging" and "bonding"

[http://ubuntuforums.org/showthread.php?t=1842656](http://ubuntuforums.org/showthread.php?t=1842656)

[http://ubuntuforums.org/showthread.php?t=1840543](http://ubuntuforums.org/showthread.php?t=1840543)

regards

---

### Post by bab1 on 2011-10-07
> **smcc-wks said:**
> Because FOG can only use 1 interface which is why we want all 3 NICs to be aliased as one NIC.  To FOG it will look like one NIC but traffic will be broadcast from the one bonded NIC to all 3 VLANs.

So why not just use aliases for eth0 or some such like this (from the man page of ifconfig)```
 interface
              The name of the interface.  This is usually a driver  name  fol&#8208;
              lowed  by a unit number, for example eth0 for the first Ethernet
              interface. [B][COLOR="Red"]If your kernel supports  alias  interfaces,  you  can
              specify  them  with  eth0:0 for the first alias of eth0. You can
              use them to assign a second address. [/COLOR][/B]To delete an  alias  inter&#8208;
              face use ifconfig eth0:0 down.  Note: for every scope (i.e. same
              net with address/netmask combination) all aliases  are  deleted,
              if you delete the first (primary).
```

See [**_[COLOR="Blue"]here[/COLOR]_**]("http://www.linode.com/wiki/index.php/Multiple_IPs") for practical examples.

Edit:  The only gotcha in this is that FOG server must be in a ******[COLOR="Magenta"]single  [/COLOR]network with all the VLANS inside.  You mention that FOG uses broadcasts, so nothing will cross a router.  An example would be a network of 192.168.0.0/16 .  All subnets (254 of them) are in the same Network (broadcast range).

---

