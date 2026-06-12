---
title: "Network Manager Applet"
date: 2010-10-16
forum: Networking &amp; Wireless
---

### Post by visys on 2010-10-16
I have assigned ip address to laptop by editing /etc/network.interfaces. From next reboot the Network Manager Applet which was present on right hand upper corner, disappeared. I wonder why? This has happened with 9.04, 9.10 and now in 10.04. Another question is, are Network Manager settings (ip) and /etc/network/interfaces do correspond to same thing or not? As I have narrated above, since network manager applet is no more visible how to see the physical network cable connectivity status (as we do in windows xp)? (is there any other app of such kind or what?) this helps lot.

---

### Post by Iowan on 2010-10-16
Network Manager and */etc/network/interfaces* are opponents - odd as that may sound. NM (arguably) generally doesn't mess with interfaces configured in */etc/network/interfaces*. Ordinarily, NM can be used to set up static addresses for interfaces. Either way *should* work - but...

---

### Post by visys on 2010-10-18
Thanks Iowan, well thats strange isn't it?

---

