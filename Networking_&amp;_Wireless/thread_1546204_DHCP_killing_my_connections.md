---
title: "DHCP killing my connections?"
date: 2010-08-04
forum: Networking &amp; Wireless
---

### Post by mdingler on 2010-08-04
Due to our old Cisco firewall deteriorating rapidly last Friday, I had to come up with a temporary solution for my company. I generally try to keep things running there, but I'm really a programmer, not a sysdadmin, so for some things I feel a bit out of my depth. That's why I tried to get a prefab router/firewall distro instead of messing around with iptables myself.

Anyway, I used an old HP server with 6 ethernet ports, 5 of which are in use right now. I've installed eBox on it (a derivate of Ubuntu 8.04 LTS). Everything went okay, basically everything's working well enough until I get time to install a Cisco replacement.

With one exception: One of the subnets exhibits frequent connection problem to the other ones (which includes the internet, of course). I moved the subnet to another ethernet card, changed switches and cables -> doesn't help. So right now I don't assume it's a hardware problem. 

The usual scenario: All of a sudden the connections are gone, other subnets can talk to each other in the mean time. After 1-10 minutes (mostly 2), everything's back to normal. dmesg doesn't show any errors (only iptables output).

What I did notice, is that almost every outage is preceded by some entries by the DHCP daemon. I first thought this came after everything's back to normal and the machines would get new IPs, but it actually seems to cause the problems. I could reproduce this with the wireless of my laptop. 

DHCP Daemon is ISC DHCP 3.0.16.

One example from the log file:
```
Aug  4 21:57:39 gw dhcpd: DHCPREQUEST for 192.168.5.108 from <MAC> via eth5: wrong network.
Aug  4 21:57:39 gw dhcpd: DHCPNAK on 192.168.5.108 to <MAC> via eth5
Aug  4 21:57:40 gw dhcpd: DHCPDISCOVER from <MAC> (Vins-iTouch) via eth5
Aug  4 21:57:40 gw dhcpd: DHCPOFFER on 172.16.4.199 to <MAC> (Vins-iTouch) via eth5
Aug  4 21:57:41 gw dhcpd: Wrote 11 leases to leases file.
Aug  4 21:57:41 gw dhcpd: DHCPREQUEST for 172.16.4.199 (172.16.4.1) from <MAC> (Vins-iTouch) via eth5
Aug  4 21:57:41 gw dhcpd: DHCPACK on 172.16.4.199 to <MAC> (Vins-iTouch) via eth5
```

I might be looking at the wrong spot here, although it was the only way I could reproduce things. I don't even know how that would be possible.

Not very likely that I'll get an immediate explanation here, but any help in looking for spots where to look for more hints would be more than welcome. Ebox itself isn't too strong on monitoring, and apart from the log entries, the files in /var/log haven't been very helpful.

---

