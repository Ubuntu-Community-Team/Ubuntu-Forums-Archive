---
title: "DHCP3 for multipul subnets with 1 interface"
date: 2013-05-20
forum: Networking &amp; Wireless
---

### Post by ataylor1988 on 2013-05-20
I have been looking all over and i cannot find a good post or anything on this.

Currently i am trying to test a ubuntu server 12.04 deployment as a DHCP server for 13 different subnets

Currently i just have 1 setup to try and test with.  The server starts fine.  But the syslog reports the following.  I think this is hitting the log everytime a request gets sent to it.

No subnet declaration for eth0 (10.206.201.100).
** Ignoring requests on eth0.  if this is not what you want, please write a subnet declaration in your dhcpd.conf file for the entwork segment to which interface eth0 is attached

The subnet the server is in will be a server/network equipment only subnet.  which means all devices on this subnet will be static.  which is why i do not have a dhcp declaration for that subnet?
Do i need this for it to give out addresses for machine on different subnets?

I have dhcp relays setup on my cisco equipment i am testing with.  i believe that portion of this test is configured properly.

I could really use some help on this quick.  I am rolling out this system in a week.  and dont want to have to try and make this all work with windows server

---

