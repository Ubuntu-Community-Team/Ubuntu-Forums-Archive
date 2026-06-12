---
title: "Dual Network: Wireless + LAN, and DNS priority."
date: 2013-04-30
forum: Networking &amp; Wireless
---

### Post by guice on 2013-04-30
I'm trying to find a way to made one particular interface, and it's DHCP settings, priority over another in regards to DNS lookup.

I have a laptop that's connected to two networks, one via Wireless, and one via Ethernet. My routing is find, I route all 10.x addresses through wlan0 and default 0.x through my eth0. However, I'm having trouble with DNS. I can't seem to find a way to make wlan0 as my priority network for DNS resolution. /etc/nsswitch.conf doesn't differentiate by device. and /etc/resolve.conf is dynamically updated based on primary device, right now it's eth0 set to 192.168.1.1.

How can I make my wireless network my primary device (for DNS). I can handle in general, and manually updated the routing table to change default route to network cable.

*This is solved (but I can't mark thread as "SOLVED"):  /etc/resolvconf/interface-order defines the DNS interface order. I put wlan* above eth* and it's working perfectly.

---

### Post by Iowan on 2013-04-30
You might be able to use the **prepend domain-name-servers** line in */etc/dhcp/dhclient.conf* - IF only one interface (wlan0) has internet access.
That won't necessarily force DNS to use wlano if eth0 can also reach internet.

Network Manager also lets you specify a DNS server by interface...

---

### Post by guice on 2013-05-01
That's my problem: I have two active connections, one on 10.x network, other on 192.x network. Both have internet access. I want to use DNS on 10.x network cause that's more of an internal network, and contains DNS entries for intranet hostnames. Here's the kicker: wifi could be also on a single network in other networks, so hard coding DNS won't work.

DNS seems to work, but sporadically -- it's not reliable. In Windows 7, I was able to make my wifi my priority connection, having Windows rely on wifi DNS settings. No way via Ubuntu?

---

### Post by guice on 2013-05-03
I found my answer: /etc/resolvconf/interface-order

I edited that file and put wlan* above eth*. Now it will use my wlan0 DNS over eth0. It's working perfectly! I did have to reboot to get the changes to notice -- I tried restarting the network, but that didn't affect anything.

---

