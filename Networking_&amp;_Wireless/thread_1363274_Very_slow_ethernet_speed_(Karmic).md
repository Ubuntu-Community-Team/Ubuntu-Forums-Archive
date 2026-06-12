---
title: "Very slow ethernet speed (Karmic)"
date: 2009-12-24
forum: Networking &amp; Wireless
---

### Post by aryangor on 2009-12-24
Hey guys!

I need to transfer about 60Gb from my desktop to my laptop. Since I dont have an external, My only options  to transfer the files would be a DVD-RW (that would take ages!) or LAN.

Now, I connected both desktop and laptop, but the speed of transfer is about 30Kb/s - pathetic!!! I have no idea where to look for a solution. Also I can see my laptop from my desktop (via Samba), but not my desktop from my laptop.

Desktop: Kubuntu 8.10
Laptop: Ubuntu 9.10

:~& cat /etc/network/interfaces
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 170.0.0.1 (170.0.0.2 for laptop)
netmask 255.255.255.0
--------------
Thanks! :)

---

### Post by aryangor on 2010-06-07
wow! nobody dared answering yet!! :)

anyway i suspect the cable i was using back then is not meant for such high speeds, so that might have been the problem....

---

### Post by coskierken on 2010-06-07
You did not give enough info.  What cable did you connect the two computers with?  If it was an ethernet cable, it had to be a crossover cable or it will be very slow.  The best way is through a router or a switch.  You can do a wireless adhoc connection, also.  Hope this helps!

Ken

---

