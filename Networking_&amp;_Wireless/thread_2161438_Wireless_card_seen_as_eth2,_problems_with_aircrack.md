---
title: "Wireless card seen as eth2, problems with aircrack-ng"
date: 2013-07-10
forum: Networking &amp; Wireless
---

### Post by jrtarsoly on 2013-07-10
Good day to all,

I've installed and configured Ubuntu 12.04 on a Hp Compaq 6735s laptop. All seems to be in order, except for the fact that I can't start monitoring with airmon-ng due to the fact that my wireless card is seen by Ubuntu as an ethernet card instead of a wireless one.

Typing iwconfig does show eth2 as having wireless capabilities, but using the "sudo airmon-ng start eth2" command does not seem to work.

For example :

-typing iwconfig :
```

lo        no wireless extensions.

eth0      no wireless extensions.

eth2      IEEE 802.11abg  ESSID:"ESSID"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: xx:xx:xx:xx:xx:xx   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off

```
-typing "sudo airmon-ng start eth2" :
```

Found 5 processes that could cause trouble.
If airodump-ng, aireplay-ng or airtun-ng stops working after
a short period of time, you may want to kill (some of) them!
-e 
PID    Name
883    NetworkManager
904    avahi-daemon
906    avahi-daemon
953    wpa_supplicant
1528    dhclient
Process with PID 1528 (dhclient) is running on interface eth2


Interface    Chipset        Driver

eth2        Broadcom    wl - [phy0]mon0: ERROR while getting interface flags: No such device

                (monitor mode enabled on mon0)

```
-

Yeah, I do run on proprietary drivers and have spent hours trying to install the b43 drivers, but all that managed to do was to shut down my wifi card completely, so I've downgraded b43 and re-installed the bcmwl-kernel-source or the Proprietary driver.

My question is what options do I have in order to make aircrack-ng to work properly ? Any advice would be much appreciated.

Thanks,

JrT

---

### Post by wildmanne39 on 2013-07-10
Hi, aircrack is not a supported topic on the forum so this thread has been closed! Your best option is the backtrack or aircrack forums.
Thanks

---

