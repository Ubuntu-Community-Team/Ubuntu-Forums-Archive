---
title: "Ubuntu 18.04 too heavy for my laptop?"
date: 2018-09-08
forum: Multimedia Software
---

### Post by livino2 on 2018-09-08
Hi,

I'm thinking Ubuntu 18.04 is too heavy for my computer.

My computer is from 2011 (HP Pavillion G7 with 3,3 Gig memory).

I'm running Darktable, Qmapshack, GIMP and some more programs but it seems to me that that's too much for my pc. (Darktable told me once it couldn't analyse the problem 'cause I was not having enough memory).

Could that be the main problem? Or is such a computer normally good enough for this type of use?

Lieven

---

### Post by TheFu on 2018-09-08
It depends.  If you run a light-DE and only 1 of those programs at a time, and have a sufficiently large swap, it should work. The size of the swap should be tuned based on the complexity of the data used by the programs, but should be at least 4.1G.
  Darktable and Gimp are very heavy.

If you post the output from** inxi -Fz** that would provide the details needed to make a better assessment. That command removes any identifiable information like MAC.

---

### Post by Autodave on 2018-09-08
Moving to a lighter desktop would certainly help: Ubuntu is very heavy in memory usage compared to Lubuntu or Xubuntu. Lubuntu is the lightest, Xubuntu just slightly heavier.  All of the same programs can be installed on any of them.

---

### Post by TheFu on 2018-09-08
> **Autodave said:**
> Moving to a lighter desktop would certainly help: Ubuntu is very heavy in memory usage compared to Lubuntu or Xubuntu. Lubuntu is the lightest, Xubuntu just slightly heavier.  All of the same programs can be installed on any of them.

Actually, there isn't any need to reinstall just to get a different desktop. 

There are packages for the DEs. Install a few alternates, logout, pick the other DE, and login to try it.  Best to use a temporary userid for this testing for a few reasons.  But you can just backup your HOME to mitigate most of those issues. Be certain you can put it back.  Each DE will save config stuff and sometimes it isn't completely compatible with other DEs.  You've been warned. Much easier to just create a new userid and use that.  Afterwards, remove it and wipe that userid's HOME.

Or consider not using a DE at all, just use a straight window manager like openbox.  It doesn't alter useability much, IMHO and saves a 200MB or so in RAM use.

---

