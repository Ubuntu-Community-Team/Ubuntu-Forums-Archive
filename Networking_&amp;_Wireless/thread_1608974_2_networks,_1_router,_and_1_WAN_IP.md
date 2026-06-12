---
title: "2 networks, 1 router, and 1 WAN IP"
date: 2010-10-29
forum: Networking &amp; Wireless
---

### Post by Fire Raven on 2010-10-29
I know using WEP is like securing your front door with cellophane tape, but I have to use it anyway.

My wireless devices are an Apple iPod Touch and a Nintendo DS Lite. (Notice there are no PCs.) The DS Lite supports only 802.11b and WEP. Even though the DSi does support WPA, it falls back to WEP-only if you play a game not DSi-savvy (which is all of my net-enabled games).

My router box supports 802.11b/g/n. Enabling WEP disables WPA and that leaves the iPod Touch as insecure as the DS. I got a wireless access point box that lets you simultaneously  support WEP on one SSID and WPA/WPA2 on a different SSID. I can set up a few more SSIDs if necessary. So far so good, but I would still like more isolation for the DS.

There is some, ahem, unofficial software that makes it possible to back up and restore game saves on a PC. This requires wi-fi since there is no USB or Bluetooth on the DS. This is the only situation where the DS will ever need access to the LAN. Otherwise only WAN is needed.

I have one IP from my ISP, and no realistic chance of getting a second. Presently my entire LAN is [192.168.3.0/24]("http://192.168.3.0/24").

What I think I could do is give the DS a static IP of [192.168.9.1/24]("http://192.168.9.1/24"). Then I can set up a Damn Small Linux VirtualBox guest and give it [192.168.9.2/24]("http://192.168.9.2/24"). If necessary, my host's eth0 can gain [192.168.9.3/24]("http://192.168.9.3/24") as eth0:0. This guest will never need WAN access, so I can use a host-only adapter in its VB configuration.

The desired end result is 3 wi-fi usage scenarios:
1. iPod Touch with WPA in 192.168.3.0
2. DS Lite with WEP using the WAN in 192.168.9.0
3. DS Lite with WEP accessing the DSL guest in 192.168.9.0
and the DS will never use 192.168.3.0 at all. If my WEP is cracked, it should be much harder to get into the .3.0 LAN by keeping IP forwarding off between .3.0 and .9.0.

I wouldn't be surprised if I have overlooked something while making this plan. So I hope there will be someone here who knows networking better than I do and can spot whatever I have done wrong before I spend a lot of time implementing it.

---

