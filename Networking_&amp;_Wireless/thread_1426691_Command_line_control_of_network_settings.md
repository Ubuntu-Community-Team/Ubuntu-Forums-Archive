---
title: "Command line control of network settings"
date: 2010-03-10
forum: Networking &amp; Wireless
---

### Post by Digimer on 2010-03-10
Hi all,

  I frequently ssh into machines to do work. In some cases, the machine is headless so there is no option to log in.

  Under Debian and on older versions of Ubuntu I would pull out the avahi and network-manager packages and manually configure the interfaces file to my liking and be done with it.

  However, I would now like to learn how to work within avahi/network manager. So, is there a doc somewhere explaining how to work with modern Ubuntu networking at the command-line level? Ie: Setting up a wireless connection, setting static/dynamic IPs, etc?

  Thanks in advance!

Digi

---

### Post by Digimer on 2010-03-15
Bump.

Anyone?

---

### Post by helgman on 2010-03-15
Hi,

Don't know if this might be something to investigate:

[http://ubuntuforums.org/archive/index.php/t-937554.html](http://ubuntuforums.org/archive/index.php/t-937554.html)

Regards,
Helgman

---

### Post by chili555 on 2010-03-15
> However, I would now like to learn how to work within avahi/network manager.Does Network Manager exist within these headless beasts? As far as I know, NM is strictly a GUI front-end. I believe it is therefor not available if there is no log-in and some display manager is not running.

In this case, I think the old way, *interfaces*, is the best way.

If you have installed a server edition of Ubuntu, NM is probably not even installed and so there is no need to rip it out, although it might be quite emotionally satisfying.

---

