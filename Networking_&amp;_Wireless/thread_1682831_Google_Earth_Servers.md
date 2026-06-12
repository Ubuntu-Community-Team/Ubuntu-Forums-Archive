---
title: "Google Earth Servers"
date: 2011-02-06
forum: Networking &amp; Wireless
---

### Post by Charlie Tame on 2011-02-06
Didn't find an answer here or anywhere else including Google forums so here is what I found after a clue from SBIN in another forum...

Using Qwest DSL and Actiontec wireless router I was getting "Google Earth Cannot Find Servers" or some such garbage. Everything else was fine, just not Google Earth.

File>Server log out and File> Server log in same trouble.

sudo gedit /etc/resolv.conf had the DNS setting from DHCP in the first line. Changing this to 8.8.8.8 which is a Google DNS server and saving the file fixed the problem, I could log out and in or restart GE and it worked fine. Only problem is after a shutdown it seems DHCP put back the router as DNS server and clearly there is a problem with that, maybe Actiontec hardware related.

So I went into preferences and "Network Connections" and edited both wired and wireless to use DHCP Addresses Only and added 8.8.8.8 and 8.8.4.4 to the DNS list. Since then, no problem.

Hope this helps others as GE help is about as much use as an ashtray on a motorcycle.

U10.10 by the way though I am not sure why that would make a difference since everything else seemed to work and one would assume the router passed on DNS references in the same format every time.

---

