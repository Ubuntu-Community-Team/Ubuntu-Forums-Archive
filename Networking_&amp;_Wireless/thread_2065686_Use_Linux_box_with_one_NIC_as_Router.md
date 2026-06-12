---
title: "Use Linux box with one NIC as Router"
date: 2012-10-02
forum: Networking &amp; Wireless
---

### Post by beboylips on 2012-10-02
Hello community,

Is it possible to use a Linux box with just one Ethernet NIC as a router, creating virtual interfaces, thus having two IP addresses on one physical network card?

eth0 192.168.2.1 (local router IP address and netmask)
eth0:0 (WAN IP Address and Netmask)

Then use IPtables and routing to direct traffic from eth0:0 to eth0 and back (or maybe use bridging if that's possible for virtual interfaces?).

Please leave your suggestions and comments.


Thank you,
-Beboy

---

### Post by lukeiamyourfather on 2012-10-02
I don't think this will work. Why would you need to do this? Another NIC could be had for around $10. If you're on a laptop or something without expansion slots there are [USB adapters]("http://www.neweggbusiness.com/Product/Product.aspx?Item=N82E16812186164&nm_mc=KNC-GoogleBiz&cm_mmc=KNC-GoogleBiz-_-pla-_-NA-_-NA&gclid=CPeQlNb24rICFelFMgodtyUAuQ") too.

---

### Post by CharlesA on 2012-10-02
> **lukeiamyourfather said:**
> I don't think this will work. Why would you need to do this? Another NIC could be had for around $10. If you're on a laptop or something without expansion slots there are [USB adapters]("http://www.neweggbusiness.com/Product/Product.aspx?Item=N82E16812186164&nm_mc=KNC-GoogleBiz&cm_mmc=KNC-GoogleBiz-_-pla-_-NA-_-NA&gclid=CPeQlNb24rICFelFMgodtyUAuQ") too.
What they said.

It won't work because you cannot create the firewall rules required with a virtual interface.

---

### Post by 1clue on 2012-10-02
It depends on what your goal is.  If you intend a firewall or some sort of secure barrier, then it won't work because lots of tools will let you snoop.

If you have, say, a cable modem with a handful of public IP addresses, then you can let the device handle your routing even though you might be on the same physical network.  I have a device like this, I tried to make a public box exist on both networks and caused it to not work at all.  Works fine when the public box only thinks it belongs on the public network.

If your card supports 802.1q (vlan) protocol then it will work, assuming you're on a trusted network on both sides of your router.  Again, tools will let you snoop.  If you use VLAN support then usually it means you have a restricted access network of switches that are all abiding by a coordinated security policy.

Keep in mind that this means shared bandwidth and extra overhead on the physical network.  It's a make-do hack at best, not good practice.

---

### Post by beboylips on 2012-10-02
Thank you all for your replies. Clearly, this is not a good idea and I will go with buying an extra NIC.

-Beboy

---

### Post by JKyleOKC on 2012-10-02
I'm amazed that nobody mentioned the most obvious reason why it won't work: a router needs at least two RJ45 sockets, one for input and one for output (although most have at least five, for multiple output connections), and the single NIC has only one!

---

### Post by 1clue on 2012-10-02
@JKyleOKC,

While that's mostly true for 'proper' routers, you can use a Linux-based router to route between two virtual networks on the same card.

Most proper routers I've seen have either 2 or 3 interfaces.  3 interface version includes one adapter for a failover device.

SOHO (small office/home office) devices can have more, but that's really a combination of a switch and a router and a wireless router.

---

### Post by JKyleOKC on 2012-10-02
> **1clue said:**
> While that's mostly true for 'proper' routers, you can use a Linux-based router to route between two [COLOR=Red]virtual[/COLOR] networks on the same card.True; I hadn't considered the possibility that the router was on a virtualization host!

---

### Post by 1clue on 2012-10-02
Not exactly what I'm talking about.  The most common use case of what I'm talking about is if you have an extra IP attached to a NIC.  You can have, for example, 192.168.1.10 as your main address.  Then you can add 10.40.2.1, on the same interface.  As long as every other host only knows about one network then everything should work fine, but you of course don't have two physical networks even if you're pretending you do.

On a virtualization host, no physical network adapters are being used within the virtualized cloud, but they are being emulated by software.  The only time the virtual traffic crosses to a physical network is if it routes to an external system.

---

### Post by JKyleOKC on 2012-10-02
Could you use that to build a router? The point that struck me was that for the usual router use case, you need one connection to a modem and another to a switch that feeds the routed devices. I don't see how virtual networks would apply to this use case.

---

### Post by 1clue on 2012-10-02
As a matter of fact, my office has an AT&T business package which does exactly that.  Not my ISP, not my router, not my responsibility.

They give 4 public IP addresses, and a private class C.

The public addresses are allocated by taking them.  There is no partitioning of ethernet ports, you can either take the dhcp assignment of a 192.168.* or you can take the public address, either from ethernet or from wireless.  If the box is public then it is exposed and should not take a private address or the routing gets fubar.  Likewise if you're private you should not try to route directly to the public.

As I've said repeatedly here, this allows the illusion of multiple networks over a single physical network.  The traffic is not limited.

The way you can tell this is what happened is as follows:

[LIST=1]
[*]Assign a public IP and a private IP to the same host.
[*]From a private-only host, try to access a service on the public address.
[*]The initial packet is routed (correctly) to the router since it is not on the same logical network.
[*]The router (correctly) routes it to the public address.
[*]The multi-addressed box processes the request and responds (incorrectly) by the most direct route.
[*]The client rejects the packet as it is not coming from the expected address.
[/LIST]

This scenario only works if everyone plays nicely, but DHCP can configure everything to play nicely except the servers, or of course if you start messing around.

---

### Post by beboylips on 2012-10-02
This confused the matter even more :P So technically it can be done with virtual NICs*?

---

### Post by 1clue on 2012-10-02
Yes and no.

You can have a system where routing takes place, but this is not in any way secure.

I believe it was put there so you could test networking software all from the same host.  Or maybe, like with so many other Linux features, because whoever coded it into the kernel wanted to take into account every possibility.

I personally think it's stupid, but it's there.  The questions on this thread are asking about "can you..."  and you can, so I said it.  "Should you..." on the other hand?  No.  And still it's happening at the hands of a major ISP.

Keep in mind that if it were me setting up this network, I would have immediately bought separate devices and handled it all myself.  My home system has multiple devices before you get to anything important, and that's just me.  AND the wireless is locked down pretty well too.

---

### Post by beboylips on 2012-10-02
> **1clue said:**
> Yes and no.

You can have a system where routing takes place, but this is not in any way secure.

I believe it was put there so you could test networking software all from the same host.  Or maybe, like with so many other Linux features, because whoever coded it into the kernel wanted to take into account every possibility.

I personally think it's stupid, but it's there.  The questions on this thread are asking about "can you..."  and you can, so I said it.  "Should you..." on the other hand?  No.  And still it's happening at the hands of a major ISP.

Keep in mind that if it were me setting up this network, I would have immediately bought separate devices and handled it all myself.  My home system has multiple devices before you get to anything important, and that's just me.  AND the wireless is locked down pretty well too.

Thank you, this answers my question fully.

---

