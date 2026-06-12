---
title: "WiFi emitting strength"
date: 2009-10-28
forum: Networking &amp; Wireless
---

### Post by tata_tulen on 2009-10-28
Hello,

is there any way to limit the WiFi card emitting strength? My notebok battery seems to be discharged in a short time (much shorter then with Vista).

Ubuntu 9.04

Thanks!

---

### Post by pat.gleeson on 2009-10-28
Hi there,

Not sure reducing the strength of the card would have very much difference in battery life. Maybe a small difference at best. Anyway, there is a command to reduce the tx power of a card but it will only work with certain cards (notoriously buggy).
**txpower** For cards supporting multiple transmit powers, sets the transmit power in dBm. If *W* is the power in Watt, the power in dBm is *P = 30 + **10.log**(W)*. If the value is postfixed by *mW*, it will be automatically converted to dBm.
In addition, *on* and *off* enable and disable the radio, and *auto* and *fixed* enable and disable power control (if those features are available).
**Examples :**
*   iwconfig eth0 txpower 15*
*   iwconfig eth0 txpower 30mW*
*   iwconfig eth0 txpower auto*
*   iwconfig eth0 txpower off*
[http://linux.die.net/man/8/iwconfig](http://linux.die.net/man/8/iwconfig)Anyway, hope this helps :-)

Good luck,

Pat.

---

### Post by tata_tulen on 2009-10-30
Thanks, Pat!

I'll try it. I supppose the 'power eater' is the WiFi (if I disable it, the life of battery get longer...)

---

