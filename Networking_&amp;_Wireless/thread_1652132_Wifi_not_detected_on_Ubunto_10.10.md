---
title: "Wifi not detected on Ubunto 10.10"
date: 2010-12-24
forum: Networking &amp; Wireless
---

### Post by icoder on 2010-12-24
Hi, yesterday i installed ubuntu 10.10 desktop edition on my HP DM4-1006TU laptop
everything working fine except the wifi.

i'm able to switch off/on my wifi as LED goes red and white but no network found under wireless network.

where as on windows 7 wifi working smoothly.

please help

---

### Post by grahammechanical on 2010-12-24
Right click the network icon. Is there a tick mark against Enable Networking and Enable Wireless? If not select each of the lines and click them.

Removing the tick mark against these lines and then putting it back switches networking and wireless off and on and this might activate a scan for networks.

Right click the network icon and select Edit Connections. Go to the Wireless tab and make sure that the wireless connection is set to connect automatically and that is is available to all users.

Go to System>Preferences>Startup Applications and make sure that there is a tick mark against the Network Manager line.

Also go to System>Administration>Additional Drivers. You may need to install a specific driver for the wireless adapter in your laptop.

Regards.

---

