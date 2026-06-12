---
title: "Why can only root enable wireless device eth1?"
date: 2006-02-09
forum: Networking &amp; Wireless
---

### Post by hyperpsyched on 2006-02-09
Hi...

When i bot up as a user Kubuntu can not access the wireless network, or the router or something. There is simply nothing happening when I open the wireless manager. The only way to get the wireless card eth1 enabled is to log into root, open network settings and then enable the card from that gui type thing. Of course it automatically claims the card is not enabled but it connects to the router nonetheless (is this a common complaint?). After this, still as root, I need to run "dhclient eth1" to get it to resolve the ip, etc... This is impossible to do (from the gui anyway) using my user account because from the window where I am supposed to be able to enable the wireless NIC everything is greyed out and when I look for the Administrator Mode button (says to use it at the top of the window) it is nowhere to be found. Someone has a twisted sense of humour.

'breath... find your happy place... continue...'

Anyway, in both the window that does the enabling for the card and the window where I config my wireless network everything is ticked off to start at boot up.

Here is my etc/net.../interfaces file:

# The loopback network interface
auto lo
iface lo inet loopback
address 127.0.0.1
netmask 255.0.0.0

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
	script grep
	map eth1

iface eth1 inet dhcp
wireless-essid darwin
wireless-key **************************

auto eth1

iface eth0 inet 


So how do enable my wireless card as a user and not root, and even better, how can I do this as root?

I did look at the other posts, without them I would never had made it online in the first place, but none of them seemed to help me too much with this particular issue. Any suggestions from the heavy Kubuntu drinkers out there?

---

### Post by hyperpsyched on 2006-02-09
At the end of the post i meant to say, better yet, how do I do this automatically...

---

