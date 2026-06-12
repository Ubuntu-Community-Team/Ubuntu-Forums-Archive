---
title: "Wireless Card - Monitor Mode"
date: 2005-12-24
forum: Networking &amp; Wireless
---

### Post by ninocass on 2005-12-24
Hi all

Im doing my 3rd year Uni placement in a Pen Testing company and i want to get my laptop set up for pen testing wireless network's

It seems that i need a card that supports monitor mode rather than one that connects to just the access points.

As im running on a laptop id like a card that is PCMICA and compatible with ubuntu, its its now my OS of choice (XP bit the dust the other day :D )

Thanks

Nino

---

### Post by Lambert on 2005-12-25
The madwifi driver supports monitor mode so any card based on the atheros chipset should be ok.

[http://madwifi.org/wiki/Compatibility](http://madwifi.org/wiki/Compatibility)

You can cross this with the wiki document about cards

[https://wiki.ubuntu.com/WirelessNetworkCards?highlight=%28wireless%29](https://wiki.ubuntu.com/WirelessNetworkCards?highlight=%28wireless%29)



[http://madwifi.org/wiki/UserDocs/MonitorMode](http://madwifi.org/wiki/UserDocs/MonitorMode)

---

### Post by TadH on 2007-11-10
how can i tell if my laptop wireles card supports monitor mode? i dont think it does because when i iwconfig ath0 mode monito it gives me an error
any ay to change it?

---

### Post by Lambert on 2007-11-10
> **TadH said:**
> how can i tell if my laptop wireles card supports monitor mode? i dont think it does because when i iwconfig ath0 mode monito it gives me an error
any ay to change it?

Install the madwifi-tools package and then follow instructions here.

[http://madwifi.org/wiki/UserDocs/MonitorModeInterface](http://madwifi.org/wiki/UserDocs/MonitorModeInterface)

---

