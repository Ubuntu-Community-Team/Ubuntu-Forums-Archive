---
title: "interface no longer recognizes other networks"
date: 2009-04-24
forum: Networking &amp; Wireless
---

### Post by AKviking on 2009-04-24
My ubuntu machine was working perfectly fine.  Then something happened yesterday ( i can't recall any changes made ).

All of a sudden it will talk to any and all device in its own network (192.168.1.0/24) but not anything off net.  It won't hit internet addresses or my Debian box which is off the same router but in a seperate VLAN.

I have made no changes to the router and have double checked its programming.

I even ran Wireshark to capture it pinging the Debian box.  It looks as though the Debian box replies, but for some reason it won't acknowledge the reply.

My other machines can access the Debian box and the internet just fine.

Any ideas?

---

### Post by Peter09 on 2009-04-24
Sounds like the network gateway is not configured any more.

---

### Post by jimv on 2009-04-24
What the other guy said...make sure you have a gateway set (will be your router's ip address).

You can check your gateway by typing "route -n" in a terminal.

---

### Post by sahabcse on 2009-04-24
check

var/log/messages

---

### Post by AKviking on 2009-04-24
> **jimv said:**
> What the other guy said...make sure you have a gateway set (will be your router's ip address).

You can check your gateway by typing "route -n" in a terminal.

You win!!  I was checking my /etc/network/interfaces configuration for my gateway and it was there as it should be, so I was confused.

I tried the **route-n** and it showed 0.0.0.0 as my gateway. 

Confused, I checked my /etc/network/interfaces again and found that I had, in error, configured a different gateway on eth0 as well, which was not necessary because it's used to just view packets in promiscuous (*if only Mom knew*) mode.

Resolved, thanks.

---

