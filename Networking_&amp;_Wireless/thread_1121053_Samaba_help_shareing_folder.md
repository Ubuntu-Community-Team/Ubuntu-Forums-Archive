---
title: "Samaba help shareing folder"
date: 2009-04-09
forum: Networking &amp; Wireless
---

### Post by crash893 on 2009-04-09
Hi all

I made a share in unbuntu called \\server\home

and its mapped \home on the unbuntu server


I made a group  grp-backup 



[Home]
        comment = Backup Drive
        path = /home
        browseable = no
        writeable = yes
        write list = @grp-backup
        read only = no

        veto files = /.recycle/
        vfs object = recycle
                recycle:keeptree=True
                recycle:versions=True
                recycle:touch=True
        hide dot files = yes

        force directory mode = 0770
        force create mode = 0660
        force group = grp-backup

        valid users = @grp-backup
        invalid users =


The problem is that though i can see all the users home drives i dont have permissions to read inside 

what do i need to change to have the grp-backup have read  or read/write access to the drives and not messup the owners (aka the users) permissions?


thanks if you can help

Crash

---

