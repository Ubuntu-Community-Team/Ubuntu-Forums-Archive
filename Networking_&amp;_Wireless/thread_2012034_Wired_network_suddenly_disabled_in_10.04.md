---
title: "Wired network suddenly disabled in 10.04"
date: 2012-06-28
forum: Networking &amp; Wireless
---

### Post by taipan67 on 2012-06-28
Apologies if this has been answered previously - i haven't done an extensive search because i'm not sure what search-terms would be best, plus having no internet is making me nervous and impatient...

Last night i accidentally hit 'Hibernate' (or 'Suspend'?) instead of 'Reboot' in my 10.04 system and when i restarted the PC after it had shut itself down, i no longer had a connection to my wired router.

I'm fairly confident that it's a software issue, as i'm writing this from a 12.04 system on the same PC (different partition).

NetworkManager appears to be running. "ifconfig -a" lists 'eth0' but in a 'down' state. "ifconfig eth0 up" changes the listing to 'UP' but doesn't grant any access...

...Probably because /etc/resolv.conf is empty (i use 'dhcp').

Any help with further diagnostic commands or fixes, or questions that i didn't think to answer up front, would be appreciated. ;) 

And before you ask, this PC doesn't do 3D, so i'd like to keep 10.04 usable, at least until i install 'Gnome-fallback' in 12.04 - coz 'Unity-2d' _ain't_ gonna grow on me, i'm afraid... :(

---

### Post by taipan67 on 2012-06-29
Fixed it, and thought i'd update the thread myself in case anyone else has a similar experience...

The file /etc/network/interfaces only contained...```
auto lo
iface lo inet loopback
```
...where the same file in 12.04 also contained...```
auto eth0
iface eth0 inet dhcp
```
Adding the latter to 10.04's version resolved the problem - though i've no idea how it occurred in the first place..? :???:

---

