---
title: "Ubuntu 9.04 cannot connect to a specific wireless network?"
date: 2009-06-02
forum: Networking &amp; Wireless
---

### Post by Mgiacchetti on 2009-06-02
I am using the Atheros ar928x with stock setup in Ubuntu 9.04.

I CAN connect to every other wireless network except in this one location in my school.

Wireless signal shows 80%+ so that's not an issue, no encryption or security, so forget that too..

here's the output of iwevent when I am trying to connect.

12:46:12.579215   wlan0    Scan request completed
12:46:12.585324   wlan0    Set Mode:Managed
12:46:12.585358   wlan0    Set Frequency:2.447 GHz (Channel 8)
12:46:13.279064   wlan0    Scan request completed
12:46:13.303054   wlan0    Custom driver event:ASSOCRESPIE=010882040b0c1216182432043048606c2d1a6e181bffff0000000000000000000000000000000000000000003d1608000700000000000000000000000000000000000000dd180050f2020101830003a4000027a400004243bc0062326600
12:46:13.307988   wlan0    New Access Point/Cell address:00:23:5E:AF:DE:00
12:46:52.675970   wlan0    Scan request completed
12:46:52.676029   wlan0    Set Mode:Managed
12:46:52.676360   wlan0    New Access Point/Cell address:Not-Associated
12:46:52.681887   wlan0    Set Frequency:2.462 GHz (Channel 11)
12:46:53.343034   wlan0    Scan request completed
12:46:53.344012   wlan0    Set Mode:Managed
12:46:53.350355   wlan0    Set Frequency:2.447 GHz (Channel 8)
12:46:54.031102   wlan0    Scan request completed
12:46:54.046760   wlan0    Custom driver event:ASSOCRESPIE=010882040b0c1216182432043048606c2d1a6e181bffff0000000000000000000000000000000000000000003d1608000700000000000000000000000000000000000000dd180050f2020101830003a4000027a400004243bc0062326600
12:46:54.052590   wlan0    New Access Point/Cell address:00:23:5E:AF:DE:00
12:46:59.206147   wlan0    New Access Point/Cell address:Not-Associated
12:46:59.220159   wlan0    Custom driver event:ASSOCRESPIE=010882040b0c1216182432043048606c2d1a6e181bffff0000000000000000000000000000000000000000003d1608000700000000000000000000000000000000000000dd180050f2020101830003a4000027a400004243bc0062326600
12:46:59.234993   wlan0    New Access Point/Cell address:00:23:5E:AF:DE:00
12:46:59.235218   wlan0    New Access Point/Cell address:Not-Associated

---

### Post by creeddd on 2009-09-03
me too i have the same problem someone has got to be able to solve it

---

