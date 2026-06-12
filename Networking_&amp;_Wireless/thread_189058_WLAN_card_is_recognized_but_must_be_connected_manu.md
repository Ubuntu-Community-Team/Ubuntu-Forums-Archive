---
title: "WLAN card is recognized but must be connected manually"
date: 2006-06-04
forum: Networking &amp; Wireless
---

### Post by ciacorp on 2006-06-04
Hello dears,

after updating breezy --> dapper, the following problem occurs:

Ubuntu/Linux recognized my WLAN card (WG511v2) when booting, but does not connect (tested with dhcp and static). I always have to activate and connect the card manually.

Don't know how to manage that quiet bothering problem.
thanks in advance!

ciacorp

---

### Post by bigkahoona on 2006-06-05
I have the exact same problem with a D-Link AirPlus G DWL-G630.
It is recognized and works without a problem once connected, but Kubuntu "forgets" to connect it to the network during bootup.
I have to run the Wireless assistant. Then it tells me that there are no networks. Once I hit "refresh", the right SSID is shown and when I highlight it my WLAN card is autoconnected, so it apparently doesn't lose the settings, it just doesn't seem to be communicating with the wireless router during bootup. All my other machines do, so it's not a problem with the router.
It seems that this is more of a common problem... anyone got an idea? :-?

---

### Post by mchs3d on 2006-06-05
ciacorp: I have the exact same card and the same problem, but I found a solution. Add the following lines to the end of /etc/init.d/bootmisc.sh at the end, but before the "exit: 0" line:

[B]modprobe ndiswrapper
iwconfig wlan0 essid "SSID" key "01234567890123456"[/B]

Of course, fill "SSID" with your ssid and key "" with your WEP key. This should automatically connect to your network every time you login.

---

