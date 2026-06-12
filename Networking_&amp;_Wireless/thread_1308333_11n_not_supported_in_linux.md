---
title: "11n not supported in linux?"
date: 2009-10-31
forum: Networking &amp; Wireless
---

### Post by simon82 on 2009-10-31
I have a d-link dwa-140 (rt2870) usb wifi card. but i only get 54mbit in Ubuntu 9.10, Under Vista i get 270mbit. 

does linux only have support for 54Mbit connections or have i missed something?

/Simon

---

### Post by brandon88tube on 2009-10-31
I have the same card as you... how did you get yours to work?

---

### Post by simon82 on 2009-10-31
i added rt2800usb to the blacklist file in /etc/modprobe.d/blacklist.conf

hope it works, took me an entire day to get that to work :(

---

### Post by steev182 on 2009-10-31
I have a Linksys 802.11n PCI card that runs at 270mbps just nicely, so it must be the driver that's being a pain. Although you could look at iwconfig and see what that says.

---

### Post by brandon88tube on 2009-10-31
So all you did was add "blacklist rt2800usb" into your blacklist.conf file and it worked for you? I just tried that with no luck.

---

