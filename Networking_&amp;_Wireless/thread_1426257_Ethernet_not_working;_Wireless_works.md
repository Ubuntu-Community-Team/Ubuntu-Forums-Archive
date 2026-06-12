---
title: "Ethernet not working; Wireless works"
date: 2010-03-10
forum: Networking &amp; Wireless
---

### Post by christopherbalz on 2010-03-10
Realized that the ethernet on my machine (ThinPad R51 running Ubuntu 9.10 up-to-date

    //cbalz-tp-r51-0/.../~ $ uname -a
    Linux cbalz-tp-r51-0 2.6.31-20-386 #57-Ubuntu SMP Mon Feb 8 11:42:49 UTC 2010 i686 GNU/Linux

likely does not work when I tried without success to connect to the Internet via a known working 2wire dsl modem (3800HGV-B) via ethernet, and then tried reach without success a known working new dlink router on its subnet i.p. (I reached and configured the dlink router instead on a Mac).


With previous updates and versions of Ubuntu, the ethernet always worked fine on my box. 

Wireless works fine with the dlink modem (the 2wire drops it constantly, but the dlink connection is solid).

//cbalz-tp-r51-0/.../~ $ cat /etc/network/interfaces
auto lo
iface lo inet loopback

auto eth0
#iface eth0 inet dhcp

auto eth2
#iface eth2 inet dhcp

auto ath0
#iface ath0 inet dhcp

auto wlan0
#iface wlan0 inet dhcp


#iface eth1 inet dhcp

//cbalz-tp-r51-0/.../~ $

---

