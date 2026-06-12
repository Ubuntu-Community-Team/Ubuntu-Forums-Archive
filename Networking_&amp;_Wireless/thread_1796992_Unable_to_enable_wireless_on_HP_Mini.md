---
title: "Unable to enable wireless on HP Mini"
date: 2011-07-04
forum: Networking &amp; Wireless
---

### Post by Phist on 2011-07-04
The wireless on this computer has worked with Ubuntu just yesterday so I know all the drivers work. The trouble is that now the wireless is turned off and the hardware switch has no effect. Is there a way to force enable it through the terminal?

---

### Post by MaindotC on 2011-07-04
My first thought would be to view your **sudo ifconfig** to see if you are associated with an access point and if you have been assigned proper address information.  If you feel you have, then **sudo ifconfig <device_name> up** to enable the device.

The issue could be more complext.  The first place to start is the [Ubuntu Wireless Troubleshooting Guide](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide).  In order for your device to work properly you need the physical connectivity (plugged in all the way and/or turned on via your machine's BIOS), a driver to communicate between the device and the operating system, and then the proper configuration of the device which typically is via DHCP.  Please follow the guide and indicate at what point you are having difficulty.

---

