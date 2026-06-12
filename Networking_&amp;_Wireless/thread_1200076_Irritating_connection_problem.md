---
title: "Irritating connection problem"
date: 2009-06-29
forum: Networking &amp; Wireless
---

### Post by Phantom Hoover on 2009-06-29
Running Ubuntu 9.04 on an Acer 5738Z, I have had problems with the connection needing to be reset and downloads stopping abruptly. Can this be fixed?

---

### Post by haaglin on 2009-07-29
I have problems with my wlan on my 5738zg too. The connection drops every 5 min or so, and reconnects after a minute. Network-manager does not report the connection as lost, but i have no internet. Also, the speed are far from good. On a online speed test with the Acer, it reports 1,5mbit, but a hp laptop next to me reports speed to 11mbit. 

> 04:00.0 Network controller: Atheros Communications Inc. AR928X Wireless Network Adapter (PCI-Express) (rev 01)

Driver is ath9k.

If anyone know how to fix this, please share ;)

---

### Post by superprash2003 on 2009-07-29
take a look at [http://ubuntuforums.org/showthread.php?t=1146367](http://ubuntuforums.org/showthread.php?t=1146367)

---

### Post by haaglin on 2009-07-30
> **superprash2003 said:**
> take a look at [http://ubuntuforums.org/showthread.php?t=1146367](http://ubuntuforums.org/showthread.php?t=1146367)

Sweet. All seems good now. Installed new kernel, and disabled IPV6 > [http://www.ubuntu-inside.me/2009/04/howto-disable-ipv6-at-ubuntu-jaunty.html]("http://www.ubuntu-inside.me/2009/04/howto-disable-ipv6-at-ubuntu-jaunty.html")
and changed the bit rate manually to 54M > [http://ubuntuforums.org/showpost.php?p=7360932&postcount=45]("http://ubuntuforums.org/showpost.php?p=7360932&postcount=45")

And upgraded to last backport-modules-jaunty. I now have full speed, 100% signal strength, and no dropouts. ;)

---

