---
title: "Can connect with nm-applet but not with iwconfig"
date: 2010-02-21
forum: Networking &amp; Wireless
---

### Post by patrickdc on 2010-02-21
I have an Atheros AR928X Wireless Adapter (built in to laptop). I can connect to net works with nm-applet fine, but when I use iwconfig, There are no changes.
Example:
```
$ iwconfig wlan0 essid Convery
$ iwconfig
```
shows no changes, not even when I set the access point to the right address.

---

### Post by chili555 on 2010-02-21
Network Manager keeps tight control on our systems. It is unlikely to be able to manipulate your network devices, even if you stop it. You can control your network devices with iwconfig, /etc/network/interfaces, et al, only if you remove Network Manager.

---

### Post by patrickdc on 2010-02-21
but even when i stop the nm-applet process, I cannot connect. would removing nm-applet really be the only way?

---

### Post by northd_tech on 2010-02-21
wicd also requires **all other** Wireless Managers (Gnome's Network Manager and KDE's KNetworkManager, etc.) to be removed before you can run wicd (pronounced "wicked" ).  I've been using wicd for about a week now, and it seems more stable and more configurable IMHO.

YMMV.

---

