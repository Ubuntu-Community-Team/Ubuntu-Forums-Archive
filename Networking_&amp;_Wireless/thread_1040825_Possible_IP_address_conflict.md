---
title: "Possible IP address conflict?"
date: 2009-01-15
forum: Networking &amp; Wireless
---

### Post by jdfoote on 2009-01-15
I am having some strange network problems - most of the time, my Internet connection is great - it just speeds along. Some of the time, however, it slows down *dramatically.*

I am pretty useless when it comes to networks, especially on Ubuntu, but I have been reading forum posts, and think that I may have an IP conflict with my neighbors who are on the same router.

I thought that the best solution would be to just set a static IP that is outside of the DHCP range, but when I open /etc/network/interfaces there is no entry for wlan0.

When I run ifconfig, however, wlan0 shows up, and I believe that is the interface that I am using (I have a USB-connected external wireless card).

So, my main question is - how can I set a static IP address without using /etc/network/interfaces, but the related question is - why isn't wlan0 showing up there?

Any help would be **greatly** appreciated.

Thanks!

---

### Post by superprash2003 on 2009-01-16
for ubuntu 8.10 - static ip [http://www.prash-babu.com/2009/01/how-to-setup-static-ip-in-ubuntu.html](http://www.prash-babu.com/2009/01/how-to-setup-static-ip-in-ubuntu.html)

---

