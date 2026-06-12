---
title: "Wireless router as a station works in Windows, not Ubuntu"
date: 2009-04-11
forum: Networking &amp; Wireless
---

### Post by linuxtorvalds on 2009-04-11
I'm using a wireless router to act as the client for a laptop to connect to a wireless access point.  Laptop dual boots to Win7 and Intrepid.

On the AP end, an Airlink wireless router is configured with DHCP server off, ethernet to a dsl modem which is the DHCP server and DNS server.

In another room, a laptop is connected via ethernet to a NetGear WGT624 wireless router.  It is set up as a station, BSSID of the AP is set, then the ESSID and Channel of the AP is set.  Then the DHCP server on it is turned off, reboot.

When the laptop is booted to Windows, it doesn't work until clicking on 'fix network connection', then it works normally.  I haven't been able to figure out what it does to fix it.  It's not in the logs and I can't access the router to see what the settings are.  (192.168.1.1 gets you to the dsl modem instead.)  Only way I know to get back in to the netgear is to do a hard reset, which wipes out all settings.

I can only observe the connections on the dsl modem.  When it's working it shows the laptop's ip as 0.168.1.2.  I can't see anymore since verizon changed the login and pw without telling me sometime in the past.  I don't want to mess with it since it is the only working connection right now.

With linux there's no assigned ip.  dhclient shows no leases, or sometimes the eth is bound to avahi.  If I leave DHCP server on all I get is a connection to the netgear.

Any ideas?

---

