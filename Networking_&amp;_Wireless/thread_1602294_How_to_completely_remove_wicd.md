---
title: "How to completely remove wicd"
date: 2010-10-21
forum: Networking &amp; Wireless
---

### Post by Handssolow on 2010-10-21
Before I changed the faulty wifi card I installed Wicd. Incidentally it didn't remove Network Manager, a bug that's reported in Launchpad. With the new wifi working well enough with Network Manager, I used Synaptic to remove Wicid, or so I thought.

I happen to be checking .xsession-errors and there's an error reported about wicid tray desktop. I removed it and no more errors appear.

After looking for advice here and on the web I used apt-get remove and purge yet a file search of wicd still finds 25 entries, in /etc/, /usr/ and /var/.

Some are archives and some are logs but some aren't, why are they still there and can I clean things up?

---

### Post by bathacid on 2010-10-21
i always use the "sudo apt-get autoremove filename" command because it will delete the program and all the dependanceys and just add purge to the command so it should remove the config files for all the dependancys as well sorry for my spelling but give that a try (you may have to reinstall wicd so it can find all the programs used by wicd)

---

### Post by Handssolow on 2010-10-21
I reinstalled wicd followed by "sudo apt-get autoremove wicd" but search still finds 25 entries. It's like having a PC running Bill's software.

---

