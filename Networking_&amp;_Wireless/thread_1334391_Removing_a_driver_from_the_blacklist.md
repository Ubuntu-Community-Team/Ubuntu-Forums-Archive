---
title: "Removing a driver from the blacklist?"
date: 2009-11-22
forum: Networking &amp; Wireless
---

### Post by jtwm0677 on 2009-11-22
I need to remove a blacklisted driver from the blacklist, and can't figure out how too.. Someone please help.. Very new to ubuntu, and the terminal commands.. Thanks in advance!!
the drivers listed in my blacklist are:
blacklist b43
blacklist b43legacy
blacklist ssb
blacklist bcm43xx

i need to remove anything related to my bcm4306 wireless card.
Thanks again

---

### Post by bkratz on 2009-11-22
> **jtwm0677 said:**
> I need to remove a blacklisted driver from the blacklist, and can't figure out how too.. Someone please help.. Very new to ubuntu, and the terminal commands.. Thanks in advance!!
the drivers listed in my blacklist are:
blacklist b43
blacklist b43legacy
blacklist ssb
blacklist bcm43xx

i need to remove anything related to my bcm4306 wireless card.
Thanks again

You could just put a # in front of the desired ones to "comment" them out and leave them there in case you need to put them back.
For instance, (only an example!)     #blacklist b43

---

### Post by gnusci on 2009-11-22
open a terminal and type:

$ gksudo /etc/modprobe.d/blacklist.conf

and then as bkratz said just put a # at the beginning of any line you want to remove.

---

### Post by jtwm0677 on 2009-11-22
Thanks, now that I've got that taken care of, any ideas why my BCM4306 isnt showing up in the proprietary drivers list? Could it have something to do with ndiswrapper and the fact that I'm having to use the windows driver for my wireless? If so, how can I stop using ndiswrapper and start using the ubuntu supported driver without the need for a wired connection? Thanks

---

