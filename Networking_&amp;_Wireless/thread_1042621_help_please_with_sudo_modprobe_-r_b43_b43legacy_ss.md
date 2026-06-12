---
title: "help please with sudo modprobe -r b43 b43legacy ssb ndiswrapper wl"
date: 2009-01-17
forum: Networking &amp; Wireless
---

### Post by bouzinsale on 2009-01-17
hi i have this command to connect my wireless gnetwork card

sudo modprobe -i lsbcmnds.inf
sudo modprobe -r b43 b43legacy ssb ndiswrapper wl
sudo modprobe ndiswrapper
sudo /etc/init.d/networking restart


but i have to do it every time i restart my computer my question is how to make it permanent thanks

---

### Post by Ayuthia on 2009-01-17
You probably only need to remove the b43 and ssb modules and reload ndiswrapper:
```
echo -e '#ssb/ndiswrapper workaround, added' `date` '\ninstall ndiswrapper modprobe -r b43 b43legacy ssb wl; modprobe --ignore-install ndiswrapper;' | sudo tee -a /etc/modprobe.d/ndiswrapper
```
The ndiswrapper -i command should not be needed because the driver should have already been loaded.

Also make sure that ndiswrapper is already loaded in /etc/modules:
```
cat /etc/modules|grep ndiswrapper
```
If it does not appear, then add it:
```
echo ndiswrapper | sudo tee -a /etc/modules
```

Hope that helps.

---

### Post by bouzinsale on 2009-01-17
thanked you worked perfect :popcorn:

---

