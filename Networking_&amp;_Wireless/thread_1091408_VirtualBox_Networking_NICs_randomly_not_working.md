---
title: "VirtualBox Networking: NICs randomly not working"
date: 2009-03-09
forum: Networking &amp; Wireless
---

### Post by adieb on 2009-03-09
This is a copy of a post i did in the Virtualbox forum. Though I am not 100% sure, if this isn´t a linux-based problem, i am posting it here too.

So here is the link:
[http://forums.virtualbox.org/viewtopic.php?f=7&t=15248](http://forums.virtualbox.org/viewtopic.php?f=7&t=15248)

Thanks.

---------------------------
Hello,

I´ve already confirmed a bug report on the public bugtracker:
[http://www.virtualbox.org/ticket/2191](http://www.virtualbox.org/ticket/2191)

But i want to describe this very confusing and annyoing error here; maybe somebody has found a workaround.

Host:
Linux Host (Ubuntu 8.04 Server 64bit)
3 Network Cards connected to different subnets


VM:
Ubuntu Jeos Client 8.04 32bit
3 Virtual NetworkInterfaces (hostif)
Dhcp-Server serving on two NICs, (two different subnets), using "ip route" source routing

The Problem:
After starting the VM it shows the 3 NICs, it can send Packages through them, but it may not receive any packages through one or two of these NICs.
This sounds like a routing problem, caused by the VM. I exlcuded that by flushing all routing tables, the routing cache and then tried to receive an adress on one of the affected NICs by using dhclient.
What I could see was, that it sends the dhcp-request, but it never receives any packages.

So I restart the Maschine (no changes to any config...) and then another NIC is affected. Restart again, again, again..... Suddenly all NICs are setup correctly.

This procedure can take up to 15 times. Very annoying!!!

Is there anybody who faces similar problems. or at least runs a similar task?

Thanks a lot. I would appreciate any kind of help.

---

### Post by adieb on 2009-03-16
bump

---

