---
title: "WRT160N not connecting, other wired/wireless do"
date: 2010-03-04
forum: Networking &amp; Wireless
---

### Post by SurferGTO on 2010-03-04
OK So I moved today and had to purchase a new wireless router. Without changing any setting I connected using WiCd wirelessly from my last residence. 

I now purchased a Linksys WRT160N wireless router to use however cant connect to that wired or wireless. well let me specify, WiCd states its connected but no internet connection is found in firefox. 

I can connect directly to the motorola surfboard modem without a hitch, and can connect to a local unsecured network (hola)

I read somewhere that this was fixed by bridging the wireless router and the modem but I cant find directions on how to do that, if that is the case? that the Surboard Modem needs to be in bridge mode?

---

### Post by SurferGTO on 2010-03-05
come on gurus, bump

---

### Post by chili555 on 2010-03-05
This may be a bit elemental, but let's start with the simple stuff and move forward. The Surfboard modem has an ethernet jack that is connected with an ethernet cable to the **WAN** port on the router.

Then, your computer has an ethernet port that connects to a **LAN** port on the router.

If you have verified that is the way things are connected, please power down all three devices and then power up the modem, wait a few moments and power up the router and, after a few moments, boot your computer. On the computer, open Applications -> Accessories -> Terminal and do:```
ifconfig
```Does your eth0 interface have an IP address, like this?> eth0     Link encap:Ethernet  HWaddr 99:19:d2:c2:88:87
          inet addr:[COLOR="Blue"]192.168.1.103[/COLOR]  Bcast:192.168.1.255  Mask:255.255.255.0If so, do:```
ping -c3 www.google.com
```If you get ping returns, you are all set. If not, post back.

---

