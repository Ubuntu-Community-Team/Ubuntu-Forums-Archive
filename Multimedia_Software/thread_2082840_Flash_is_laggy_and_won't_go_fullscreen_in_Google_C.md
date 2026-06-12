---
title: "Flash is laggy and won't go fullscreen in Google Chrome"
date: 2012-11-10
forum: Multimedia Software
---

### Post by SiflOlly on 2012-11-10
It is fine when small format, but when you hit full screen it gets very laggy in Firefox, and it won't go full screen in Google Chrome.  It was working fine.  And now it's not.

---

### Post by Halbblutplins on 2012-11-11
For me helped this:

```
cd /usr/lib/flashplugin-installer
``````
sudo perl -pi.bak -e 's/libvdpau/lixvdpau/g' libflashplayer.so
```[B]

--------------------------------------------------[/B]

or this method:
```
sudo gedit /etc/apt/apt.conf.d/70debconf.
```Remove everything in file and put in

```
APT::Cache-Limit "100000000";
```then just do:

```
sudo apt-get clean && sudo apt-get update --fix-missing
```Peter

---

