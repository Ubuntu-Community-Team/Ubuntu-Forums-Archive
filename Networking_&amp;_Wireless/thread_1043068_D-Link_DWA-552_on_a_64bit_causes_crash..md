---
title: "D-Link DWA-552 on a 64bit causes crash."
date: 2009-01-18
forum: Networking &amp; Wireless
---

### Post by fhydan on 2009-01-18
Hi,

I just bought a new PC and it is fitted with a D-Link DWA-552 wireless adapter. The processor is an intel core 2 quad. I've tried to get it to work on Ubuntu 8.10. The device shows up in ifconfig as wlan0 and I can scan for network connections using the networkmanager thingy. However, when I try to connect to my wireless network, it tells me that it is connected, and ifconfig shows that the device now has an inet address. However, even pinging the router fails. Now, if I try to reconnect again, or connect to any other network, the computer just freezes. 

Sometimes, it simply freezes at the first attempt to turn connect to a wireless network. After reading around for a while I couldn't figure out how to solve this so I even tried some other distributions and both Fedora and OpenSUSE had the exact same issue. I'm sure the wireless adapter works because I'm using it right now from the dual-booted windows. I am not sure what to do, any help would be greatly appreciated.

---

### Post by mikedmor on 2009-02-26
Same here. DWA-552 causes 32bit to freeze as well. I was able to get it to working using the 32bit xp drivers and ndiswrapper. but now im using a 64bit. would be great if someone could explain how to get this to work.

---

