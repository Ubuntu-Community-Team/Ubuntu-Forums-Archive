---
title: "Plz help me to configure kismet in bcm4313"
date: 2011-06-06
forum: Networking &amp; Wireless
---

### Post by lavesh on 2011-06-06
[SIZE=3]I want to use kismet server in moniter mode i already install kismet but whenever i give the command sudo kismet tese error show in the terminal....

lavi@lavi-Inspiron:~$ sudo kismet
[sudo] password for lavi: 
Launching kismet_server: //usr/bin/kismet_server
Suid priv-dropping disabled.  This may not be secure.
No specific sources given to be enabled, all will be enabled.
Non-RFMon VAPs will be destroyed on multi-vap interfaces (ie, madwifi-ng)
Enabling channel hopping.
Enabling channel splitting.
NOTICE: Disabling channel hopping, no enabled sources are able to change channel.
Source 0 (wifi): Enabling monitor mode for b43 source interface wlan0 channel 6...
FATAL: GetIFFlags: interface wlan0: No such device
Done.
lavi@lavi-Inspiron:~$ [/SIZE]

[SIZE=3][COLOR=Red]what is this plz help to configure kismet in ubantu.. i am use ubantu 10.10    64 bit ubantu...[/COLOR][/SIZE]

---

### Post by chili555 on 2011-06-06
I think you might have to bring the interface down first. Does it work as expected if you do:```
sudo ifconfig wlan0 down
sudo iwconfig wlan0 mode monitor
sudo kismet
```Post back any error messages.

---

