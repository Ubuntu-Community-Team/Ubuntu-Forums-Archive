---
title: "VPN connection routing question"
date: 2009-12-09
forum: Networking &amp; Wireless
---

### Post by bigheart on 2009-12-09
Hi,
first of all, i am using 32bit Ubuntu 9.10 .i failed to use the GUI network manager to setup my PPTP connection. i end-up to use the manual method in [http://pptpclient.sourceforge.net/howto-debian.phtml](http://pptpclient.sourceforge.net/howto-debian.phtml)
and it is successful ..

however, after i tested the pptp client can ping the NAS in the remote network, ssh also OK, but i found i cannot use the web interface of the NAS ...
i follow the following 
[http://pptpclient.sourceforge.net/routing.phtml#automatic-setup](http://pptpclient.sourceforge.net/routing.phtml#automatic-setup)
to setup the routing ...
and it is my routing table
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.1     *               255.255.255.255 UH    0      0        0 ppp0
119246039114.ct 10.0.34.254     255.255.255.255 UGH   0      0        0 eth0
192.168.1.0     *               255.255.255.0   U     0      0        0 ppp0
10.0.34.0       *               255.255.255.0   U     0      0        0 eth0
link-local      *               255.255.0.0     U     1000   0        0 eth0
default         10.0.34.254     0.0.0.0         UG    100    0        0 eth0

192.168.1.0 is my remote network.

i guss it should be some problem in the routing but if it is wrong how can i get the ssh connection!?
really have no idea, anyone can help?

thanks!!

Joseph

---

