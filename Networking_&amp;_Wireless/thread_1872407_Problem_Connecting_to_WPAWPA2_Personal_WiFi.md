---
title: "Problem Connecting to WPA/WPA2 Personal WiFi"
date: 2011-10-30
forum: Networking &amp; Wireless
---

### Post by UnusualPi on 2011-10-30
Still a Novice here.

I had a Netgear router using WPA/WPA2 security and never had an issue connecting.  That thing overheated and crapped out so I bought a Linksys Hooked it up with the same security, SSID, everything and now Ubuntu won't connect to it.  It asks for the passcode i enter it in and it just spins until it says disconnected.

The router is working, everything else connects to it fine...xbox, windows 7, xp, etc.

And I know that Ubuntu is not having a problem with my wireless card since it connected in the past to the Netgear, also, this Linksys has a "Guest" connection that I activated that has no security and I am connected to that just fine.

Does anybody know if Linksys handle WPA/WPA2 security differently that I don't know about?  Thanks in advance for any help from the cloud!

---

### Post by mahmoud.l on 2011-10-31
Did you have the old connection automatically saved?
If so, remove it in Edit Connections and then try to connect to it again

---

### Post by UnusualPi on 2011-11-02
Yes definitely tried that. Still no luck.

---

### Post by UnusualPi on 2012-05-20
BUMP. With Updates.

Okay, so I had to do a re-format on my system so I figured I'd re tackle this issue, since I never figured it out, still not working but here's some updates.

1.) I can connect to the wifi network in my office just fine.  With wpa2 security.
2.) I can connect to the "Guest" network on my router that has no security just fine.
3.) I cannot connect to the regular network with WPA/WPA2 Personal security.
4.) I have attempted to disable ipv6 to no avail.
5.) I think I have narrowed it down to the how the security key is being transmitted.
Maybe it is being transmitted as hexidecimal and maybe it needs to be ascii...i dont' know how to change this.

The router model is: Linksys E2500

If there is any help out there or anybody else who has run into this, advice is much appreciated.  Thanks.

---

