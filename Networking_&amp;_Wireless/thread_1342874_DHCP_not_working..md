---
title: "DHCP not working."
date: 2009-12-01
forum: Networking &amp; Wireless
---

### Post by kanchankjha on 2009-12-01
Hey All,
I am new to this OS and new to forum.
Few weeks back my PC was able to get IP address from DHCP server in our LAN on default interface eth0 but now suddenly i am seeing that its not able to get the IP address.
Seems i edited some file in between which i don;'t remember.

I added another USB NIC card and on that there is no issues but the primary NIC card is still without IP address.

Any help will be appreciated.

Thanks,
-Kanchan

kkumarjh@kkumarjh-linux:~$ uname -a
Linux kkumarjh-linux 2.6.31-15-generic #50-Ubuntu SMP Tue Nov 10 14:54:29 UTC 2009 i686 GNU/Linux

---

### Post by Iowan on 2009-12-01
**ifconfig -a** (from a terminal) should show if any interface is getting IP address. [This ]("http://ubuntuforums.org/showthread.php?t=1156441") fixed my DHCP problem, but yours may be due to two cards.

---

### Post by kanchankjha on 2009-12-02
Hi,
Thanks for response.
But i don't think having multiple interface card does create any issues as these are connected to 2 different port of switch.

Thanks,
-Kanchan

---

