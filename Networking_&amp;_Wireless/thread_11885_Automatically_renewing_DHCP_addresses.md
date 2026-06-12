---
title: "Automatically renewing DHCP addresses?"
date: 2005-01-20
forum: Networking &amp; Wireless
---

### Post by irishbear on 2005-01-20
Hi there,

Where I work, we're starting to investigate using Linux as a desktop platform (at the moment we're testing using Ubuntu), instead of Windows. However, a lot of our users have laptops, and we're having a strange problem with DCHP.

We have our lan split into different subnets; so for example, our finance department might have have IP addresses in the x.x.160.x range, while our IT department might have addresses in the x.x.64.x range, etc..

If a laptop is connected to the network when it boots up, it'll pick up an appropriate address via DHCP just fine. If you pull out the network cable, the machine detects that it's disconnected (verified by the Network Monitor panel applet). However, if we then take that laptop and reconnect it to the network from a connection in a different subnet, while the machine detects that it's reconnected, it doesn't automatically renegociate a new address via DHCP, and attempts to use the old one.

If we do a manual release/renew using 'sudo ifdown eth0' followed by a 'sudo ifup eth0', then we get a valid new address fine; but the machine won't do this automatically.

I've had a look around via Google, but haven't found anything useful. Is there any way to set this up?

Thanks for your help!


John

---

### Post by python on 2005-01-20
[QUOTE=irishbear]Hi there,

Where I work, we're starting to investigate using Linux as a desktop platform (at the moment we're testing using Ubuntu), instead of Windows. However, a lot of our users have laptops, and we're having a strange problem with DCHP.

We have our lan split into different subnets; so for example, our finance department might have have IP addresses in the x.x.160.x range, while our IT department might have addresses in the x.x.64.x range, etc..

If a laptop is connected to the network when it boots up, it'll pick up an appropriate address via DHCP just fine. If you pull out the network cable, the machine detects that it's disconnected (verified by the Network Monitor panel applet). However, if we then take that laptop and reconnect it to the network from a connection in a different subnet, while the machine detects that it's reconnected, it doesn't automatically renegociate a new address via DHCP, and attempts to use the old one.

If we do a manual release/renew using 'sudo ifdown eth0' followed by a 'sudo ifup eth0', then we get a valid new address fine; but the machine won't do this automatically.

I've had a look around via Google, but haven't found anything useful. Is there any way to set this up?

Thanks for your help!


John[/QUOTE]
 Search for DNS on this site and you should find some stuff that may help.

---

### Post by irishbear on 2005-01-20
I've already had a look and haven't been able to track anything down.

I think the problem is that when the cable is disconnected, even though Linux is detecting that the connection is gone (verifiable via the 'disconnected' status reported by the 'Network Monitor' panel applet), Linux isn't bringing the interface down automatically, so it holds on to it's old address and doesn't try to get a new one via DHCP when the connection is restored (even if the new connection is on a different subnet).

Is there a way to get linux to automatically bring an interface down when it's disconnected, and back up again when there's a new connection?

---

### Post by irishbear on 2005-01-21
Aha! In [a post on another forum](http://www.linuxquestions.org/questions/showthread.php?s=&postid=1421986), I got a link to a small daemon utility called ifplugd (available at [http://www.stud.uni-hamburg.de/users/lennart/projects/ifplugd/](http://www.stud.uni-hamburg.de/users/lennart/projects/ifplugd/)). This wee process will detect if a connection has been removed from a network interface, and will automatically bring the interface down; it'll also detect if a connection is restored, and automatically bring the interface up again.

I've tested this out on one of our laptops, and it has circumvented the problem we were having; if anyone else is having the same issue, I highly recommend giving ifplugd a go (there's even an Ubuntu package for it).


John

---

