---
title: "Wicd"
date: 2011-09-24
forum: Networking &amp; Wireless
---

### Post by nomko on 2011-09-24
If i install WICD, what's the benefit of this program over the standard Gnome networkmanager? And if i install WICD, does it remove the standard networkmanager?

---

### Post by papu40000 on 2011-09-24
Hi,

I think they are sincronizated.
Test to install and from terminal run
wicd-gtk
it would be appear near the other applet

I tried to connect wired conection with 1, and the other do the same.

Hope that helps,
papu

---

### Post by varunendra on 2011-09-24
> **nomko said:**
> If i install WICD, what's the benefit of this program over the standard Gnome networkmanager? And if i install WICD, does it remove the standard networkmanager?
Wicd is simpler than NetworkManager and, in some cases, works better with wifi, especially if the security type is WPA/WPA2 mixed type.

Installing it won't remove NM automatically, but you should do it manually. Using both at the same time may cause problems due to mutual conflict.

---

### Post by Enigmapond on 2011-09-24
> **varunendra said:**
> Wicd is simpler than NetworkManager and, in some cases, works better with wifi, especially if the security type is WPA/WPA2 mixed type.

Installing it won't remove NM automatically, but you should do it manually. Using both at the same time may cause problems due to mutual conflict.

You can actually have both installed just tell the startup apps to start one at boot and not the other. I have had both on a system before with no conflicts. Also it's better at the beginning justin case you can't get wicd to work properly as I just did a few minutes ago....

---

### Post by varunendra on 2011-09-25
> **Enigmapond said:**
> You can actually have both installed just tell the startup apps to start one at boot and not the other. I have had both on a system before with no conflicts. Also it's better at the beginning justin case you can't get wicd to work properly as I just did a few minutes ago....
O yeah.. that's a better suggestion :)

---

