---
title: "total confusion with network configuration"
date: 2011-08-07
forum: Networking &amp; Wireless
---

### Post by spidertattoos on 2011-08-07
basically i had the bcm driver issue when i upgraded to natty which was fixed by installing the previous proprietary driver from 10.10. but now although i can connect to wireless the system thinks that my wireless card is the ethernet and doesnt register if anything is actually plugged into the ethernet, as a result my 100mbps broadband is topping out at 2mbs at best. if i run iwconfig i get.

massacre@Massacre:~$ sudo iwconfig
lo        no wireless extensions.

eth2      IEEE 802.11bg  ESSID:"spidertattoos"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: A0:21:B7:4D:95:B8   
          Bit Rate=5.5 Mb/s   Tx-Power:24 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=5/5  Signal level=-44 dBm  Noise level=-57 dBm
          Rx invalid nwid:0  Rx invalid crypt:45  Rx invalid frag:0
          Tx excessive retries:115  Invalid misc:0   Missed beacon:0

So eth2 is connected to my wireless which apparently doesnt exist. very confused.any help would be brilliant. oh i am also running my natty with gnome3 not unity.

---

### Post by chili555 on 2011-08-07
It's not at all unusual for wireless interfaces to be named eth-somethingorother. My Intel IPW2915 is named eth1.

Your wireless appears to be connected, albeit at a low rate:> eth2 IEEE 802.11bg ESSID:"spidertattoos"
Mode:Managed Frequency:2.437 GHz Access Point: A0:21:B7:4D:95:B8
[COLOR="Red"]Bit Rate=5.5 Mb/s[/COLOR] Tx-Power:24 dBm
Retry min limit:7 RTS thrff Fragment thrff
Encryption keyff
Power Managementff
Link Quality=5/5 Signal level=-44 dBm Noise level=-57 dBm
Rx invalid nwid:0 Rx invalid crypt:45 Rx invalid frag:0
Tx excessive retries:115 Invalid misc:0 Missed beacon:0
You might try to force it:```
sudo iwconfig eth2 rate 54M
```Other than that, it looks fine.

---

### Post by spidertattoos on 2011-08-08
thanks ill try it in a minute. any ideas on why my ethernet isnt recognising when i plug it in?

---

### Post by chili555 on 2011-08-08
> **spidertattoos said:**
> thanks ill try it in a minute. any ideas on why my ethernet isnt recognising when i plug it in?I have no idea but I'll be happy to help troubleshoot it. Please run and post:```
lspci -nn | grep 0200
```

---

