---
title: "adding privledges to shares"
date: 2009-05-25
forum: Networking &amp; Wireless
---

### Post by WinterMadness on 2009-05-25
i have my entire desktops file system accessible to me, but i would like to have it so someone has to enter a password to gain access, as it stands right now anyone on the network (who uses linux) can freely go through my shares

thanks a ton

---

### Post by WinterMadness on 2009-05-25
bump

---

### Post by dmizer on 2009-05-25
What protocol are you using to share your shares (NFS, Samba, FTP ...)? How did you configure them in the first place?

---

### Post by WinterMadness on 2009-05-25
> **dmizer said:**
> What protocol are you using to share your shares (NFS, Samba, FTP ...)? How did you configure them in the first place?


im using samba, and I setup the share just by right clicking the folder i wanted to share and clicking sharing options

on the computer i did this one, it didnt have samba but it installed it right after

---

### Post by superprash2003 on 2009-05-26
go to your /etc/samba/smb.conf file and add a line (to the shared folder which you want password protected) like

valid users = username

 where username is the user you wish to give access to

---

### Post by dmizer on 2009-05-26
> **superprash2003 said:**
> go to your /etc/samba/smb.conf file and add a line (to the shared folder which you want password protected) like

valid users = username

 where username is the user you wish to give access to

I don't believe this will work, as "username" will need to be given an account on the server. Also, since the share was not configured with /etc/samba/smb.conf, this edit probably won't work anyway.

I'll have to look at this when I get home as it's been too long since I tried to make the GUI work for file sharing.

---

### Post by superprash2003 on 2009-05-26
well no harm in getting a username on the server.. well it does go on the smb.conf file atleast for me on a gutsy machine..

---

