---
title: "Switching to IPv6"
date: 2009-12-07
forum: Networking &amp; Wireless
---

### Post by soltanis on 2009-12-07
Hey guys,

I help manage a medium-sized office LAN for a student radio station. We're looking to upgrade our older systems to be more future-oriented.

One of the potential upgrades I'm looking at is switching our LAN network from IPv4 to IPv6.

So a few questions:

1) What are the potential benefits for IPv6? Will this affect my network performance? Will so-called "jumbograms" be a good idea to use considering that we are linked by Gigabit Ethernet, or is it a waste of my time?

2) How could I possibly make this switch happen? Currently our setup uses statically assigned IP addresses in the private subnet range (10.*.*.*) and then uses DHCP to dynamically assign the rest. If I switched to IPv6, what guidelines should I be following for numbering the nodes in my network? Does DHCP still work, or would I expect compatibility issues?

3) How can I keep the internal network IPv6 while maintaining Internet connectivity (a 6to4 tunnel at the router, I assume?); and considering that our ISP has us on IPv4 anyway, again, is it really worth switching?

I find it kind of disappointing that it's taking everyone so long to go over to IPv6, especially considering how fast IPv4 addresses are being used up, and the more time passes, the more I steadily get anxious that I'm falling behind. So, IPv6, ftw?

---

### Post by davidm84 on 2009-12-07
There isn't any real enhancements for IPv6. Not any faster or anything like that. The only advantage for IPv6 is to have more hosts on the Internet (running out of IPs for hosting things on the net). Within a private network this is not viable to switch over because from a 192.168.0.0/16 you have 65,536 host addresses. If you need more then go to IPv6.....

---

### Post by Ux64 on 2010-01-26
> **davidm84 said:**
> Within a private network this is not viable to switch over because from a 192.168.0.0/16 you have 65,536 host addresses. If you need more then go to IPv6.....

Dont forget 10. and 172.16 to 172.31 addresses. Even more space. ;)

---

### Post by Skaperen on 2010-02-02
> **Ux64 said:**
> Dont forget 10. and 172.16 to 172.31 addresses. Even more space. ;)
IPv6 offers Unique Local Addresses (like private IPs) that are more globally unique. While collisions could still happen, they are rare enough that if businesses use ULA addresses for machines not intended for internet access, and two of them merge together in some future business deal, they are very unlikely to have any collision issues from both of them using these addresses, when they merge their networks.

---

### Post by Grenage on 2010-02-02
> There isn't any real enhancements for IPv6

There are **loads** of enhancements!  However at the moment using v6 will be more headache than salvation.

---

### Post by Ux64 on 2010-02-07
> **Skaperen said:**
> IPv6 offers Unique Local Addresses (like private IPs) that are more globally unique. While collisions could still happen, they are rare enough that if businesses use ULA addresses for machines not intended for internet access, and two of them merge together in some future business deal, they are very unlikely to have any collision issues from both of them using these addresses, when they merge their networks.

I don't get point of using private address spaces. Those are only for small businnesses and home users. If you got real business you don't need those. So it's not a problem to join companies using public addresses.

Using private address space is very bad habit and causes many many problems. And doesn't provide any real advantages, except you don't need to have public addresses.

Btw. There is only one Finnish ISP which provides IPv6 addresses and net access. Most of ISP's just say WTF when you ask if they are IPv6 ready and if they need testers or if they even have IPv6 plan. Nope, nobody's doing anything about that. I just wonder what kind of problem it will be when they're forced to start using IPv6. No pre-planning what so ever.

---

### Post by Skaperen on 2010-02-14
Even if I had public IP space, I'd use private IP space as a very distinct separation of network nodes that are supposed to NOT access the net (or be accessed by the net).  I don't currently have any public IP addresses, so it's moot for now.

I've never had any issues with private IP addresses in IPv4.  I don't see how IPv6 add any.  You have any details I don't know of?

What will happen when the day comes that ISPs need to get IPv6 going real fast, is a lot of poorly configured IPv6 configurations, and a rising demand for network engineers experienced with IPv6.

---

