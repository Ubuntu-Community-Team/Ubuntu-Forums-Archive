---
title: "sync system accounts with samba"
date: 2010-02-03
forum: Networking &amp; Wireless
---

### Post by Tompalaz on 2010-02-03
Hey.

I've searched the web, read the man pages etc but I cant find a option to accomplish this.

What I want is to use the systems account as the samba accounts.
In school we have a project to simulate some sort of corporation with different platforms. I've created a map called shared and for authentication the users should only need to be a member of the group employees. (force group = groupname in smb.conf right?)

Now, I don't want to create the users with smbpasswd -a because there is alot of accounts and the users should be able to choose their own passwords. 

So, is it possible to sync the system accounts with samba and only use group as authentication? 

Thanks.

---

### Post by Tompalaz on 2010-02-05
There is this option: sync unix accounts, but this doesn't seem to work or is it a way to update the samba user database?

---

### Post by johnson.d on 2010-02-11
You have to perform a few more steps in Ubuntu to sync the unix users and the password with samba. You may find the following link helpful

[http://jaka.kubje.org/infodump/2007-05-14-unix-samba-password-sync-on-debian-etch/](http://jaka.kubje.org/infodump/2007-05-14-unix-samba-password-sync-on-debian-etch/)

---

