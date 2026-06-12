---
title: "Interesting Wifi Routing Conundrum"
date: 2012-05-28
forum: Networking &amp; Wireless
---

### Post by PilotPaul on 2012-05-28
OK here's the scenario...

I have a PC running Mythbuntu 12.04 which has two wireless connections.  The first is used to connect to an external open wifi hotspot that requires a password to be entered into a login screen in a browser window before actual internet access is enabled.  This network is quite hard to connect to from inside the location of the PC since it is inside a narrowboat (effectively a Faraday cage), and so I use a USB adapter with an external aerial to make this connection. The second wireless connection is internal to the PC and configured as a wireless access point using hostapd and isc_dhcp_server to allow internal clients to make a wireless connection with this system.  This allows additional internal PCs to act as MythTV frontends as well as ensuring a connection to the external internet (normally difficult due to the Faraday cage effect) via IP masquerading (configured using iptables).

So far so good...the only problem I have is that it seems that the external wifi router doesn't like the internet connection sharing that is effectively happening and drops the authentication when another station tries to communicate over the shared internet. I suspect that this is a deliberate intention by the ISP to stop their connection being shared out - understandable but for my purposes slightly infuriating!

So my question is this - has anyone any similar experiences with this kind of configuration and if so any suggestions as to how to overcome the restriction being imposed by the ISP, preferably without having to pay an external site to act as a VPN host?

Ta in advance

Pilot Paul

---

### Post by thebeest on 2012-05-28
This hotspot setup sounds like a similar system I am trying to implement. Can you find out the type of Captive Portal software they are using for the login page?
We might be able to get a better idea on how to get around the system if we know which one it is! I guess you should be able to find out in a copyright at the bottom of the login page or hidden in the html somewhere?

---

