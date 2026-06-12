---
title: "Wi-Fi has gone insane, any way to fix it?"
date: 2012-01-28
forum: Networking &amp; Wireless
---

### Post by davethewave83 on 2012-01-28
my Wi-Fi is at it again, it is connecting, then disconnecting on it's own repeatedly within a minute or two interval. At times it pops up the WPA key request and has it already inserted, so I press okay. It connects, then disconnects a minute later, then says it's a bad password (even though it was connected just fine a minute ago). It's gone insane. 

The Wi-Fi quality goes up and down while connected, from 80% to 40% 

I tried uninstalling network manager and using Wicd instead, but it behaved even worse, connecting for only about 10-20 seconds before disconnecting. so I re-installed network manager and uninstalled Wicd (it still starts at boot up even though I removed it) so I have two wi-fi programs running now.

I checked the /etc/network/interfaces file and there is nothing except the lo loopback

there is no reference to my wi-fi or eth0 eth1 or anything, could this be what is causing it?

it's also very slow

---

