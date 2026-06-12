---
title: "PPTPD VPN Ruting Issues"
date: 2009-04-25
forum: Networking &amp; Wireless
---

### Post by un_dave on 2009-04-25
Hi all, 

I'm attempting to setup a VPN server (pptpd) on 8.04 (fully updated), 
I've installed the pptpd packages, and done some basic setup, to the point where I can now connect to the VPN remotely from a windows system. 

The network layout is like this:

Windows System -> router/modem -> INTERNET -> 

-> router/modem 
    -> VPN Server
    -> Printer
    -> Other office workstations etc. 

(I hope that makes sense!)

However, I think I'm having some issues with routing, or at the least, my understanding of how a VPN is meant to work must be flawed. 

While (once the VPN is connected) I can ping the VPN servers internal ip from the windows system, I cannot ping/see any of the other things on the internal network (Such as the printer, or even the router/modem). 

I figure that I've got to somehow tell the VPN server that it should be forwarding traffic to the appropriate internal network locations, but I'm not sure how.

Anyone have any ideas where to start ?

---

### Post by un_dave on 2009-04-29
Well, it seems that the helpful folks on IRC managed to point me in the right direction. 

For anyone else with the same issue, all i needed to do was enable ip forwarding. 

to check the status of ip forwarding:
```

cat /proc/sys/net/ipv4/ip_forward

```

to update it, something like this:
```

echo 1 > /proc/sys/net/ipv4/ip_forward

```

and to perminantly apply it, just put:
```

net.ipv4.ip_forward=1

```
 in /etc/sysctl.conf (or i found it was already there, i just needed to uncomment it)

---

