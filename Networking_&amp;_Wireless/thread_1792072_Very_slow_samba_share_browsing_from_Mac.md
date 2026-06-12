---
title: "Very slow samba share browsing from Mac"
date: 2011-06-27
forum: Networking &amp; Wireless
---

### Post by pr0fess0r on 2011-06-27
Hi Guys, I'm running Mac OS on a home network that includes a Win 7 machine and a Ubuntu box (Ubuntu 11.04 (GNU/Linux 2.6.38-8-generic i686))
Connecting to, and browsing the shared drives I have on the Ubuntu box (which acts as my server) is extremely slow from the Mac, it seems that the icons especially take ages to load.
I've found a few suggestions on the net that I've implemented to no avail i.e.

socket options = TCP_NODELAY IPTOS_LOWDELAY SO_RCVBUF=65536 SO_SNDBUF=65536

Are there any other settings I should play with, or is there an alternative to samba that will work faster on a mixed network and be compatible with everything?

Cheers

---

### Post by kerry_s on 2011-06-27
go into synaptic, type "smb" in that search at the top. look for the 1 that is for compatibility, i think it was smbfs, sorry been awhile memories not what it was, i have my share on snow leopard now instead of linux.

---

### Post by pr0fess0r on 2011-06-27
Thanks kerry_s, I installed smbfs and restarted but it didn't make any difference.
Using a Mac with BBEdit looking at a share on the Ubuntu box, the php files in one can take 20 seconds or some to become scrollable and have all their icons displayed. It's ridiculous :/

---

