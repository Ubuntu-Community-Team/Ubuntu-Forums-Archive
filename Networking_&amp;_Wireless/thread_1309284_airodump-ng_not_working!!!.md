---
title: "airodump-ng not working!!!"
date: 2009-11-01
forum: Networking &amp; Wireless
---

### Post by waqarafzaal on 2009-11-01
i am getting this:

owner@ubuntu:~$ airodump-ng -c 6 --bssid 00:13:D4:E8:4F:14 -w output ath0
socket(PF_PACKET) failed: Operation not permitted
This program requires root privileges.
                                                                                  ](*,)

---

### Post by malcolmmersham on 2009-11-20
u need to be root

try sudo airodump
or sudo password
then su root

---

