---
title: "network-manager-gnome supports WPA?"
date: 2008-12-29
forum: Networking &amp; Wireless
---

### Post by kelinu on 2008-12-29
Hi,
I have this problem with Ubuntu 8.04 (well actually it's Linux Mint but it works all the same).  It just won't connect wireless.  I am stuck with this wire running across the hall, which becomes incredible annoying.  I use network-manager-gnome, with the nm-applet thing. It seems to be detecting the actual network, it's just the security of the network is set to WPA-PSK, and it looks as though network-manager-gnome does not support the encryption type.

I then tried uninstalling network-manager-gnome and installing wcid.  The problem with wcid is that sometimes it detected my network and sometimes it didn't.  And when it actually did detect my network, it automatically detected it as WEP and not WPA-PSK! And it would refuse me saying that it was not WEP but in actual fact WPA!

Next I tried wifi-radar.  Wifi-radar found the network, but when I clicked connect it just didn't manage to.  It didn't ask me to select security type, to input any password, nothing.  So that was pretty useless.

Now I have reinstalled network-manager-gnome once again, and I'm stuck with that wire across the hall, once again.  What to do?!

Any help is REALLY REALLY appreciated,

Kelinu

---

### Post by zrs_12 on 2008-12-29
Try a different encryption type.  To do this, reset the router, then goto it's page (normally 192.168.0.1) and from there, you should be able to set it up with a different encryption type and key.

---

### Post by kelinu on 2008-12-29
I don't want to go to WEP though, its just not as secure as WPA!

---

### Post by zrs_12 on 2008-12-29
Some computers/OSes just flat-out don't support WPA.  If you don't live in close proximity to your neighbors, though, WEP should be fine.

---

### Post by razy60 on 2008-12-29
you need to install nm0.7 as it does support WPA, i have it as that is what sky uses.

Raz

---

