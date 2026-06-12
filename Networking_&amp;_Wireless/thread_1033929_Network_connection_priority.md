---
title: "Network connection priority"
date: 2009-01-07
forum: Networking &amp; Wireless
---

### Post by joshuapauljonah on 2009-01-07
I am connected to two networks, one via wireless and one via wired ethernet. I do this to share files with my neigbour, we're both geeks and like to share things with each other. I'm not just stealing his wireless. 

Both networks have separate internet connections. When i go to [http://whatismyip.com](http://whatismyip.com), it has the IP for his ISP, not mine.

How do i configure the wired connection to be my primary connection?

I'm using 8.10.

---

### Post by olmecnz on 2009-10-30
I have a similar issue in that I want to force which connection is used for web traffic.

My setup is slightly different.

I have a mobile broadband 3G cellular wireless usb device as my internet connection

I have wireless local network on fixed IP address system (not DHCP)

I have firestarter firewall running with internet connection sharing turned on and the appropriate network devices set for shared and web connections

This is so that my other laptop can connect to the internet via the local wireless network using the USB mobile broadband connection of the primary computer.

I have had this working well in ubuntu 9.04 I have recently upgraded to 9.10 (admittedly via beta and then regular updates)

Currently it only allows me to connect to the  web from the primary computer if I disable the wireless connection. Or if I enable the connections in the correct order.

---

### Post by Iowan on 2009-10-30
I saw a thread about changing the metrics to give one interface preference over the other - but don't remember where/when.

---

### Post by njparton on 2010-06-01
I'd like to give my wireless a higher priority than my wired connection.  
 
Any further pointers on metrics?

---

### Post by tech.kyle on 2010-08-18
Different situation, same problem. I'd like to rely on eth0 when it's up and fall back to wifi0 when eth0 goes down.
They're both the same network. It would be nice if I could even keep the same IP address.

It's another one of those "I know how to do it in Windows, now how do I do it in Ubuntu?" moments. How do we set network connection priority and is it possible to set them up as a redundant links rather than two seperate connections? Bonus points, is it possible to do load ballancing between the two?

---

