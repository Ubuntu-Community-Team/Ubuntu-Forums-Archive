---
title: "Network Places Trouble"
date: 2010-06-10
forum: Networking &amp; Wireless
---

### Post by bell53 on 2010-06-10
Hello, I'm new to Ubuntu.  Trying to make a switch in an office environment from Windows to Ubuntu.
I'm having a problem in that my file server does not show up in the Windows Network folder.  I can search it with smbclient and I can connect with "connect to server", but to replace windows my users need to access the share through the Windows Network folder.  Any thoughts on this?  Advice is much appreciated.

---

### Post by Iowan on 2010-06-10
(Yet) another weak area for me...
Dunno if your server checks in with DHCP server -  but by default, Ubuntu machines don't send their hostname. The option is there in */etc/dhcp3/dhclient.conf*. IF the machine has a static address, this probably doesn't apply...

---

