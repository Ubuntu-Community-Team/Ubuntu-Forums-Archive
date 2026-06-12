---
title: "connect two laptops using wifi"
date: 2006-06-28
forum: Networking &amp; Wireless
---

### Post by jerinjoy on 2006-06-28
i have two laptops both of which are wifi enabled. is it possible to connect them via wifi? without using a hub?

---

### Post by jchau on 2006-06-28
I'm almost certain that creating a wireless network without any access points is possible once you get the wireless cards working (get appropriate drivers).  The wireless cards should support Ad-Hoc mode (which does not require access points).  

Try the command:
```
sudo iwconfig eth1 essid "WirelessNetworkName" mode Ad-Hoc key s:*************
```
Where WirelessNetworkName is the name of the wireless network you wish to create and the ************* is the WEP key in ASCII.  My wireless network interface is eth1; you should replace eth1 with the name of your interface.

I managed to start an Ad-Hoc network like this.  However, the other computers on the network are WinXP machines.  I believe that one of the WinXP machines is providing the network information through DHCP but I am not certain.  

Since I never started an ad-hoc network with purely Ubuntu machines, I am not certain if this is enough to do so.  If this doesn't work, try running a DHCP server on one of the computers or try to manually assign the network info.  

Good luck, and tell me if this works (it is definately possible though).

---

