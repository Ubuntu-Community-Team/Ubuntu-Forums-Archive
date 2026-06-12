---
title: "Vnc"
date: 2009-04-25
forum: Networking &amp; Wireless
---

### Post by boondocks on 2009-04-25
We have:

A Windows XP system with one network card and ip address [COLOR="Red"]192.168.3.12[/COLOR]

A Ubuntu 8.10 system with 3 network cards:
[INDENT]1st card has ip address [COLOR="Red"]192.168.3.14[/COLOR]
2nd card has ip address [COLOR="Blue"]192.168.6.22[/COLOR]
3rd card has ip address [COLOR="Green"]192.168.9.35[/COLOR]
[/INDENT]
From the Ubuntu system, you can do:
[INDENT]vncviewer [COLOR="Red"]192.168.3.n[/COLOR]
vncviewer [COLOR="Blue"]192.168.6.n[/COLOR]
vncviewer [COLOR="Green"]192.168.9.n[/COLOR]
[/INDENT]
But from the Windows XP system, you can only do:
[INDENT]TightVNC [COLOR="Red"]192.168.3.n[/COLOR][/INDENT]

So how do you:
[INDENT]TightVNC [COLOR="Blue"]192.168.6.n[/COLOR] hosts from Windows XP, via the Ubuntu system
TightVNC [COLOR="Green"]192.168.9.n[/COLOR] hosts from Windows XP, via the Ubuntu system[/INDENT]

---

### Post by p388l3s on 2009-04-28
You are trying to see across subnets, to do this on your windows PC you would need to set your subnet to 255.255.0.0 instead of 255.255.255.0

Also you would need to ensure that there are routes to the other 2 subnets setup on both the ubuntu box AND on your windows PC to route through the ubuntu box.

Also I'm not sure but I would think you would need a route pointing back to your windows box from the ubuntu box so that the ubuntu box knows what to do with the network traffic flowing through it to the windows box, although that *MAY* be taken care of by the normal routes setup by ubuntu for each nic.

hope this helps.

Pebbles

---

