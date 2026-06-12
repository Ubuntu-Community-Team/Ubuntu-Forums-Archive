---
title: "Sharing USB modem over WiFi Ubuntu 9.10"
date: 2009-12-01
forum: Networking &amp; Wireless
---

### Post by mark_lawton73 on 2009-12-01
Hi, I can only find older post with reference to this, my apologies if repeated.
First off I'm a newbie with Ubuntu, a fast learning curve but it is a fantastic breath of fresh air - thanks for all of the help and support, especially from reading  these forums :D.

First a run down..

INTERNET
USB E220 MODEM SHARED OVER NETWORK CARD/FIREWALLED (rented house no cable/landline)
DESKTOP PC XP PRO NETWORK CARD STATIC IP4 192.168.0.1 ,SUBNET 255.255.255.0
LAN CABLE
NETGEAR ROUTER 
STATIC IP4 192.168.0.2, SUBNET 255.255.255.0, DEFAULT GATEWAY AND PRIMARY DNS 192.168.0.1, USING PORT 1 (NOTHING IN ADSL PORT ON ITS OWN)
LAN CABLE
WiFi AP 
STATIC IP4 192.168.0.3,SUBNET 255.255.255.0, DEFAULT GATEWAY AND PRIMARY DNS ARE 192.168.0.1, THIS IS PLUGGED IN THE NETGEAR IN PORT 2 (NOTHING IN ADSL PORT ON ITS OWN)

With this settings the desktop pc on XPPro shares its 80Gb music folder and the printer, the XP name of this network is WORKGROUP.

Add 2 laptops (mine and sons), have Vista Ult/Ubuntu 9.10 and XPpro/Ubuntu 9.10
 These laptops can access the internet and the shared music folder of the desktop, the desktop can also access the internet. This is regardless as to wether on Windows (very rare.. only few games) or usually Ubuntu (cause its awesome!) , and the laptops wok great on other WiFi networks, college, work etc.
Their settings are DHCP IPv4 Auto.

As we use Ubuntu 98% of the time the problem is to get the desktop pc to share the internet and the music folder over the WiFi, using Ubuntu 9.10.

Leaving everything else unchanged Im guessing its the addressing of the autoeth0, as DHCP it never connects, shared with others kills the internet access of the desktop, manual 192.168.0.1 subnet 255.255.255.0 also kills the internet access, and no one has access to either the internet nor the music folder.

Hopefully avoiding messing with Network manager on the desktop pc (tried this but ended up with a manager that doesnt support USB modems.. and after trying every possible solution the only way to get Network manager back running is to re-install Ubuntu in the same partition.. it will not reinstall from spm nor CD !!), 

Is there any help or advice as to how to solve the network connectivity issues, example the settings for auto eth0, or what masq settings to use, sorry I am a noob and still learning and thank you for your help,
Best regards
Mark

---

