---
title: "[WIFI] Networkmanagers ****** up"
date: 2009-05-13
forum: Networking &amp; Wireless
---

### Post by shadowlemon on 2009-05-13
I'm running on the new Jaunty and reinstalled kubuntu yesterday to 9.04.

Since I was having some issues with networkmanagers I installed wicd yesterday and it doesn't seem to work. All of the drivers selected in advanced (wext,madwifi...)
do not work and do not give any wireless response allthough nm-applet and knetworkmanager work (no WPA though).

my question is:

how can I get nm-applet and Knetworkmanager back to work? it seemed that by installing wcid, they are ****** up and don't work anymore after uninstalling wcid...

I tried ```
 service NetworkManager start 
``` but has no effect at once...

OR

how can I get wcid to work? (install madwifi drivers/wext?)


my specs:
dell studio 1735 
Kubuntu 9.04

using: Dell wireless 1510 Wireless-N WLAN Mini-card


thanks in advance!

---

### Post by shadowlemon on 2009-05-13
bump

---

### Post by Peter09 on 2009-05-13
```
sudo apt-get install network-manager
```

---

### Post by shadowlemon on 2009-05-13
> **Peter09 said:**
> ```
sudo apt-get install network-manager
```

tried noteless times, when using the
service NetworkManager start 
it always says it's started, and effectively i can start nm-applet!

but i can't scan for networks

---

### Post by Peter09 on 2009-05-13
What does 

```
ifconfig
```

show

---

### Post by wirelessmonkey on 2009-05-13
Restart it...
```
sudo /etc/init.d/NetworkManager restart 
```

---

