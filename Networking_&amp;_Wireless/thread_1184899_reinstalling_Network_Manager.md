---
title: "reinstalling Network Manager"
date: 2009-06-11
forum: Networking &amp; Wireless
---

### Post by silkwj on 2009-06-11
Hi All,

I tried to set my installation of 9.04 to static ip, using the edits to /etc/network/interfaces and /etc/resolv.conf shown in many posts all over tis forum and others. Part of that process includes uninstalling Network Manager because of potential conflicts. Well, now my internet is broken. How do i reinstall Network Manager and get back on DHCP, without a functioning connection?

Thanks!

---

### Post by pedja_portugalac on 2009-06-11
Using Synaptic you can install network-manager-gnome, or

sudo atp-get install network-manager-gnome

---

### Post by silkwj on 2009-06-11
apt-get says it's already installed, Synaptic wants to download packages from the internet. can't i make it pull the packages from the CD?

---

### Post by dwanders on 2009-06-11
System -> Administrator -> Software Sources

Change it to CD Only

---

### Post by dwanders on 2009-06-11
could also try sudo apt-get remove network-manager-gnome 
then try re-installing it

---

### Post by silkwj on 2009-06-11
now Synaptic says it has no available version but it exists in the database.

---

