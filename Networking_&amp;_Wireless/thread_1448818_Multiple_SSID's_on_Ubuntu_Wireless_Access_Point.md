---
title: "Multiple SSID's on Ubuntu Wireless Access Point?"
date: 2010-04-07
forum: Networking &amp; Wireless
---

### Post by harfagre on 2010-04-07
I have just set up an Ubuntu 9.10 server PC at home. I have been able to set it up as a wireless AP with the athk9-driver, hostapd for wireless configuration and dhcp3 for the assignment of IP-addresses to wireless hosts. I have bridged the wlan0-interface on the server to the eth0-interface which allows me to connect wirelessly to both my LAN and the Internet.

Besides being able to connect to my encrypted, private wireless network I would also like to have an extra, unencrypted SSID that is open for everyone. I would like to set it up so that the unencrypted wireless network is open towards the Internet, but not to my local LAN.

Is there anyone out there with experience of similar scenarios? Is it even possible for an Ubuntu Wireless AP to server multiple SSID's? I have some experience with networking since before, but this is my first real shot at Linux... any help is appreciated!

---

### Post by Sooner Al on 2010-04-07
Well I can't answer your question directly but I can suggest looking at a dual wireless LAN [WLAN] router as an alternative solution. For example I run a ZyXEL NBG334W dual WLAN router to do exactly what you want to do.

[http://theillustratednetwork.mvps.org/LAN/CurrentHomeLAN.png]("http://theillustratednetwork.mvps.org/LAN/CurrentHomeLAN.png")

[http://tinyurl.com/AmazonNBG334WSources]("http://tinyurl.com/AmazonNBG334WSources")

If you have a supported router I believe DD-WRT firmware (free) will do something similar.

[http://www.dd-wrt.com/wiki/index.php/Glossary#VLAN]("http://www.dd-wrt.com/wiki/index.php/Glossary#VLAN")
[http://www.dd-wrt.com/wiki/index.php/Supported_Devices]("http://www.dd-wrt.com/wiki/index.php/Supported_Devices")

---

