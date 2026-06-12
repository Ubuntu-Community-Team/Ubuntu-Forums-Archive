---
title: "Need help with samba file sharing"
date: 2009-07-31
forum: Networking &amp; Wireless
---

### Post by samabecker on 2009-07-31
HEY! I am completely new to linux... I'm running Xubuntu on one of my machines and xp on my other. I want to share files on my Xubuntu computer, I got it working and all but when i tried to write a file on to the xubuntu computer with my XP it gave me this error
 
"cannot create or replace linux: Access is denied.
 
Make sure the disk is not full or write-protected
and that the file is not currently in use"
 
The drive is not full, I unchecked "read only" and the file is not in use. 
 
what is wrong with it?!

---

### Post by swerdna on 2009-08-01
It will be a permissions conflict. I suspect the xp user is attaching as a guest. If so, she will attach as username "nobody" from group "nogroup". That user often doesn't have rights to change files unless you explicitly arrange them.

So, have a look here: [The Samba LAN Primer for Ubuntu: HowTo Set up an Ubuntu-Windows Home & Office LAN/Network]("http://ubuntu.swerdna.org/ubulanprimer.html")
In particular look at "A read-write share with guest access" and at "Usershares".

Tip: if you used the Nautilus share tool to set up the share make sure you checkmarked all the boxes as in this screenshot:
[http://ubuntu.swerdna.org/lanprimer/primer1.png](http://ubuntu.swerdna.org/lanprimer/primer1.png)

Tip: if you made a share by adding a so-called [stanza] to the config file, smb.conf, then make sure it contains the line:> read only = no

Tip: if you have guest access (no passwords to get in), make sure the permissions on the shared folder/s is/are drwxrwxrwx

If still flummoxed, tell us what you did to share files and give more information so we can guide you in ways more focused than the generalities I just gave.

---

### Post by dmizer on 2009-08-01
> **swerdna said:**
> Tip: if you made a share by adding a so-called [stanza] to the config file, smb.conf, then make sure it contains the line:
> read only = no


That or the option:
```
writeable = yes
```
Either is equally functional.

---

