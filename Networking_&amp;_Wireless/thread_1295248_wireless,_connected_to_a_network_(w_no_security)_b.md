---
title: "wireless, connected to a network (w/ no security) but cant browse anymore"
date: 2009-10-19
forum: Networking &amp; Wireless
---

### Post by bodyharvester on 2009-10-19
ive always connected to the same wireless network, sometimes id have the odd day where the connection is weak or i just cant connect to it.

recently however i cannot browse the internet or download when connected, i have no issue getting connected, it connects quickly, but when i try to load a webpage it wont load and after a while FF displays the page stating that the website cannot be found. There is no security (WEP key or WPA) when i check the info. and im not asked for any passwords when connecting.

ive already searched this sub-forum for an answer but cant find a solution.
any ideas?

thanks

---

### Post by sedawk on 2009-10-19
Here some tests that come to my mind:

* Check you got an IP from the DHCP server ([sudo] ifconfig wlan0)
* Try to get an IP from the DHCP server ([sudo] dhclient wlan0)
* Test pinging the WLAN router works (ping <router_ip>)
* Test DNS is setup and works (nslookup ubuntuforums.org)
* Try to ping servers on the internet

---

### Post by bodyharvester on 2009-10-19
hi, thanks for the suggestions, 

i think i found the problem. it claims there is no such device, apparently :|

```
joe@ZenOfJoe:~$ sudo ifconfig wlan0
[sudo] password for joe: 
wlan0: error fetching interface information: Device not found
``````
joe@ZenOfJoe:~$ sudo dhclient wlan0
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

SIOCSIFADDR: No such device
wlan0: ERROR while getting interface flags: No such device
wlan0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
```

any other suggestions of what to do next?

thanks again

---

### Post by bodyharvester on 2009-10-19
tried the live cd of 9.04 and those two commands produced the same results. is it possible that this is a hardware issue related to my wireless card?

i could connect to my mobile broadband collection fine but the wireless network was the same, fine connecting to it but no webpage loads

gonna try Zenix next

edit: Zenix was also unsuccessful, but thats just likely to it being the buggy first iso known as zenbuntu

---

