---
title: "Var/WWW still written to  incorrectly"
date: 2009-11-02
forum: Networking &amp; Wireless
---

### Post by Kat of Zion on 2009-11-02
Hello

Im attempting to write to another computer's /var/www directory.  However when I write it through SMB4K sharing, it still sets the owner of that file incorrectly (I want it to write the folder as www-data:www-data).  Instead, it writes the file with spotty:spotty.

For my SMB conf file, there is no global "force user" setting.  For the var/www, I have the following settings:

path = /var/www
writeable = yes
browseable = yes
read only = no
force create mode = 0755
valid users = www-data
force user= www-data
force group = www-data
create mask = 0755
directory mask = 0700

I have another share already hooked up that is for all home directories o that machine 

The force user in that case is = spotty.  Is that overriding even the force user under my var/www settings or is there something else?

---

### Post by Kat of Zion on 2009-11-03
Edit: So far besides being told "Im doing it wrong", I have been told that NFS is the better match.  How would I set this up.  I tried to start the nfs-kernel-server on the server I want to connect to with a remote desktop.  The result is, the starting nfs kernel daemon hangs for many minutes before saying "[ok]".   Im wondering if my dynamic IP for the computers (due to our wireless router) is the reason for this.

---

### Post by Iowan on 2009-11-03
[Here]("http://ubuntuforums.org/showthread.php?t=1311888") is an NFS How-To with a link to another one.

---

### Post by Kat of Zion on 2009-11-04
So far, I have encountered a couple of problems in my attempt.

1. The NFS kernel daemon seems to hang when it comes to starting (running the restart command).

2. Im still unable to use mount /var/www without lacking any result. Says that the fstab or mtab file doesnt list it, but thats not true. I did add it to both to make sure it finds it in one of these two, but to no avail

---

