---
title: "Laptop/Router stop connecting to each other, but each still work with all other boxes"
date: 2009-09-24
forum: Networking &amp; Wireless
---

### Post by gcopenhaver on 2009-09-24
My problem is that occasionally my Ubuntu laptop will not be able to connect to my Ubuntu router.  However my Ubuntu laptop can still access any other device on the network (wired or wireless), and my Ubuntu router can still access any other device on the network (wired or wireless).

When I notice that the laptop won't communicate with the router (usually when the browser suddenly can't load a page), any attempts to ping the router or login through ssh fail/timeout.  Even reconnecting the wireless on the laptop often doesn't fix it, *though note that I think the laptop is communicating with the router to get an IP address from the DHCP daemon* (at least I'm not aware of any type of caching that allows the laptop to assume it will get the same address), but then there's no more communication after that.

My workaround has been to login to the router some other way, usually by remotely logging into my desktop and then remotely logging into my router from the desktop, and then having the router ping my laptop.  After at least a few seconds, the router and laptop start communicating again, and everything is fine until some seemingly unpredictable time in the future (sometimes under half an hour, other times many hours or days).  I have often logged into the router and set it to continue pinging my laptop all the time, which keeps them communicating except for the occasional hiccup where they stop communicating for maybe 5 seconds (the pings will stop and the laptop won't be able to communicate with the router), and then it continues working again.

It's a very strange problem that I haven't been able to narrow down to any piece of hardware.  The wireless works fine, because the laptop can still communicate with other machines on the network and vice-versa.  The router and ethernet are fine, as other machines (wired or wireless) can still connect to the router just fine and vice-versa.  I'd like to figure out what the problem is (as it's annoying, and could potentially cause problems for others that wouldn't be able to figure out how to workaround it).

I'm not sure what log files or config files may be useful to post.  In the past when I've looked through the log files I didn't notice anything related to this, but it's quite possible I wasn't looking in the right places or just missed the relevant information (or was unaware of the relevance of some info).  Please let me know what log files may be of use in helping with this problem.

Thank you for reading this!


**Some Details:**

_Laptop:_
[INDENT]Ubuntu 9.04 32-bit
Dell Inspiron 6000 w/ Broadcom BCM4318 wireless using b43 module[/INDENT]

_Router:_
[INDENT]Ubuntu 8.04.3 32-bit
Dell Server w/ 2x Realtek RTL-8139
services running:
[INDENT]Firewall (iptables)
DHCP
DNS
SSH[/INDENT][/INDENT]


_Other machines include:_
Desktop - Ubuntu 9.04 64-bit
Dell Laptop - Windows XP SP3
Wii


_Networking equipment:_
16-port 10/100 switch
D-Link wireless router w/ 4-port switch


_Connections:_
Router and Desktop -> 16-port switch
D-Link wireless router -> 16-port switch
Ubuntu and Windows laptops, Wii -> D-Link wireless router

---

