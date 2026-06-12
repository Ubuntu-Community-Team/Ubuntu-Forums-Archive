---
title: "UPnP through ICS for XBOX"
date: 2010-11-19
forum: Networking &amp; Wireless
---

### Post by Jethro_uk on 2010-11-19
I have a weird setup ... Wireless router connecting to wlan0 on10.04 machine which has firestarter ICS running, and eth0 connected to Windows XP machine which itself has ICS and a connection to an XBOX.

Machine is a new one, replacing a 9.10 one which I set up by trial and error over many months (learning as I went)

New machine seems to work fine, ICS is working as XP machine can access internet fine. XBox can access internet too, and Xbox live. However it's warning me that the connection is "moderate NAT" and some features may not work.

Everything worked fine on old 9.10 box. I know this 100% as my son was able to talk to his friends - now he can't.

The 10.04 box itself is quite happily driving UPnP on my router, as Vuze is happy as anything (what a speed !!!!) and the router is showing UPnP established connections.

Am I missing something ... do I need to do anything to get the XBox to be able to UPnP ? I have run a UPnP test tool on the XP box, and it seems something is stopping XP being able to open ports (XP firewall is OFF btw).

---

### Post by Jethro_uk on 2010-11-20
UPDATE:

I have run a long Cat5 cable to allow me to move the internet-enabled wireless router closer to the XP machine, and connected directly to it. I ran the XBOX network test and BINGO ! It works OK. So I have eliminated the router and the XP PC as causes of the problem. The problem only occurs when using the Ubuntu machine for ICS ....

Does this help anyone give a suggestion as to what to check/change ?

---

### Post by Atomic Fusion on 2010-11-20
I don't know how "ICS" relates to network interface bridging, but if they're not the same thing, you could try bridging. Otherwise, OpenVPN could be useful for abstracting your networking beyond the actual hardware. You could make a virtual network with OpenVPN and bridge that, but that might be more complicated than just bridging.

---

### Post by Jethro_uk on 2010-11-25
for some reason, firestarter was set to block ICMP packets (except ECHO) by default. This was stopping pings to DNS servers, hence the message. I unchecked the "enable ICMP filtering" option on edit..preferences and all is fine.

I diagnosed this using the new nifty nokia WiFi sniffer ....

---

