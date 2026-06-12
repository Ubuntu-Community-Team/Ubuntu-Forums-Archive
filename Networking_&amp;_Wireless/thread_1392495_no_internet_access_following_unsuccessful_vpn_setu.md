---
title: "no internet access following unsuccessful vpn setup"
date: 2010-01-28
forum: Networking &amp; Wireless
---

### Post by jcalmighty on 2010-01-28
Hi, I'm relatively new to Linux and a bit embarassed to have to post what is possibly a really simple problem. I tried to setup a VPN connection to anonine using pptp, after trying to connect and failing I deleted the vpn connection. This seems to have interfered with my normal setup in that I no longer have access to the internet. I connect to my broadband router no probs as I am recieving an IP address via DHCP in the correct subnet however pings to the router fail and I cannot access it to check configuration, pinging loopback and my own address is successful.

On my windows partition there are no problems, the VPN is configured and internet access works. pings to the router are successful and I can access the router configuration via firefox. I am using Ubuntu 9.10 with an Intel(R) 82562V-2 10/100 NIC.

If anyone can help I'd be very grateful as I feel a bit like I'm bashing my head against a wall.

If I do a network reload I get the following output

   * Reconfiguring network interfaces...
  There is already a pid file /var/run/dhclient.eth0.pid with pid 3034
  killed old client process, removed PID file
  Internet Systems Consortium DHCP Client V3.1.2
  Copyright 2004-2008 Internet Systems Consortium.
  All rights reserved.
  For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)
  
  parse_option_param: Bad format a
  Listening on LPF/eth0/00:21:9b:0e:c7:4d
  Sending on   LPF/eth0/00:21:9b:0e:c7:4d
  Sending on   Socket/fallback
  DHCPRELEASE on eth0 to 192.168.1.254 port 67
  Internet Systems Consortium DHCP Client V3.1.2
  Copyright 2004-2008 Internet Systems Consortium.
  All rights reserved.
  For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)
  
  Listening on LPF/eth0/00:21:9b:0e:c7:4d
  Sending on   LPF/eth0/00:21:9b:0e:c7:4d
  Sending on   Socket/fallback
  DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
  DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 13
  DHCPOFFER of 192.168.1.64 from 192.168.1.254
  DHCPREQUEST of 192.168.1.64 on eth0 to 255.255.255.255 port 67
  DHCPACK of 192.168.1.64 from 192.168.1.254
  bound to 192.168.1.64 -- renewal in 39434 seconds.
  
  

 "There is already a pid file /var/run/dhclient.eth0.pid with pid 3034 killed old client process, removed PID file". and "parse_option_param: Bad format a" seem as if they could be issues.

---

### Post by Everton Krystian on 2010-08-02
In this case i'm solved following steps on this how-to:

[http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg1196464.html](http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg1196464.html)

I'm hope to help you.

---

