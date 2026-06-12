---
title: "Samba / Network share access issues"
date: 2010-12-04
forum: Networking &amp; Wireless
---

### Post by Richipedia on 2010-12-04
Hi all,

Having some major issues with networking on a fresh Ubuntu 10.10 install. Whenever I try to access the Windows Network I get the error message: 

[CENTER][B]Unable to mount location
Failed to retrieve share list from server[/B][/CENTER]

I've tried working through some of the solutions to similar issues in other threads but not had any success. I've tried reinstalling the Samba service. Checking **smbtree** in Terminal prompts for my password but then shows nothing; when I try and trace this back with **smbtree -N -d 2** I get:

smbtree -N -d 2
rlimit_max: rlimit_max (1024) below minimum Windows limit (16384)
added interface wlan0 ip=fe80::223:6cff:febf:9f98%wlan0 bcast=fe80::ffff:ffff:ffff:ffff%wlan0 netmask=ffff:ffff:ffff:ffff::
added interface wlan0 ip=10.0.0.19 bcast=10.0.0.255 netmask=255.255.255.0
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/gencache.tdb: Permission denied
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No such file or directory

This then repeats several times before self-terminating. I've even tried manually restarting the nmbd and smbd services, but in each case get the message that the service is unrecognised. I'm now completely stuck and have no idea how to proceed. Anyone have any idea how to fix these issues?

Regards,

R.

---

