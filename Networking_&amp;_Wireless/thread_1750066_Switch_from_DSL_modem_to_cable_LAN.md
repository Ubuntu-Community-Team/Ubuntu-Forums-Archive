---
title: "Switch from DSL modem to cable LAN"
date: 2011-05-05
forum: Networking &amp; Wireless
---

### Post by MS6 on 2011-05-05
Hello everybody, I am using a Asus Notebook in 2 different networks- at home I am using a DSL-modem and at work I using the local area network of my institution. To switch between these two networks I have copied the /etc/network/interfaces to a /etc/network/interfaces.bak.

Now If I want to switch from DSL to cable LAN I remove the /etc/network/interfaces
and reboot the computer. If I want to switch back I simply copy  /etc/network/interfaces.bak to  /etc/network/interfaces and reboot the computer.

I know this is quick and very very dirty. Hence I am interested if this procedure could be performed in a better way (e.g. without reboot)?

---

### Post by dineshs on 2011-05-05
If you have network manager installed ,edit /etc/network/interfaces so that it contain only
```
auto lo
iface lo inet loopback
```
Configure DSL as in [http://ubuntuforums.org/showpost.php?p=9611335&postcount=9](http://ubuntuforums.org/showpost.php?p=9611335&postcount=9) 
Configure wired ethernet as in [http://ubuntuforums.org/showpost.php?p=9467538&postcount=5](http://ubuntuforums.org/showpost.php?p=9467538&postcount=5)
Now click on NM icon and connect DSL/ethernet as required

---

