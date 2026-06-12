---
title: "Ubuntu on Acer laptop"
date: 2011-03-29
forum: Networking &amp; Wireless
---

### Post by fuquam on 2011-03-29
Machine brand: Acer 5253-BZ893 laptop
Ethernet controller: Atheros communication device 1083
Network controller: Broadcom Corp. Device 4357
iwconfig: no wireless extensions
network config: *-network UNCLAIMED
iwlist scan: Interface doesn't support scanning
Ubuntu release: 10.04.2
uname -mr: 2.6.32-28-generic x86_64
------------------------------------------------------

I have not been able to get an internet connection wired or wireless on my laptop. I downloaded the drivers from Acer's website and tried installing them using ndiswrapper. Still no luck. Any other suggestions? Hopefully I've included enough info.

---

### Post by doctorzeus on 2011-03-29
> **fuquam said:**
> Machine brand: Acer 5253-BZ893 laptop
Ethernet controller: Atheros communication device 1083
Network controller: Broadcom Corp. Device 4357
iwconfig: no wireless extensions
network config: *-network UNCLAIMED
iwlist scan: Interface doesn't support scanning
Ubuntu release: 10.04.2
uname -mr: 2.6.32-28-generic x86_64
------------------------------------------------------

I have not been able to get an internet connection wired or wireless on my laptop. I downloaded the drivers from Acer's website and tried installing them using ndiswrapper. Still no luck. Any other suggestions? Hopefully I've included enough info.

You could check if there were some native linux drivers...easiest way is using the "hardware drivers" menu and installing the wireless drivers..

Broadcom wireless chip sets and Linux don't go hand it hand I'm afraid (got one myself)

---

### Post by fuquam on 2011-03-29
I tried the "hardware drivers" first but all I get is "Downloading package indexes failed, please check your network status. Most drivers will not be available". 

I can't get an internet connection even plugging directly into my router. Windows 7 came preinstalled so I know the network connection works, just not with Ubuntu yet. I might try a clean install and try the netbook version.

---

### Post by bkratz on 2011-03-29
> **fuquam said:**
> I tried the "hardware drivers" first but all I get is "Downloading package indexes failed, please check your network status. Most drivers will not be available". 

I can't get an internet connection even plugging directly into my router. Windows 7 came preinstalled so I know the network connection works, just not with Ubuntu yet. I might try a clean install and try the netbook version.

The broadcom 4357 uses the STA driver. About halfway down the page see the section labeled

"STA no-internet access"

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)

---

