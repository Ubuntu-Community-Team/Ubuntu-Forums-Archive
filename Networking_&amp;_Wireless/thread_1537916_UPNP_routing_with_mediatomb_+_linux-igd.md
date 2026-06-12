---
title: "UPNP routing with mediatomb + linux-igd"
date: 2010-07-24
forum: Networking &amp; Wireless
---

### Post by atoma on 2010-07-24
Hi All,

I've been fighting with this for too long, now.

I'm running the current setup:

D-Link Wireless AP/router/modem on 192.168.1.1/24
MediaTomb running on one lucid machine cable connected to the D-Link via eth0 on 192.168.1.2/24
Another lucid machine with Hostap running on wlan0 192.168.2.1/24 and eth0 cable connected to the D-Link via eth0 on 192.168.1.7/24

Now the issue:

All wireless and wired clients connected to the D-Link are able to access contents shared by MediaTomb. No wireless client connected to Hostap does.
At first I thought it was a UPNP routing issue and turned to linux-igd.
But after installing and configuring it nothing has changed.
Specifically, I don't see any rule added in iptables by linux-igd after start (is it supposed to add rules only as a response to some event?)
Nothing appears in debug log after the

upnpd[3220]: Advertisements Sent.  Listening for requests ...

message is printed if I either start the server (MediaTomb) or a client (XBMC or PS3) on the 192.168.2.0/24 wireless network.

I followed many tutorials and direction found around the web with no luck.

I tried to disable the firewall on the Hostap machine (I'm running arno-iptables-firewall with UPNP enabled) with no result.

I followed directions for manual iptables setup found in
[http://www.gentoo-wiki.info/HOWTO_Setup_UPnP_with_IPTables](http://www.gentoo-wiki.info/HOWTO_Setup_UPnP_with_IPTables)
and nothing happened.

Has anybody out there a similar setup (MediaTomb and clients on two separate networks)? What should the router configuration be? Can this even be done?

Please, advice.

Regards.
Antonio.

---

