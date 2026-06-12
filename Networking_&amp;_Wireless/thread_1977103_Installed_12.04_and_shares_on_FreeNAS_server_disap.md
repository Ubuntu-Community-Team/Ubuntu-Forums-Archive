---
title: "Installed 12.04 and shares on FreeNAS server disappear on my MAC OS X box (weird!)"
date: 2012-05-09
forum: Networking &amp; Wireless
---

### Post by Bullwinkle_Moose on 2012-05-09
I have three devices on my network that are not interacting properly since my install of Ubuntu Precise 12.04:

- A media center computer that was running Ubuntu Natty and is now*running Precise

- A Mac running OS X (Snow Leopard)

- A server running FreeNAS

The problem is that ever since I have upgraded the media center computer to 12.04, I've noticed that my FreeNAS SAMBA share disappears from my Mac Finder.  It's not that the FreeNAS server is down, because if I reboot the Mac the FreeNAS share comes back, but the problem started the same day I updated Ubuntu to 12.04.  It's very annoying, and while I understand that nothing I do with Ubuntu should have any effect on the Mac communicating with the FreeNAS server, that in fact does appear to be the case.

The FreeNAS shares have also disappeared from Nautilus in Ubuntu, but that doesn't seem to happen nearly as often.

I'm just wondering if anyone has seen anything similar happen since upgrading to 12.04 and if so, whether you were able to figure out what is causing the issue.

---

### Post by Bullwinkle_Moose on 2012-05-12
Just in case anyone else experiences this, going into /etc/samba/smb.conf and setting
**domain master = no**
under the "Misc" section, then restarting samba using
**sudo service smbd restart**
fixed the problem.

---

