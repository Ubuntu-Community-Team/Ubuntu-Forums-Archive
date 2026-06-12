---
title: "Cannot connect to Wireless Router"
date: 2009-04-03
forum: Networking &amp; Wireless
---

### Post by Kenny_C on 2009-04-03
Hi guys.
I have beentrying to connect my computer to my wireless network. The cumputer is running dual boot, with windows XP and Ubuntu 7.10. after a lot of playing about, I managed to get my Belkin wireless N1 +MIMO USB adapter to work with ndiswrapper, and network manager now sees all networks in the vicinity, including mine. However, when I selsct my own network, enter the passkey, it simply does not connect, it just says connected to network 0%. Windows can connect no problems at all. My router is a Belkin wireless N1 +MIMO router. Can anybody help?

---

### Post by CyberMando on 2009-04-03
sudo aptitude install wicd
It will remove network-manager and replace it with a reliable little program called wicd. I sure hope the KDE network applet matures soon.

---

### Post by Kenny_C on 2009-04-03
right... I've installed Wicd, and I cannot get it to work. I mean, it seems to run, but nothing appears in the taskbar, and I cannot access it to change settings. What now?

---

### Post by imdano on 2009-04-06
Run ```
wicd-client
```You should see the tray icon pop up in your taskbar.  Click it and the main GUI will pop up.

---

