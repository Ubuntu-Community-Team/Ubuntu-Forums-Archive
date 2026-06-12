---
title: "console equivalent to &quot;activate&quot; button"
date: 2006-03-25
forum: Networking &amp; Wireless
---

### Post by TLE on 2006-03-25
Hey everybody
Just a quick question. I'm trying to install xubuntu via server install on an old pc, but for some reason it does not activate the eth0 on startup (after install). So I re-installed in normal mode and found out that starting network-admin (in GNOME) choosing eth0 and pressing activate does the trick. So the only problem as that network-admin does not run in terminal in server mode, so my question is:
Does anybody know what the console equivalent to this action (network-admin eth0 activate) is?
Thanks in advance

PS: If I'm missing this info in the forum please just redirect me, I did try searching but found it difficult to find this particular info.

---

### Post by ranf on 2006-03-26
```
sudo ifconfig eth0 up
sudo dhclient eth0
```

There also is an `ifup' command.

---

### Post by rattking on 2006-03-26
check and see if eth0 (or whatever eth# you are using) is in
the auto line of /etc/network/interfaces
eg.
auto lo eth0

reboot and see if eth0 is automatically started on boot
more info
man interfaces

---

### Post by TLE on 2006-03-26
Great thanx a lot, there actually was no auto line in the /etc/network/interfaces     added it and now it works

---

