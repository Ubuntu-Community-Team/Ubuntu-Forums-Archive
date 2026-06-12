---
title: "Connect to WEP WLAN without DHCP"
date: 2010-08-18
forum: Networking &amp; Wireless
---

### Post by Hkotel on 2010-08-18
Hey,
I am trying to connect to a WEP encrypted WLAN without using the DHCP server of the AP. (=giving myself a static IP)
So far i have tried:
```

/etc/init.d/networkmanager stop (tried it with and without) 
ifconfig wlan0 down
dhclient -r wlan0
ifconfig wlan0 192.168.1.50 netmask 255.255.255.0 up
route add default gw 192.168.1.1
iwconfig wlan0 essid 'WLAN_NAME'
iwconfig wlan0 key WEPKEY
iwconfig wlan0 key open
iwconfig wlan0 mode Managed
dhclient wlan0

```But i cant even ping 192.168.1.1 (Network unreachable error). Is it possible that Ubuntu tries to use eth0 (which was connected to a similar /16 before) to ping 192.168.1.1 or is there somethign wrong with my commands?
Also will an AP allow access to the network although i don't have an IP from its DHCP server?

Thanks in advance

---

### Post by Hkotel on 2010-08-19
Bump.
Can anyone help me?

---

### Post by Hkotel on 2010-08-21
Noone wanna help me?

---

### Post by Iowan on 2010-08-22
Wireless isn't my forte - WEP, even less...
What are results of **ifconfig -a**?
It might be a problem if both interfaces are in the same subnet.

---

