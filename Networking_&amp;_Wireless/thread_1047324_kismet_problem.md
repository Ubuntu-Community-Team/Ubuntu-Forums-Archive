---
title: "kismet problem"
date: 2009-01-22
forum: Networking &amp; Wireless
---

### Post by vikingman on 2009-01-22
[FONT="Lucida Console"]hey guys.

im under ubuntu 8.10, im trying to use kismet, after running sudo kismet the problem i get is :

```
Launching kismet_server: /usr/local/bin/kismet_server
Will drop privs to thor (1000) gid 1000
No specific sources given to be enabled, all will be enabled.
Non-RFMon VAPs will be destroyed on multi-vap interfaces (ie, madwifi-ng)
Enabling channel hopping.
Enabling channel splitting.
NOTICE: Disabling channel hopping, no enabled sources are able to change channel.
Source 0 (Broadcom): Enabling monitor mode for bcm43xx source interface eth1 channel 6...
FATAL: Failed to set monitor mode: Invalid argument.  This usually means your drivers either do not support monitor mode, or use a different mechanism for getting to it.  
Make sure you have a version of your drivers that support monitor mode, and consult the troubleshooting section of the README.
Done.

```

after entering in terminal : lspci | grep -i network, i get :
```
06:00.0 Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 01)

```

after iwconfig i get :

```

lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11  Nickname:""
          Access Point: Not-Associated   
          
pan0      no wireless extensions.

```

any help please.

PS: is there any replacement other than kismet to netstumbler that works under ubuntu, or a gui kismet

thnx in advance
[/FONT]

---

### Post by vikingman on 2009-01-22
[FONT="Lucida Console"]dump[/FONT]

---

### Post by vikingman on 2009-02-03
dump....

---

