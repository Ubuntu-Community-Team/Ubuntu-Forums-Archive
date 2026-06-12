---
title: "ZyXEL G-202 Wireless Modem With Ubuntu 11.04"
date: 2011-09-16
forum: Networking &amp; Wireless
---

### Post by gmseed on 2011-09-16
Hi

I've upgraded from Ubuntu v9 and my ZyXEL G-202 wireless modem used to work fine.

However, with the recently installed v11 it no longer works.

If I go to the NetWork Connections dialog and select the Wireless Tab and add a new connection, I can't get it to work.

I'm completing the SSID field, selecting Ad-hoc, Automatic Band, Automatic(DHCP) for iPv4 Settings and entering my security key for WPA & WPA2 Personal.

Has anyone any ideas?

Thanks.

Graham

---

### Post by gmseed on 2011-09-16
Just noticed that "wireless is disabled by hardware switch" is in the wireless pulldown.

Looks like others have experienced this problem:

[http://ubuntuforums.org/showthread.php?t=1745681](http://ubuntuforums.org/showthread.php?t=1745681)

I did as suggested:

lsmod | grep dell

followed by:

sudo rmmod -f dell_laptop
sudo rfkill unblock all

and restarted the laptop. However, it's still not working.

I see in the network connections pulldown on the top right that "Enable Networking" is enabled but "Enable Wireless" is disabled. Also, there is a menu item "Wireless Network (ZyDAS-ZyXEL G202)" listed but it is greyed out and still has the tag "wireless is disabled by hardware switch".

---

### Post by gmseed on 2011-09-16
Found the link:

[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper#autostart](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper#autostart)

I did what it suggested about installing the correct UCB wireless adpater driver, etc.

Still not working!!

---

