---
title: "WLAN disabled on startup"
date: 2011-04-04
forum: Networking &amp; Wireless
---

### Post by weathercast0 on 2011-04-04
Hey guys,
i got a problem with NetworkManager.

Everytime i start my computer i have to enable WLAN, by changing this option in the Networkmanager...
Somehow it won't be saved!

i tried editing: /var/lib/NetworkManager/NetworkManager.state
-> after reboot: option set to false again

i am using Kubuntu 10.10 with KDE 4.6
on my Acer 1551 (Broadcom BCM43225, STA driver)!

thanks in advance,
weathercast0


edit:
Just wrote a shell script, which is executed before KDE-Login

> dbus-send --system --type=method_call --dest=org.freedesktop.NetworkManager /org/freedesktop/NetworkManager org.freedesktop.DBus.Properties.Set string:org.freedesktop.NetworkManager string:WirelessEnabled variant:boolean:true

---

