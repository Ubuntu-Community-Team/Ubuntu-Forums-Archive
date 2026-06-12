---
title: "Setting up a WDS with hostapd"
date: 2012-05-28
forum: Networking &amp; Wireless
---

### Post by TVicarelli on 2012-05-28
Hi,
I'm trying to realize a Wireless network with 2 access points and a WDS (Wireless Distribution System) between them.

I configured the 2 PCs as access points and it's ok. I could connect with both without any problem.
I try to configure the wds but it doesn't work! I created a new wds  interface and I set the peer using the mac address of the other access  point. I found this instruction in this documentation:  [http://linuxwireless.org/en/users/Documentation/modes](http://linuxwireless.org/en/users/Documentation/modes)
The commands that i used are:

sudo iw phy phy0 interface add wds0 type wds
sudo iw dev wds0 set peer [MAC ADDRESS]

The interface phy0 is the physical interface of wlan0 where is active hostapd.
I did it in both access points.
The system didn't give me any error but it doesn't work.

Have you any ideas?

 Help me, please!

---

