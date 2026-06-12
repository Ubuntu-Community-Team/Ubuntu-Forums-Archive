---
title: "wlan 0 missing"
date: 2009-11-24
forum: Networking &amp; Wireless
---

### Post by glaeven on 2009-11-24
I just upgraded (and by that i mean clean installed) to 9.10 on a fairly old toshiba sattelite. wireless has always been an issue, and i normally have to install wicd to get ubuntu to use my wireless card (dwl-650+).

but after this last install, the wireless card doesnt seem to show up at all. wicd says it cannot find any networks, and iwconfig only reports eth0 and lo, no wlan0.

any help? i would love to have this working by tomorrow.

---

### Post by glaeven on 2009-11-25
I tried installing 9.04 and upgrading using update manager. i got 9.04 working and installed wicd and the wireless card worked perfectly. then i used the update manager, over wifi, and not wicd doesnt detect my card.

iwconfig only lists eth0 and lo, no wlan0. lshw -C network shows the card, but says "*.network UNCLAIMED"

please help.

---

### Post by lexfati on 2009-11-27
Not having your interface wlan0 is a sign that your driver isn't loading.  If you had built the driver before on a previous kernel it will have to be rebuilt or replaced.

Depending on your chipset, you might be able to find your driver from [[COLOR="blue"]madwifi-project.org[/COLOR]]("http://madwifi-project.org/").  At least according to this [[COLOR="Blue"]chart[/COLOR]]("http://linux-wless.passys.nl/query_part.php?brandname=D-Link").

---

