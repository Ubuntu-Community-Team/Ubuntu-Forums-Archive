---
title: "need help setting up samba share (to share a folder on my linux box to windows client"
date: 2009-09-20
forum: Networking &amp; Wireless
---

### Post by jnw222 on 2009-09-20
this is becoming hard work trying to set this up.
i just cant get a working file share system working.

what i want to do. 
1. have my ext. drive attached to my desktop.
2. be able to access the drive on windows clients remotely from the same wireless network (as a network drive preferably).
3. windows clients able to write and run files on the drive.

sooo need help.

my server is running 9.04 with latest updates

---

### Post by scrooge_74 on 2009-09-20
You need to read up the samba manual to get a better grasp of what you need. 

You also need to install the samba server and open the ports for it to function properly, if Im not mistaken the Windows machines need to talk to your linux box using BIND for the name resolution part.

You are also going to need to export the disk as a share and you need to add to samba the users on the XP machines that will be using the drive. <-That all goes in the smb.conf file

Sorry being a while since I used samba, I'm just giving you a general idea of what you are going to face here.

[http://us1.samba.org/samba/](http://us1.samba.org/samba/)
[http://us1.samba.org/samba/](http://us1.samba.org/samba/)
[https://help.ubuntu.com/8.04/serverguide/C/installing-samba.html](https://help.ubuntu.com/8.04/serverguide/C/installing-samba.html)
[https://help.ubuntu.com/8.04/serverguide/C/configuring-samba.html](https://help.ubuntu.com/8.04/serverguide/C/configuring-samba.html)
[http://ubuntuforums.org/showthread.php?t=190542&highlight=open+port+138](http://ubuntuforums.org/showthread.php?t=190542&highlight=open+port+138)

---

### Post by dmizer on 2009-09-20
Right click on the folder, select "sharing options". Make sure all three boxes are checked, and install any software it tells you to.

Done.

---

### Post by jnw222 on 2009-09-20
i dont use the GUI/GNOME

maybe a sample working /etc/samba/smb.conf or so would be nice
this gets frustratng

---

### Post by badger_fruit on 2009-09-20
> **jnw222 said:**
> i dont use the GUI/GNOME

maybe a sample working /etc/samba/smb.conf or so would be nice
this gets frustratng


/etc/samba/smb.conf has many options and comments to help you with configuring your own samba server; here is a template i use, i copy and paste it into smb.conf, edit where appropriate and restart the samba service (sudo service samba restart)

```

[global]
        printing = cups
        printcap name = cups
        cups options = raw
        map to guest = Bad User
        include = /etc/samba/dhcp.conf
        usershare allow guests = Yes
        netbios name = MYCOMPUTERNAME
        workgroup = MYWORKGROUP
        server string = "COMPUTER DESCRIPTION"
        name resolve order = bcast host lmhosts wins

[A_SHARE]
        comment = SHARE COMMENTS
        path = /path/to/share
        guest ok = yes
        read only = no
        force user = name_of_local_user

```

---

### Post by dmizer on 2009-09-20
The default smb.conf should be sufficient. Just add your share definition at the end.

A working share definition might look like this:
```
[[COLOR="Red"]test[/COLOR]]
path = [COLOR="Red"]/mnt/raid/test[/COLOR]
browseable = yes
read only = no
guest ok = yes
```
Change [COLOR="Red"]test[/COLOR] to whatever you'd like your share to be named, and change [COLOR="Red"]/mnt/raid/test[/COLOR] to the actual location of your share.

---

### Post by jnw222 on 2009-09-20
my network must have something against file and printer sharing. i copied you r suggestion and restarted, but still didn't work (both windows computers didnt even see my desktop of the same workgroup.

---

### Post by dmizer on 2009-09-20
> **jnw222 said:**
> my network must have something against file and printer sharing. i copied you r suggestion and restarted, but still didn't work (both windows computers didnt even see my desktop of the same workgroup.

You can't just copy/paste.

You must make changes that match your own environment. I pointed out a few, and so did badger_fruit

---

### Post by jnw222 on 2009-09-20
i ment copied mut modified names paths, etc to fit my workgroup, folder, names. etc

---

### Post by badger_fruit on 2009-09-20
can your windows machine ping your ubuntu machine and vice-versa?

---

### Post by scrooge_74 on 2009-09-20
> **jnw222 said:**
> i ment copied mut modified names paths, etc to fit my workgroup, folder, names. etc

Did you took the time to read any documentation for samba? It would seem you just want people to give you a quick fix solution without learning how to do it, samba is one of those things you need to understand it so it dosent end up being a frustrating task

---

