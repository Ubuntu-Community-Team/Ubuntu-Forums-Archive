---
title: "Avahi finds nothing on localhost"
date: 2011-05-05
forum: Networking &amp; Wireless
---

### Post by Forseti on 2011-05-05
Hi,

I've got problem with Avahi on my laptop. It can see the other machines and services on the LAN but not it's own local services and I have no idea why.

The laptop (hostname: forseti) sports Ubuntu 10.10, installed aavahi-daemon, avahi-dnsconfd and libapache2-mod-dnssd. Firewall is disabled. Other hosts on the LAN are: magni (openSuSE 11.4 with lots of services published and visible from forseti) and freya (Ubuntu 10.10 with gnome-user-share up & running). Forseti can see the other hosts and their services but not itself. The other hosts can't see forseti. Checked both with nautilus and CLI's avahi-browse.

Any idea what's up? 

BR
Forseti

---

### Post by Forseti on 2011-05-08
I have to add that AppArmor is not the cause - I've uninstalled it and it didn't help.

---

