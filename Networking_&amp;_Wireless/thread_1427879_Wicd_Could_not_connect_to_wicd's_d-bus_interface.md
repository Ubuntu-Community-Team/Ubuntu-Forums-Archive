---
title: "Wicd: Could not connect to wicd's d-bus interface"
date: 2010-03-12
forum: Networking &amp; Wireless
---

### Post by dusdus on 2010-03-12
Hi there,

I've installed ubuntu 9.10 using a minimal install and started from there installing the rest of the things I needed.
I'm running KDE4.4 and Wicd 1.6.1.

Problem is, wicd worked fine, but I don't know what happened before I got this annoying problem.

After logging into KDE, wicd asks me for my password in order to connect to the network-device. After filling that in, I get the message:
```

Could not connect to wicd's d-bus interface

```
and I need to check wicd's log. The log tells me nothing, no error at all:
```

2010/03/12 09:21:11 :: ---------------------------
2010/03/12 09:21:11 :: wicd initializing...
2010/03/12 09:21:11 :: ---------------------------
2010/03/12 09:21:11 :: wicd is version 1.6.1 426
2010/03/12 09:21:11 :: setting backend to external
2010/03/12 09:21:11 :: trying to load backend external
2010/03/12 09:21:11 :: successfully loaded backend external
2010/03/12 09:21:11 :: trying to load backend external
2010/03/12 09:21:11 :: successfully loaded backend external
2010/03/12 09:21:11 :: Automatically detected wireless interface wlan0
2010/03/12 09:21:11 :: setting wireless interface wlan0
2010/03/12 09:21:13 :: automatically detected wired interface eth0
2010/03/12 09:21:13 :: setting wired interface eth0
2010/03/12 09:21:13 :: setting wpa driver wext
2010/03/12 09:21:13 :: setting use global dns to False
2010/03/12 09:21:14 :: setting global dns
2010/03/12 09:21:14 :: global dns servers are None None None
2010/03/12 09:21:14 :: domain is None
2010/03/12 09:21:14 :: search domain is None
2010/03/12 09:21:14 :: setting automatically reconnect when connection drops True
2010/03/12 09:21:14 :: Setting dhcp client to 0
2010/03/12 09:21:14 :: Wireless configuration file found...
2010/03/12 09:21:14 :: Wired configuration file found...
2010/03/12 09:21:14 :: chmoding configuration files 0600...
2010/03/12 09:21:14 :: chowning configuration files root:root...
2010/03/12 09:21:14 :: Using wireless interface...wlan0
2010/03/12 09:21:14 :: Using wired interface...eth0
2010/03/12 09:21:15 :: hidden
2010/03/12 09:21:20 :: Autoconnecting...
2010/03/12 09:21:20 :: No wired connection present, attempting to autoconnect to wireless network
2010/03/12 09:21:21 :: hidden
2010/03/12 09:21:21 :: trying to automatically connect to...Mafkezen
2010/03/12 09:21:21 :: Connecting to wireless network Mafkezen
2010/03/12 09:21:24 :: Putting interface down
2010/03/12 09:21:24 :: Releasing DHCP leases...
2010/03/12 09:21:25 :: Setting false IP...
2010/03/12 09:21:25 :: Stopping wpa_supplicant
2010/03/12 09:21:25 :: Flushing the routing table...
2010/03/12 09:21:25 :: Putting interface up...
2010/03/12 09:21:25 :: Generating psk...
2010/03/12 09:21:25 :: Attempting to authenticate...
2010/03/12 09:21:30 :: Running DHCP
2010/03/12 09:21:30 :: Internet Systems Consortium DHCP Client V3.1.2
2010/03/12 09:21:30 :: Copyright 2004-2008 Internet Systems Consortium.
2010/03/12 09:21:30 :: All rights reserved.
2010/03/12 09:21:30 :: For info, please visit http://www.isc.org/sw/dhcp/
2010/03/12 09:21:30 :: 
2010/03/12 09:21:31 :: Listening on LPF/wlan0/00:17:c4:a4:fb:22
2010/03/12 09:21:31 :: Sending on   LPF/wlan0/00:17:c4:a4:fb:22
2010/03/12 09:21:31 :: Sending on   Socket/fallback
2010/03/12 09:21:33 :: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4
2010/03/12 09:21:33 :: DHCPOFFER of 192.168.1.34 from 192.168.1.254
2010/03/12 09:21:33 :: DHCPREQUEST of 192.168.1.34 on wlan0 to 255.255.255.255 port 67
2010/03/12 09:21:33 :: DHCPACK of 192.168.1.34 from 192.168.1.254
2010/03/12 09:21:33 :: bound to 192.168.1.34 -- renewal in 12115 seconds.
2010/03/12 09:21:33 :: DHCP connection successful
2010/03/12 09:21:33 :: Connecting thread exiting.
2010/03/12 09:21:36 :: Sending connection attempt result Success

```

The taskbar shows me the icon of wicd and hovering above it tells me ```
Wicd daemon unreachable
```

As you can see in the logging, internet is working fine. I manually have to start wicd-client and I get an extra wicd-icon in the taskbar showing me the signal strength as it should do.

I've been searching a lot, but can't find anything about this, except a lot of people having the same errormessage, but they have some errors in the wicd.log too.

Can anyone point me into the right direction? If more info is needed, I'll be happy to supply it!

---

### Post by dusdus on 2010-03-12
I've asked on wicd irc channel and even there I couldn't get an answer. 

Please, anyone?

---

### Post by dusdus on 2010-03-14
wierd... after installing openftd, which requires a lot of gnome-apps I rebooted and automatically Gnome started, instead of KDE. After configuring KDM I rebooted again and the problem is fixed...

anyway, happy now

---

