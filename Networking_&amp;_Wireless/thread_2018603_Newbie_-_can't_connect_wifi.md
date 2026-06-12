---
title: "Newbie - can't connect wifi"
date: 2012-07-06
forum: Networking &amp; Wireless
---

### Post by RV92113 on 2012-07-06
I have an older MacBook which used to have dual boot Mac OSX/MS Windows XP. Wifi worked fine on both partitions. The hd was replaced and converted (no more OSX or XP) the MacBook to Ubuntu 12.04 last week, have been able to easioly connect to **secure** wifi networks at the office and a friends house as well as several **unsecured** networks. However, my home network which is secured **will not connect**. My Android tablet, Network printer, Android phone, 2 HP laptops running MS Windows 7 and Roku box all are able to connect to the home network without any problems. Ubuntu dialog box keeps popping up stating I am disconnected.
 
Router and modem have been rebooted, confirmed wifi is working on all other devices, entered password into Ubuntu dialog box - still can't connect. No problems connecting/disconecting to any of the other networks I have previously connected to.
 
Any suggestions? I am new to Ubuntu, so I need help in plain english.
 
Thanks

---

### Post by praseodym on 2012-07-06
Hi,

check, if a MAC-address filter is active in your router (interface). Maybe your card is blocked (or you are running out of IP-addresses, check the address pool).

---

### Post by RV92113 on 2012-07-06
I'm at work now, MacBook has been connected to Wi-Fi for 3 hours, no problems.  So I know the MacBook, wi-fi and Ubuntu work.  I will check for MAC filter on home network when I get home tonight.  Not all of the devices mentioned in my initial post were on at the same time so I don't think we are out of addresses yet.
 
Thanks.

---

### Post by praseodym on 2012-07-07
Check@home:

```
lspci -nnk | grep -iA2 net
rfkill list
lsmod
iwconfig
sudo iwlist scan
cat /etc/resolv.conf
route -n
```

---

