---
title: "Trouble with OpenVPN on multiple interfaces"
date: 2009-02-01
forum: Networking &amp; Wireless
---

### Post by HonoredMule on 2009-02-01
Some time ago, I set up my gateway machine running 8.10 with an OpenVPN tunnel server using certificate-based authentication, added a wireless card running in access-point mode on a separate subnet, and set up all the requisite routing/firewall rules (using IPTables directly).

It worked perfectly.  The gateway itself, private LAN on 192.168.0.x, and the public WLAN on 192.168.1.x could all access the PPPoE internet connection.  The WLAN and LAN could not communicate directly with each other in any way, but the WLAN and outside connections from the internet alike could authenticate with the VPN using any certificate I had signed to get an address on the 192.168.2.x subnet which freely routed to, from, and between both of the other internal subnets.

According to NetworkManager on my netbook, the last time I used the VPN over my wireless was nearly a month ago.  Now, when I try to connect over the WLAN, OpenVPN simply doesn't respond, and I can't find any indication in OpenVPN's logs that it was ever reached by the netbook.  No configuration had changed since I last used it internally, and I've been using the VPN from a remote location daily this whole time.  After much troubleshooting and trying to re-configure my way out of whatever happened, I discovered that I could once again connect over WLAN if I told OpenVPN to listen on 192.168.0.1.  But I still need to be able to use it remotely as well.

So my questions are:
1) Why did it stop working in the first place?
2) Is this a known regression from a recent update that will be fixed soon, and if not, how can I revert to before the update and prevent it from breaking again?
3) Is there a workaround that does not involve running two separate OpenVPN instances and/or overcomplicating my system setup at every level?

---

