---
title: "xorg.conf no longer present after using 'failsafe'"
date: 2011-08-12
forum: Multimedia Software
---

### Post by lewys93 on 2011-08-12
Hi,
I managed to break my xorg.conf file earlier today and used the failsafe method to restore it.
I no longer have the file xorg.conf in /etc/X11/, but I do have several, including the xorg.conf.failsafe (which I presume X is currently using) and a number of backups.

How can I reconfigure X so that it uses one of the backup files I made (renamed to xorg.conf, the default)?
I didn't want to just rename it and delete the failsafe one just in case it doesn't work

(I've tried searching for this, but I can't find anything relating to my problem)

Thanks in advance.

Edit: From what I gather, X uses xorg.conf.failsafe only if the usual xorg.conf isn't present. I wrote a new xorg.conf file and everything seems to be working fine. I know that the 'normal' xorg.conf file is being used because I added the string not to show the nVidia logo (the failsafe version of xorg.conf does show the nidia logo)

---

