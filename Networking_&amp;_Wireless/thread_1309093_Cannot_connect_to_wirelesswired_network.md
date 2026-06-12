---
title: "Cannot connect to wireless/wired network"
date: 2009-11-01
forum: Networking &amp; Wireless
---

### Post by contedel on 2009-11-01
Dear All,
       My Ubuntu won't connect to any network displayed in the netowrk manager.
I have been running Ubuntu 9.04 on the same hardware and never had any problem with networking. Both wired and wireless connections worked out of the box.
Yesterday I installed 9.10 from scratch and I cannot connect to the network anymore (ETH0 and wireless network do appears in my network manager, they simply don't connect)
I decided to reinstall from scratch 9.04 again (as it used to work) and now even 9.04 shows the same problem! :)
I also use vista on the same hardware (PC + router) and I can use wired and wireless connection with it.
I don't have network problems either when I run Ubuntu from the cd (both 9.04 and 9.10). It happens only after the installation.

Any idea?

I tried to "restart the network" and this is the output

 * Reconfiguring network interfaces...                                                             Internet Systems Consortium DHCP Client V3.1.2
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/00:24:1d:12:91:83
Sending on   LPF/eth0/00:24:1d:12:91:83
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
Discarding packet with bogus hlen.
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
Discarding packet with bogus hlen.
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
Discarding packet with bogus hlen.
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 21
Discarding packet with bogus hlen.
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
Discarding packet with bogus hlen.
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
Discarding packet with bogus hlen.
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

I'll attach also the output of lshw -C network and the output of dmesg


Thanks in advance,
                     contedel

---

