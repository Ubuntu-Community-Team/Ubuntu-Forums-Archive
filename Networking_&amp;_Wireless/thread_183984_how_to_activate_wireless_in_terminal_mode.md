---
title: "how to activate wireless in terminal mode"
date: 2006-05-29
forum: Networking &amp; Wireless
---

### Post by villem123 on 2006-05-29
Hi all,

I didnt'succeed to make apt-get for Gnome as it requires network connection (to get the contact with repositories). Could someone help how to set up wireless in terminal mode. hardware was working, it needs only to activate enter the network key, make eth0 default and activate it. 

Waiting for your replies and best regards,

---

### Post by cskeide on 2006-05-29
Hi, edit your /etc/network/interfaces file to look similar to this one, (change the lines that are bold):```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet dhcp
        # wireless-* options are implemented by the wireless-tools package
        wireless-mode managed
        [B]wireless-essid essid
        wireless-key1 xxxxxxxxxxxxxxxxxxxxxxxxxx[/B]
```
Then type:```
sudo /etc/init.d/networking restart
```

---

### Post by villem123 on 2006-05-29
thanks for help

---

