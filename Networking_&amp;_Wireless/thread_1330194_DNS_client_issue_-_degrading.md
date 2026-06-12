---
title: "DNS client issue - degrading"
date: 2009-11-18
forum: Networking &amp; Wireless
---

### Post by daveyt on 2009-11-18
I'm running 8.10, upgraded from 8.04 a few months ago, its 64 bit desktop. Mostly works ok most of the time, no serious problems up to now.

A couple of days ago, I lost internet activity - specifically I cant do DNS lookups, local LAN access is fine, and the box is accessible to clients via samba, ftp anything. But the box itself will not do any kind of lookup. It has a DHCP assigned IP and DNS etc, and tried manual - all ok. 

I have a VMware XP session running on this box, and that works perfectly, doing its own DNS lookups.

Today, I noticed that now that XP VM can now no longer access the net.

Other (windows) PC's on my home network are unaffected, the internet connection, router etc are working normally. The Ubuntu is getting slowly worse.

I notice since the 8.10 upgrade, there is a network configuration icon in the upper right task bar, with a little cross on it - claiming there is no connections. But when i choose edit connection, I can see my eth1 card and change the settings as needed. It has been like that long before this problem though.

Any one have any suggestions? Thanks

edit: have added manual nameserver entries to /etc/resolv.conf and this appears to improve things. I'm left with the issue as to why this box doesnt want to use my router as a DNS server - all the other clients use it fine and so did this box until a few days ago.

---

