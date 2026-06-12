---
title: "Cannot connect to internet using wired connetion"
date: 2011-05-14
forum: Networking &amp; Wireless
---

### Post by me12 on 2011-05-14
Im trying to connect to the internet through a wired link to a bthomehub
every time i try and connect i get this:

May 14 23:08:28 ubuntu dhclient: Internet Systems Consortium DHCP Client 4.1.1-P1
May 14 23:08:28 ubuntu dhclient: Copyright 2004-2010 Internet Systems Consortium.
May 14 23:08:28 ubuntu dhclient: All rights reserved.
May 14 23:08:28 ubuntu dhclient: For info, please visit [https://www.isc.org/software/dhcp/](https://www.isc.org/software/dhcp/)
May 14 23:08:28 ubuntu dhclient: 
May 14 23:08:28 ubuntu NetworkManager[855]: <info> (eth0): DHCPv4 state changed nbi -> preinit
May 14 23:08:28 ubuntu dhclient: Listening on LPF/eth0/00:24:8c:e6:3f:6d
May 14 23:08:28 ubuntu dhclient: Sending on   LPF/eth0/00:24:8c:e6:3f:6d
May 14 23:08:28 ubuntu dhclient: Sending on   Socket/fallback
May 14 23:08:28 ubuntu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
May 14 23:08:30 ubuntu dhclient: DHCPOFFER of 192.168.1.227 from 192.168.1.254
May 14 23:08:30 ubuntu dhclient: DHCPREQUEST of 192.168.1.227 on eth0 to 255.255.255.255 port 67
May 14 23:08:31 ubuntu dhclient: DHCPNAK from 192.168.1.254
May 14 23:08:33 ubuntu dhclient: DHCPREQUEST of 192.168.1.227 on eth0 to 255.255.255.255 port 67
May 14 23:08:33 ubuntu dhclient: DHCPNAK from 192.168.1.254
May 14 23:08:39 ubuntu dhclient: DHCPREQUEST of 192.168.1.227 on eth0 to 255.255.255.255 port 67
May 14 23:08:39 ubuntu dhclient: DHCPNAK from 192.168.1.254
May 14 23:08:53 ubuntu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
May 14 23:08:54 ubuntu dhclient: DHCPOFFER of 192.168.1.227 from 192.168.1.254
May 14 23:08:54 ubuntu dhclient: DHCPREQUEST of 192.168.1.227 on eth0 to 255.255.255.255 port 67
May 14 23:08:55 ubuntu dhclient: DHCPNAK from 192.168.1.254
May 14 23:08:57 ubuntu dhclient: DHCPREQUEST of 192.168.1.227 on eth0 to 255.255.255.255 port 67
May 14 23:08:57 ubuntu dhclient: DHCPNAK from 192.168.1.254
May 14 23:09:01 ubuntu dhclient: DHCPREQUEST of 192.168.1.227 on eth0 to 255.255.255.255 port 67
May 14 23:09:01 ubuntu dhclient: DHCPNAK from 192.168.1.254
May 14 23:09:12 ubuntu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
May 14 23:09:13 ubuntu NetworkManager[855]: <warn> (eth0): DHCPv4 request timed out.
May 14 23:09:14 ubuntu NetworkManager[855]: <info> (eth0): canceled DHCP transaction, DHCP client pid 2370
May 14 23:09:14 ubuntu NetworkManager[855]: <info> Activation (eth0) Stage 4 of 5 (IP4 Configure Timeout) scheduled...
May 14 23:09:14 ubuntu NetworkManager[855]: <info> Activation (eth0) Stage 4 of 5 (IP4 Configure Timeout) started...
May 14 23:09:14 ubuntu NetworkManager[855]: <info> (eth0): device state change: 7 -> 9 (reason 5)
May 14 23:09:14 ubuntu NetworkManager[855]: <info> Marking connection 'Auto eth0' invalid.
May 14 23:09:14 ubuntu NetworkManager[855]: <warn> Activation (eth0) failed.
May 14 23:09:14 ubuntu NetworkManager[855]: <info> Activation (eth0) Stage 4 of 5 (IP4 Configure Timeout) complete.
May 14 23:09:14 ubuntu NetworkManager[855]: <info> (eth0): device state change: 9 -> 3 (reason 0)
May 14 23:09:14 ubuntu NetworkManager[855]: <info> (eth0): deactivating device (reason: 0).

the homehub says its conneted yet ubuntu says its not
im using version 11.04

---

### Post by chili555 on 2011-05-14
Perhaps this will help: [http://community.bt.com/t5/BB-Speed-Connection-Issues/BT-HomeHub-firmware-upgrade-broken-network-connectivity-Ubuntu/td-p/176473/page/9](http://community.bt.com/t5/BB-Speed-Connection-Issues/BT-HomeHub-firmware-upgrade-broken-network-connectivity-Ubuntu/td-p/176473/page/9)

---

