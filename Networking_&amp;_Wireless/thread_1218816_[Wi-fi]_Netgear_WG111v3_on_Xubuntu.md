---
title: "[Wi-fi] Netgear WG111v3 on Xubuntu"
date: 2009-07-21
forum: Networking &amp; Wireless
---

### Post by Ma55imo1973 on 2009-07-21
Hello all, I have a Xubuntu 8.04 LTS version installed on an ASUS laptop and I was trying to install a wireless adapter WG111v3 from NETGEAR to work with my router DG834G. I read tens of tutorials and guides and I think I'm on the brink of coping with it, but still I'm not connecting. The summary is the following:
 
1) Installed ndisgtk and the drivers for WG111v3 that I found in the original installation for Windows (WG111v3.inf). Command line «ndiswrapper -l» says the driver is installed and the device is present. The same on ndisgtk. 
 
FIRST QUESTION: the adapter's blue led is flashing at 10 seconds intervals for 1-2 seconds and the remaining time is turned off. IS THAT CORRECT ? I tried to remove the driver and re-install it but nothing changes in the behavior of the led.
 
2) Command lines iwconfig, iwlist, etc say wlan0 is workinf and the wifi network is visualized with signal intensity and so on. 
 
3) Wicd network manager sees the network NETGEAR.
 
4) I input the MAC address of the laptop in the router configuration (Wireless options) thru the cable connection. 
 
5) I set the satic IPs (192.168.0.2 fo the laptop, 255.255.255.0 for the netmask, 192.168.0.1 for the gateway (router) and the 2 DNS are the ones for Alice Provider (212.216.112.112 e 212.216.172.62).
 
PROBLEM IS: when I try to connect to the wifi I receive the message:
 
«Connected to None at 0%%» AND I CAN'T PING NOR NAVIGATE thru firefox
 
What does that mean ?
 
I remind tha I blacklisted the component rtl8187 according to several guides and threads as apparently not supported by the kernel version. 
 
Please help me !
 
Many thanks !
 
Massimo

---

