---
title: "Extremely slow wireless connection"
date: 2010-11-14
forum: Networking &amp; Wireless
---

### Post by pschalkx on 2010-11-14
Good day,

I'm moving my Ubuntu 10.04 desktop from the wired network to my wireless network, and the connection is so slow that it's unusable.
Machine is an HP7260, aand doesn't show any proprietary drivers.

As a reference, I did the following checks:
1) Just after reboot + login I can ping google.com. After a few minutes, pinging google just times out.
2) Just after reboot + login the browser will download the home page. After that, loading any other url will time out.
3) When I ping I see that the ICMP packets sequence jumps numbers: 17, 25, 29.... 
4) When I go back to wired network all works fine, and ICMP packets are in sequence: 1, 2, 3 ...

5) I also have a laptop, also with Ubuntu 10.04 that works perfectly fine on the wireless network.
6) The machine is double boot and in Windows it shows a USB wireless network adapter with a driver made by Gemtec. Under windows the machine works fine on the wireless network.

Based on the above I would say that hardware is working OK and that my ADSL modem is not doing anything funny, and that for some reason, the wireless connection of the PC is flaky under Ubuntu and looses packets.

Is there some setting I'm not aware of? Where else can I look for a cause?

Rgds,

Philip

---

