---
title: "dhclient3 segmentation fault"
date: 2009-07-14
forum: Networking &amp; Wireless
---

### Post by mjf on 2009-07-14
When I reboot my Ubuntu 8.10 Desktop, I end up without an active Internet connection, and I run dhclient3 to try to get one.  (I used to directly connect to my ISP by running pon dsl-provider, but I have since installed a router which directly connects to the ISP instead.  I think the Ubuntu box still thinks it is in the old configuration which is why I must manually run dhcp now.)

However, running dhcp-client3 from a gnome-terminal results in a segfault (output pasted below).  I discovered that booting into single-user mode and running dhclient3 results in an active connection; and then running telinit 5 to get back into X works fine.

Any thoughts on what could be going wrong?  Thanks.

$ sudo dhclient3
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/pan0/6a:28:1e:77:14:fe
Sending on   LPF/pan0/6a:28:1e:77:14:fe
Listening on LPF/eth0/00:11:d8:eb:77:7f
Sending on   LPF/eth0/00:11:d8:eb:77:7f
Sending on   Socket/fallback
DHCPDISCOVER on pan0 to 255.255.255.255 port 67 interval 6
DHCPREQUEST of 192.168.1.104 on eth0 to 255.255.255.255 port 67
DHCPACK of 192.168.1.104 from 192.168.1.1
/sbin/dhclient-script: line 155:  6682 Segmentation fault      ifconfig $interface inet $new_ip_address $new_subnet_arg $new_broadcast_arg $mtu_arg

---

