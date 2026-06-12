---
title: "Ubuntu 9.04 not detecting Router"
date: 2009-08-30
forum: Networking &amp; Wireless
---

### Post by AngelAir on 2009-08-30
I hope that someone can help me with this problem or guide me in the right direction.

I recently upgraded from Ubuntu 8.04 to Ubuntu Studio 9.04 and also replaced my Lynksys BEFW11S4v4 with the WRT160Nv2.  There are to systems connected to the router:  1) A Windows XP and 2) The Ubuntu Studio 9.04.  Both systems connect to the Internet fine; but, on the US9.04 the icon with the two monitors (that shows your network connection) have a [COLOR="Red"]red x[/COLOR] on it.

The first time that I installed Ubuntu 8.04 after configuring the NIC; the system connected to the Internet and the router (BEFW11S4v4) was detected without any configuration on my part.

Please Help!

---

### Post by Iowan on 2009-08-30
Wired or wireless? You can check [this]("http://ubuntuforums.org/showthread.php?t=1156441") one to see if disabling rfc3442 will help.

---

### Post by dbalascak on 2009-08-30
So what is the problem that you are experiencing?  Both systems communicate with the Internet. Is it just the icon that is red?  Or is there a connectivity problem?  The icon will have a red X unless you have configured the system to use NetworkManager to configure the interfaces.  By default the interface configuration is in the file */etc/networks/interfaces*.

---

