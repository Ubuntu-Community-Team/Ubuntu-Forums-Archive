---
title: "Wireless for KDE"
date: 2006-06-14
forum: Networking &amp; Wireless
---

### Post by Cable on 2006-06-14
I got my wireless working perfectly using Network Manager in GNOME.  But, I'm still having problems finding a good app in KDE.  I can get it to connect in KDE (I think), but it messes with my /etc/network/interfaces file so that before I can get wireless in GNOME (using Network Manager) again, I have to comment a few lines out.  Any suggestions?

---

### Post by ltmon on 2006-06-15
You can run network manager in KDE fine (type nm-applet in a terminal) or you can enable the universe repository and:
```

sudo apt-get install knetworkmanager

```

It's a KDE frontend to exactly the same thing, so it should work pretty much the same as the gnome networkmanager.

L.

---

### Post by stupidkid on 2006-06-15
Can you post your /etc/network/interfaces?

Mine works fine under both gnome and kde.

```
iface eth1 inet dhcp
wireless_essid <essid>
wireless_key <key>

auto eth1

```

---

