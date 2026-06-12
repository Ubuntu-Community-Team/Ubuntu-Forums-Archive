---
title: "broadcom sta driver disabled and not working after update"
date: 2010-10-02
forum: Networking &amp; Wireless
---

### Post by coredatarecovery.com on 2010-10-02
I applied the latest updates today and when I rebooted, My wireless broadcom driver is not working and the ifconfig does not list it either anymore, was working 8 min ago but is now dead. If I turn off the wireless with a switch and back on, I get a blue light but it remains disabled and greyed out on the network icon.

Ubuntu 10.04, latest updates applied daily.

I removed the driver and reinstalled it, it did not help at all.

Also, my Truecryt gdecrypt stopped working.


Update: it seems the wireless switch on the front of the laptop is now working backwards, in checking the daemon log I found

Turning off the wifi so the light goes out:

Oct  2 20:09:18 chuck-laptop NetworkManager: <info>  WiFi now enabled by radio killswitch
Oct  2 20:09:18 chuck-laptop NetworkManager: <info>  (eth1): bringing up device.
Oct  2 20:09:18 chuck-laptop NetworkManager: <info>  (eth1): supplicant interface state:  starting -> ready
Oct  2 20:09:18 chuck-laptop NetworkManager: <info>  (eth1): device state change: 2 -> 3 (reason 42)
Oct  2 20:09:20 chuck-laptop avahi-daemon[880]: Registering new address record for fe80::216:44ff:fe7c:fe60 on eth1.*.

Turning the wifi ON the front of the computer so the light is on:

Oct  2 20:09:50 chuck-laptop NetworkManager: <info>  WiFi now disabled by radio killswitch
Oct  2 20:09:50 chuck-laptop NetworkManager: <info>  (eth1): device state change: 3 -> 2 (reason 0)
Oct  2 20:09:50 chuck-laptop NetworkManager: <info>  (eth1): deactivating device (reason: 0).
Oct  2 20:09:50 chuck-laptop NetworkManager: <info>  Policy set 'Auto eth0' (eth0) as default for routing and DNS.

Turning off the switch:

Oct  2 20:09:50 chuck-laptop NetworkManager: <info>  (eth1): taking down device.
Oct  2 20:09:50 chuck-laptop avahi-daemon[880]: Withdrawing address record for fe80::216:44ff:fe7c:fe60 on eth1.
Oct  2 20:10:05 chuck-laptop NetworkManager: <info>  WiFi now enabled by radio killswitch
Oct  2 20:10:05 chuck-laptop NetworkManager: <info>  (eth1): bringing up device.
Oct  2 20:10:05 chuck-laptop NetworkManager: <info>  (eth1): supplicant interface state:  starting -> ready
Oct  2 20:10:05 chuck-laptop NetworkManager: <info>  (eth1): device state change: 2 -> 3 (reason 42)
Oct  2 20:10:07 chuck-laptop avahi-daemon[880]: Registering new address record for fe80::216:44ff:fe7c:fe60 on eth1.*.

Update, I found that if I boot the laptop up with the networking switch off, then, after I'm booted up, turn it on, it works.

However if I reboot the laptop with the network switch in the on position I get the above issue with the switch being inverted and not working properly.

Weird issue. Does anybody have any suggestions or places for me to submit the bug?

---

### Post by jawahar on 2010-10-04
I've been having the same issue for a while now. Removing and reinstalling the driver only helps till the next boot.

---

### Post by raffen on 2010-11-26
Same problem here on a HP Mini running Ubuntu 10.10 with broadcom STA driver.  It was working brilliantly for a couple of weeks.  I was online using wireless then suddenly I lost the connection and haven't been able to get the wireless interface up ever since.  Full reinstall of 10.10 did not resolve issue.  

I can of course not rule out hardware failure but it's almost brand new so I suspect software failure. 

Nov 26 13:34:24 raff-mini NetworkManager[821]: <info> (eth1): bringing up device.
Nov 26 13:34:24 raff-mini NetworkManager[821]: <info> (eth1): supplicant interface state:  starting -> ready
Nov 26 13:34:24 raff-mini NetworkManager[821]: <info> (eth1): device state change: 2 -> 3 (reason 42)
Nov 26 13:34:26 raff-mini avahi-daemon[829]: Joining mDNS multicast group on interface eth1.IPv6 with address fe80::c617:feff:fe34:3273.
Nov 26 13:34:26 raff-mini avahi-daemon[829]: New relevant interface eth1.IPv6 for mDNS.
Nov 26 13:34:26 raff-mini avahi-daemon[829]: Registering new address record for fe80::c617:feff:fe34:3273 on eth1.*.
Nov 26 13:34:35 raff-mini kernel: [  286.560041] eth1: no IPv6 routers present

Let me add the HP Mini does not have a wireless kill switch so I cannot test that aspect.

---

