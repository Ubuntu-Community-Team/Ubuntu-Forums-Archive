---
title: "Need help detecting wireless card"
date: 2009-07-29
forum: Networking &amp; Wireless
---

### Post by kbjustin on 2009-07-29
While I am not that new to linux I am new to having it on one of my own laptops and setting everything up. I have an asus eeepc 1005ha that came with windows xp and i installed ubuntu 9.04 so it dual boots. When i go into ubuntu it doesnt even seem to detect that i have a wireless card because when i click the network icon on the top it says no network devices available and i can only configure a vpn. I really dont have any idea what to from here and i cant seem to find a solution online. Ok sorry didnt read posting rules at first:

When i run lspci i get: Network controller:Atheros Communications Inc. AR9285 Wireless Network Adapter(PCI-Express
When i run ifconfig i see nothing about wireless and when running iwconfig it says: lo     no wireless extensions
                                                                                                                       pan0   no wireless extensions
When i run sudo lshw -C network it says network unclaimed and that basically gives the wireless controller info which i already listed.
The iwlist scan command just comes up saying Interface doesnt support scanning for lo and pan0.

If you need more information let me know as I said i have never configured any linux by myself

---

### Post by mynameinc on 2009-07-29
You may have to install the driver:
System->Preferences->Hardware Drivers

---

### Post by kbjustin on 2009-07-30
when i go there it says no proprietary drivers are in use on this system

---

### Post by Raubsau on 2009-08-01
[http://ubuntuforums.org/showthread.php?t=1219931&highlight=1005ha](http://ubuntuforums.org/showthread.php?t=1219931&highlight=1005ha)

---

