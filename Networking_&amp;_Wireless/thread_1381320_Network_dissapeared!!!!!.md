---
title: "Network dissapeared!!!!!"
date: 2010-01-14
forum: Networking &amp; Wireless
---

### Post by oldsoundguy on 2010-01-14
OK,  yesterday had a power outage and was able (thanks to battery back up) get all my computers shut down cleanly and had to turn off my router in order to have enough back up to run my cable modem .. as it is my phone also.

Once everything came back up, I rebooted each machine .. 2 XP machines, 2 9.10 machines, 1 8.04 machine (main box), 1 Mint machine (latest build) and one Mythbuntu  machine (again latest build).

The Windows computers see each other still, but NONE of the Ubuntu based machines can see each other nor can they see the Windows set up sufficiently to MOUNT (they DO show up in places/network .. but get mount error(s)).

ALL computers can get on line via the router.

But have lost print sharing also.
EVERYTHING was working prior to the outage and subsequent shut down.

Went so far as on one machine removed everything Samba and re-installed to no avail.

---

### Post by oldsoundguy on 2010-01-15
conditions remain the same, even after removing all traces of a network from everything and then re installing the networks in both the XP machines and the Linux machines.

Did we get an update recently that could have caused this?
(There were updates on the day of the power failure!)

---

### Post by superprash2003 on 2010-01-15
make sure that all ubuntu machines have an ip address and all machines can ping each other..

---

### Post by oldsoundguy on 2010-01-16
> **superprash2003 said:**
> make sure that all ubuntu machines have an ip address and all machines can ping each other..

If you will note .. all machines went on line.  They could not TALK to each other.

Problem solved, though.  

Re-boot and select repair in Grub.  Everything is back to normal.

---

