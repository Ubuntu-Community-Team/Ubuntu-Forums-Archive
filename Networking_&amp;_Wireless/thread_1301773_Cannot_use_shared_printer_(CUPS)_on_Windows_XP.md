---
title: "Cannot use shared printer (CUPS) on Windows XP"
date: 2009-10-26
forum: Networking &amp; Wireless
---

### Post by jon80 on 2009-10-26
Within CUPS ([http://localhost:631/printers](http://localhost:631/printers)) the printer appears as published, although I still cannot see it as a share from my laptop. For example, if I key in \\computer name on my Windows-XP laptop, there is no shared printer to connect.

1. I checked the following:
Start > System Settings > Server Settings

Share published printers connected to this system is checked. 

2. I have tried the following command, however, it seems that it cannot be resolved this way (suggested in link #2).

sudo adduser administrator lpadmin
...
The user 'administrator' is already a member of lpadmin.

Any ideas?

Ubuntu 9.04
CUPS 1.3.9

Related links:
1. [https://answers.launchpad.net/hplip/+question/86357](https://answers.launchpad.net/hplip/+question/86357)
2. [http://ubuntuforums.org/archive/index.php/t-407716.html](http://ubuntuforums.org/archive/index.php/t-407716.html)
3. [http://blog.mypapit.net/2008/05/enable-printer-sharing-with-ubuntu-computers.html](http://blog.mypapit.net/2008/05/enable-printer-sharing-with-ubuntu-computers.html)

---

