---
title: "Using openDNS and need help to master config on router.."
date: 2009-01-14
forum: Networking &amp; Wireless
---

### Post by hockey97 on 2009-01-14
Hi, I just started to use OpenDNS and It seems faster then my  isp dns servers.

ok, well I config my router to use those dns servers.

Now I need to learn to master the router config.

ok, my computer has a server so I need a static internal ip the rest about 3 other computers could obtain the ip from the router.

Now how do I config the router so that no computer gets the same ip address and creates a conflict? 

I have linksystem. Also when the other computers are set to automaticly get an ip address does that mean they will pick up what I config the router to use as a dns server?


I notice that sometimes when my sister turns on her laptop our router gets clogged or something where I have to go to the router to unpower it and power it back up which usally fixes the problem.

I want to prevent such a thing from happening.

could you help me out?

---

### Post by Iowan on 2009-01-14
I'm not really familiar with appliance routers - I don't remember if the one I played with was D-Link or LinkSys.  Anyway, it *seems* like they come with DHCP enabled out-of-the-box. If so, it *should* take care of unique addresses. This is only true if all machines on your network use DHCP or have static address set outside DHCP range.
Those machines set to "Get IP address automatically" *should* get DNS information from DHCP server (router?).

---

### Post by hockey97 on 2009-01-14
I see; So you mean that my computer should be outside the range that assigns the other computers automaticly?

I just want to know if I have 3 computers that get a ip automaticly, if they would get ip conflicts with one another?

The reason was that it happened with my sisters laptop with my dads computer. Where the adaptor gave a message saing that it had a ip conflict.

I want to avoid any problems with one another computer.

Is it possible that I can assign each computer it's own static ip by the routers config? or not really?

---

### Post by Iowan on 2009-01-15
Yes, static addresses should outside the dynamic range.  The DHCP server (router?) assigns addresses from that range, and keeps track of which machine has which address.  Therefore, machines that get an automatic (DHCP) address should never get conflicting addresses. (Unless... there is more than one DHCP Server handing out addresses - this is abnormal, and shouldn't normally occur). Since you mentioned it, does your server have DHCP server installed?  If so, either it OR the router could be used... but not both. 
It is possible to configure each machine with a static address - or (if the router is capable) have it to assign a static _lease_ (fixed address) based on MAC address.
  If all machines get DHCP addresses from the same DHCP server, there *should* never be an address conflict.

It kinda sounds like your sister's computer may be set for a static address...

---

