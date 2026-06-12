---
title: "Using Network Manager to Share Wireless Connection with Wired"
date: 2012-02-28
forum: Networking &amp; Wireless
---

### Post by alphasynaptic on 2012-02-28
So I followed the directions at [https://help.ubuntu.com/community/Internet/ConnectionSharing](https://help.ubuntu.com/community/Internet/ConnectionSharing) in the section labeled "GUI Method via Network Manager (Ubuntu 9.10 and up)".

I have exactly the circumstances the instructions suggest will work.

comp1:
Ubuntu 11.10 using Gnome Classic(no effects)
wlan0->router->internet
eth0->comp2 via crossover

wlan0 has its ipv4 information all set manually.
eth0 is set to "Shared to other computers"

Ipv6 is set to ignore for eth0.
Otherwise both connections use default settings.

Now for the client.

comp2:
Also running 11.10 with Gnome Classic(no effects)
eth0->comp1 via crossover

eth0 has ipv4 setting set to DHCP auto and ipv6 setting set to ignore.

comp1.eth0 has been assigned 10.42.43.1 which seems a bit odd to me but could be irrelevant
comp2.eth0 has been assigned 10.42.43.10

both connections show active but comp2 can't ping comp1 via 10.42.43.1 and will certainly not load a page in firefox

doing a killall dnsmasq on comp2 says it's not installed.
doing the same on comp1 kills the process.
refreshing comp2.eth0 connects right back up but still doesn't allow network access

turning my configured Firestarter firewall on allows comp2.eth0 to hit the internet but if comp2 is rebooted, the firewall bust be stopped, comp2.eth0 restarted, then the firewall must be turned back on to hit the net.

while this kind of works, it isn't feasible given that I wish for comp2 to have internet access without touching comp1 as the two machines have different users.

help?

---

