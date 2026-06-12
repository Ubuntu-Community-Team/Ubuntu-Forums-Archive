---
title: "Trouble With DHCP, Traceroute, And Local Windows XP PC"
date: 2011-08-03
forum: Networking &amp; Wireless
---

### Post by Craig Stcr1 on 2011-08-03
I'm having trouble connecting to my Windows XP pc on my wired network, which is configured to use DHCP.  Nslookup works fine.  But if I run traceroute, giving it the IP address of my Windows XP pc, traceroute just shows asterisks, 30 lines of them, and exits.  I can't telnet to it either.  I can access other hosts, locally and on the internet, no problem.  And from Windows 7, traceroute to the Windows XP pc works fine.  It's just a problem on my workstation running Ubuntu 11.04 Natty Narwhal.  My /etc/network/intefaces looks like this:

```
#/etc/network/interfaces

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp
```I'm stumped.  Any ideas???

---

### Post by dandnsmith on 2011-08-03
I take it that all the PCs are connected to a router, hub or switch?

You wouldn't expect to be able to telnet to the XP PC, unless you've set up a telnet server on it.

The Win7 may get a response where the UBuntu doesn't because of (for example) firewall settings.
I'd start with simple pings (try both ways), and then go on from there.

---

### Post by Craig Stcr1 on 2011-08-03
Thanks for your response.  All the PCs are connected to a switch, and a Westell 2200 DSL modem/router.  Regarding telnet, you're absolutely right, I don't have the telnet server running.  But I should get a "connection refused" right away.  Instead, it hangs and then times out.  Maybe I shouldn't have even mentioned the telnet issue, because it's a distraction.  I'm not really worried about getting telnet working.  The fact that traceroute isn't giving a meaningful response is more the issue.  I tried ping... no response.

---

### Post by dandnsmith on 2011-08-03
so, ping name , and ping IP address:
one of those should work if routing is set up and firewalls aren't obstructing. The modem/router should take care of the routing, which leaves firewalls (if all the ports etc are working).

---

### Post by Craig Stcr1 on 2011-08-03
Thanks Derek.  It was the firewall on the Windows XP pc.  I don't know why traceroute to the Windows XP pc worked when originating from Win 7, and not from Ubuntu, but it seems the problem is solved now.  And I didn't think traceroute actually needed connectivity to the target host, but just elicited information from the routers along the way.  Thanks for your help!

---

