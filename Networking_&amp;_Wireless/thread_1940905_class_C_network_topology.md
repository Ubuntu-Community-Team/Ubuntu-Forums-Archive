---
title: "class C network topology"
date: 2012-03-14
forum: Networking &amp; Wireless
---

### Post by cbryant on 2012-03-14
I'm trying to set up a set of routers via subnetting.

I have a main router which does the NAT from external IP to 192.168.1.0/255.255.248.0 network. (CIDR wise a /21 class C network). This is a netgear router (my home network)

I have setup a secondary router which then subnets to 192.168.3.0/21. External interface is 192.168.1.181 and internal is 192.168.3.1 (2 NICs). This is a computer running ubuntu 11.10 server. Configured as per the ubuntu router page also running quagga. All IPs are currently static but will be running dhcp2-server on the internal port. This will be my business server so will be relocating to an office in the future and the external interface will then go to ISP modem. Currently have firewall full open for testing on this box to get routing working before I start locking things down.

I can communication just fine to the internet from dig, ping, etc.. running on the above router.

Anything connected to the internal port of router 2 can ping the internal and external ports on router 2 but can't access anything on 192.168.1.1. I tried removing all the iptable drop settings and added rules to allow icmp every which way I could think of, but ping still not working to the first router from the 192.168.3.x subnet.

I have ip forwarding enabled on the router 2.

Any suggestions on why router2 not routing packets or anything to look at?

---

### Post by redmk2 on 2012-03-15
> **cbryant said:**
> I'm trying to set up a set of routers via subnetting.

I have a main router which does the NAT from external IP to 192.168.1.0/255.255.248.0 network. (CIDR wise a /21 class C network). This is a netgear router (my home network)

I have setup a secondary router which then subnets to 192.168.3.0/21. External interface is 192.168.1.181 and internal is 192.168.3.1 (2 NICs). This is a computer running ubuntu 11.10 server. Configured as per the ubuntu router page also running quagga. All IPs are currently static but will be running dhcp2-server on the internal port. This will be my business server so will be relocating to an office in the future and the external interface will then go to ISP modem. Currently have firewall full open for testing on this box to get routing working before I start locking things down.

I can communication just fine to the internet from dig, ping, etc.. running on the above router.

Anything connected to the internal port of router 2 can ping the internal and external ports on router 2 but can't access anything on 192.168.1.1. I tried removing all the iptable drop settings and added rules to allow icmp every which way I could think of, but ping still not working to the first router from the 192.168.3.x subnet.

I have ip forwarding enabled on the router 2.

Any suggestions on why router2 not routing packets or anything to look at?

[**_[COLOR="DarkSlateGray"]Classful[/COLOR]_**]("http://en.wikipedia.org/wiki/Classful_network") IP Networks are a way to describe network addressing architecture.  CIDER (***[[I][COLOR="DarkSlateGray"]_Classless_[/COLOR]*]("httphttp://en.wikipedia.org/wiki/Classless_Inter-Domain_Routing")[/I]** Inter-Domain Routing) is another method.  You should use one method or the other, not both.  But what's in a name...

What is more important is understanding the boundaries of your networks and that all addresses in the network must be contigious Below is a /21 (255.255.248.0) network.  Using your 192 root, see below
```

Start:	192.168.0.[COLOR="Red"]0[/COLOR]	= 110000001010100000000000[COLOR="Red"]00000000[/COLOR]
End:	192.168.7.**[COLOR="Blue"]255[/COLOR]**	= 110000001010100000000111[COLOR="Blue"]**11111111**[/COLOR]
This is a range of 2048 addresses

Resulting network range (in CIDR notation): 192.168.0.0/21 (255.255.248.0)

```
Resulting network range (in CIDR notation): 192.168.0.0/21 (255.255.248.0)

Note that the Network ID is 192.168.0.0 (not a strictly valid device address).  Note also that the broadcast address is 192.168.7.255 (not a valid device address for sure).  In this network all of the rest of the addresses are for devices (hosts) and are peers (this is 1 large network).

If you want to create 2 networks out of this address range, The boundaries are:
```

The ***first*** network

New start:	192.168.**[COLOR="Purple"]0[/COLOR]**.[COLOR="Red"]0[/COLOR]	= 1100000010101000**[COLOR="Purple"][COLOR="Purple"]00000000[/COLOR][/COLOR]**[COLOR="Red"]00000000[/COLOR]
New end:	192.168.**[COLOR="Purple"]3[/COLOR]**.**[COLOR="Blue"]255[/COLOR]**	= 1100000010101000**[COLOR="Purple"]00000011[/COLOR]****[COLOR="Blue"]11111111[/COLOR]**
This is a range of 1024 addresses

Resulting network range (in CIDR notation): 192.168.0.0/22 (255.255.252.0)

The ***second*** network

New start:	192.168.[COLOR="Purple"]**4**[/COLOR].[COLOR="Red"]0[/COLOR]	= 1100000010101000[COLOR="Purple"]**00000100**[/COLOR][COLOR="Red"]00000000[/COLOR]
New end:	192.168.[COLOR="Purple"]**7**[/COLOR].**[COLOR="Blue"]255[/COLOR]**	= 1100000010101000[COLOR="Purple"]**00000111**[/COLOR]**[COLOR="Blue"]11111111[/COLOR]**
This is a range of 1024 addresses

Resulting network range (in CIDR notation): 192.168.4.0/22 (255.255.252.0)

```
Both of these have a Network ID and a broadcast address:
```
First Network ID:	192.168.0.0 /22
First Network B'cast	192.168.3.255

Second Network ID:	192.168.4.0
Second Network B'cast	192.168.7.255
```
In looking at your description it appears that you have tried to create to networks using the ***same*** address space.  This will always cause anomalies.  I see you have installed quagga, but for what reason?  Dynamic routing protocols are used to keep track of network routes that you don't control in a dynamic environment.  All your routes appear to be static.

What is the reason for the second router?  Routers allow traffic between separate networks (inter-networking).  With the /21 network you do not need a router for IP addresses 192.168.0.1 through 192.168.7.254.  If you are just experimenting, I suggest you use the 2 networks I described above (2, 4 or 8 networks).  If you want these networks to be smaller then subnet them along the boundaries as I described.  If you need help with the sub-netting, let us know what you want.

---

