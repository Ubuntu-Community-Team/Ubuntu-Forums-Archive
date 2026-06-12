---
title: "Sharing options config file location"
date: 2010-01-20
forum: Networking &amp; Wireless
---

### Post by top_bullfrog on 2010-01-20
Hello,

I enabled file sharing in nautilus by right clicking on a folder, clicking "Sharing options" and doing my configuration from there.  I'd like to be able to further configure this share through webmin, which looks for the Samba config in /etc/samba/smb.conf, the default location for samba.  For some reason when Sharing options is used to configure file shares, it doesn't write the config into the default samba config file.  Any idea where else I might look to find where Sharing options writes the config?  I've looked through smb.conf for references to other files and saw nothing.  Thanks for any help.

Top_bullfrog

EDIT: Ubuntu 9.10

---

### Post by ubername on 2010-01-20
Have a look at 

[http://ubuntuforums.org/showthread.php?t=1129647](http://ubuntuforums.org/showthread.php?t=1129647)

---

### Post by top_bullfrog on 2010-01-20
Thanks!

---

### Post by Morbius1 on 2010-01-20
/var/lib/samba/usershares

You can also get a quick display by issuing the following command in a terminal: **net usershare info**.

[COLOR=Blue]EDIT: [/COLOR]Just so you know, unlike classic samba that has it's share definitions in smb.conf, nautilus-share does not allow any of the usual parameters to be set at the share level like valid users, create mask, things like that. You can set for read /write and guest / no guest and that's about it. You can make parameter entries into smb.conf but all will be global.

---

