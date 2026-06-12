---
title: "Mount network share into /home/user/Documents?"
date: 2011-09-01
forum: Networking &amp; Wireless
---

### Post by wheels83 on 2011-09-01
Is there a way to do it? It works the way I think it should when I mount it to /media/Documents, but I get nothing when I try to mount it in the home folder.

Is it a permissions issue?

Thanks,

Richard

---

### Post by northd_tech on 2011-09-01
If I understand you correctly, you want to mount a Windows Networking shared directory from another external computer somewhere on your network under Ubuntu.  Once that's done, I'm pretty sure that you can make a **symlink** under ~/Documents (but I'm not sure that is necessary):

**Creating a symlink in Ubuntu **
[http://www.herikstad.net/2009/07/creating-symlink-in-ubuntu.html](http://www.herikstad.net/2009/07/creating-symlink-in-ubuntu.html)

Do you know if you have Samba installed?  Post the results of this terminal command:

```
smbtree
```As an example, my **working** Samba setup tells me this for **smbtree** (where I can see a WinXP desktop with a HP PSC 1300 printer shared on the Workgroup MACHOME2):

> WORKGROUP
MACHOME2
    \\JELENA-HOME            JenaHome
        \\JELENA-HOME\C$                 Default share
        \\JELENA-HOME\H$                 Default share
        \\JELENA-HOME\ADMIN$             Remote Admin
        \\JELENA-HOME\print$             Printer Drivers
        \\JELENA-HOME\SharedDocs         
        \\JELENA-HOME\IPC$               Remote IPC
        \\JELENA-HOME\hppsc1300          hp psc 1300 series


EDIT:  If Samba is running properly, you should be able to browse around the Windows Network by going into Places > Network > Windows Network

---

