---
title: "Default routing problem after rising second eth i-face"
date: 2010-06-28
forum: Networking &amp; Wireless
---

### Post by dr_fred@zababki.ru on 2010-06-28
Hi guys,

I definitely need your help as I can't find the reason myself. The problem is as described below (Ubuntu server 10.04).

One network  interface stops responding when I'm starting the second interface. After eth1 is up I get the following routing table with 2 default routes:

1.2.3.80/28 dev eth1  proto kernel  scope link  src 1.2.3.93 
1.2.3.80/28 dev eth0  proto kernel  scope link  src 1.2.3.94 
default via 1.2.3.81 dev eth0                                   
default via 1.2.3.81 dev eth1   

(IPs are changed in their first part not to show real ones).

or like this (with metrics):

~# ip route
1.2.3.80/28 dev eth0 proto kernel scope link src 1.2.3.94
1.2.3.80/28 dev eth1 proto kernel scope link src 1.2.3.93 metric 100
default via 1.2.3.81 dev eth0
default via 1.2.3.81 dev eth1 metric 100 

If I delete one default gw as following, both interfaces become available (pingable, ssh-able etc.):

:~# ip route
1.2.3.80/28 dev eth1  proto kernel  scope link  src 1.2.3.93
1.2.3.80/28 dev eth0  proto kernel  scope link  src 1.2.3.94
default via 1.2.3.81 dev eth0

The default gw IP is correct but I get 2 of them. 

Questions are: 

1) what to tune to get only ONE default route after 'ifup eth1'?
2) is it normal - to get 2 default routes or it's abug?

# cat /etc/network/interfaces
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp


And one more thing (not sure it's important) - Ubuntu server instance is running under Xen 3.4.

Thanks in advance! I'd appreciate any advices.


--
Fedor.

---

### Post by Iowan on 2010-06-28
The two default routes (gateways) might be a problem. Which interface *should* receive default traffic? Are both interfaces in the same subnet?
[This]("http://ubuntuforums.org/showthread.php?t=1508791") thread *might* provide some insight...

---

### Post by dr_fred@zababki.ru on 2010-06-29
Hi Iowan,

Thanks for answering and the link, checking the thread now.

Default traffic should remain on eth0 and eth1 should be available. Btw, I see no problems with the same set-up on Centos instances.

Yes, same subnet. IPs are received via DHCP

--
Fred.

---

