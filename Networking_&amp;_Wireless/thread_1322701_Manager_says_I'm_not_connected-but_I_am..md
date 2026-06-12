---
title: "Manager says I'm not connected-but I am."
date: 2009-11-11
forum: Networking &amp; Wireless
---

### Post by hugh v. angle on 2009-11-11
I suddenly loose the network. The log ( /etc/log/daemon.log) has
the message that the avahi-daemon is "withdrawing address
record for 192,168.1.101".  And, 'ifconfig' no longer list my IP address.
I run 'dhclient' and I am back on the network. What is happening?


I upgraded to Karmic about three weeks ago. Everything went well
until I disconnected my computer from the router and went
directly to the modem. A red x appeared on my network manager
icon and the message "no network connection" appeared. Over
a period of three days, I tried various solutions that were
suggested by the forum to users who were having network problems.
Yesterday, out of frustration,  I tried to access a web
page and discovered that I was connected to the network in
spite of the fact that the network manager indicated
that I was not. Going through the list of solutions to recover
the second time,  I discovered that 'dhclient' does the trick,
which I should have known since 'avahi' is associated with
the DHCP.

I know that I am not out of the woods until the red 'x' goes
away. What is keeping it around?

____________________________________________________________________
                daemon.log

 DHCPREQUEST of 192.168.1.101 on eth0 to 192.168.1.1 port 67
 dhclient: DHCPACK of 192.168.1.101 from 192.168.1.1
 dhclient: bound to 192.168.1.101 -- renewal in 41943 seconds.
 NetworkManager: <info>  (eth0): carrier now OFF (device state 3)
 NetworkManager: <info>  (eth0): device state change: 3 -> 2 (reason 40)
 NetworkManager: <info>  (eth0): deactivating device (reason: 40).
 NetworkManager: <WARN>  check_one_route(): (eth0) error -34 returned from     rtnl_route_del(): Sucess#012
 avahi-daemon[1132]: Withdrawing address record for 192.168.1.101 on eth0.
 avahi-daemon[1132]: Leaving mDNS multicast group on interface eth0.IPv4 with address 192.168.1.101.
 avahi-daemon[1132]: Interface eth0.IPv4 no longer relevant for mDNS.
 NetworkManager: <info>  (eth0): carrier now ON (device state 2)
 NetworkManager: <info>  (eth0): device state change: 2 -> 3 (reason 40)
 NetworkManager: <info>  (eth0): carrier now OFF (device state 3)
 NetworkManager: <info>  (eth0): device state change: 3 -> 2 (reason 40)
 NetworkManager: <info>  (eth0): deactivating device (reason: 40).
 NetworkManager: <info>  (eth0): carrier now ON (device state 2)
 NetworkManager: <info>  (eth0): device state change: 2 -> 3 (reason 40)

---

