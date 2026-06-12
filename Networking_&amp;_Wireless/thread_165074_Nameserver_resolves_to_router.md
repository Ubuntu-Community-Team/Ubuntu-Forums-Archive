---
title: "Nameserver resolves to router"
date: 2006-04-23
forum: Networking &amp; Wireless
---

### Post by sanderjd on 2006-04-23
My issue is that Ubuntu seems to be resolving the DNS nameserver to the local address for my router. That is, resolv.conf outputs:
```
192.168.1.1
```
How is this being determined? I am wondering what mechanism the operating system uses to determine what nameserver to use, so that I can perhaps tweak this myself so that it finds the correct servers. I know it is a DNS problem, because everything works with simple numbers, and furthermore I can manually enter the correct DNS server addresses and the problem is fixed, but even then, a daemon of some sort seems to come around and overwrite resolv.conf periodically. If anyone knows where all of this is handled, it would be very helpful. Thanks

---

### Post by jazzmuzik on 2006-04-23
What router and model are you using? Can you log in to your router with Firefox?

I believe resolv.conf is overwritten by the system itself when it gets DHCP info from your router.

---

### Post by sanderjd on 2006-04-23
My router is currently a netgear WGR614, but I had a very similar problem using an Actiontec GT701-WG, though this was with SuSE rather than Ubuntu.

If resolv.conf is being updated by the system based on information received from my router, is there any way to determine why my router would seemingly be identifying itself as a nameserver when it clearly is not functioning as such, or is there any way to lock resolv.conf to keep it from being overwritten?

---

### Post by jazzmuzik on 2006-04-24
Can you log in to your router? I believe it has an address of 192.168.1.90 or 192.168.1.1

A quick Google search shows others with the same problem.

---

### Post by mips on 2006-04-24
[QUOTE=sanderjd]My router is currently a netgear WGR614, but I had a very similar problem using an Actiontec GT701-WG, though this was with SuSE rather than Ubuntu.

If resolv.conf is being updated by the system based on information received from my router, is there any way to determine why my router would seemingly be identifying itself as a nameserver when it clearly is not functioning as such, or is there any way to lock resolv.conf to keep it from being overwritten?[/QUOTE]

Your router basically forwards the DNS queries to your ISP.

Log into your router and manually specify the ISP DNS server IP addresses. This might help but not sure.

---

