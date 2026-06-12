---
title: "Bridged wlan-lan-accesspoint not working from wlan"
date: 2013-06-04
forum: Networking &amp; Wireless
---

### Post by Nadjita on 2013-06-04
Hey there!

I've been a FreeBSD-user for more than a decade. I've always kept an eye on Linux and lately especially kubuntu (for my desktop) and ubuntu. I've replaced all my FreeBSD-clients with kubuntu and now the last bastion (my DSL-router which acts as access-point for wlan) is about to fall due to problems with zfs in conjunction with samba-shares. I'm experiencing problems with linux/ubuntu though, and hope you can help me.

Because I need to use DLNA/UPnP between the LAN and the WLAN, I'm currently bridging them together under FreeBSD. This works absolutely perfect. In Ubuntu, however, I'm not there yet.
I bridged together em1 and wlan0 (atheros chipset) into br0. I configured hostapd on wlan0 (with the nice bridge-option, so it plays well) and dnsmasq on br0 (the bridge). After thorough documentation-reading (including, but not limited to, several hours of trial and error) I got bridging to work. em1 and wlan0 don't have IP-addresses, only ppp0 and br0. My mobile-phones and notebooks can authenticate via wlan0, get IP-address from dnsmasq via br0 and my LAN-connections get IP-addresses and can use the internet without problems. What's not working is internet from wireless-devices. The server has a DSL-modem attached and configured via PPPoE on the second la-adapter, so clamp-mss is automatically being added (if this is of any relevance). I can ping hosts on the internet from my wireless-devices up to ping -s 1396, but as soon as I increase the size to 1397 or above, I get 100% packet loss. Needless to say that the same happens to all HTTP-requests from mobile devices, so internet is basically not working. From LAN however, it all works perfectly.

After hours of googling and fiddling with the configurations, I found out that setting "[COLOR=#000000]fragm_threshold" in /etc/hostapd.conf to a very low value (around 256) **seems** to solve this problem. I haven't found out why though and if it's the "correct" solution and haven't put it to stress-test yet. Not understanding why something does something or even what this something does is quite bad from my experience, because it leads to unexpected "surprises". I haven't heard of anyone else with this issue, so I'm assuming, I've made a terrible mistake and cannot see the forest for the trees.

So the questions are:

1. What is the correct(tm) way of bridging em1 with wlan0?

2. Why does that fragm_threshold seem to solve the problem and what exactly does this option do?

Please help a poor soul returning to Linux after a very long absence [/COLOR];)

---

