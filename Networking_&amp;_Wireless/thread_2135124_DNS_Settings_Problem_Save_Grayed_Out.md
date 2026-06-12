---
title: "DNS Settings Problem Save Grayed Out"
date: 2013-04-13
forum: Networking &amp; Wireless
---

### Post by jeffblack18042 on 2013-04-13
xubuntu 12.04, using usb wireless adaptor. When I type in the address the save button grays out. Also in /etc/dhcp3/dhclient.conf has .save added and I can't edit that. I'm setting up ICS in an old PIII Everything works but I can't change to a different server. (opendns) Thank You

---

### Post by praseodym on 2013-04-13
You are using the network-manager? Start it from terminal via

```
gksu nm-connection-editor
```

---

