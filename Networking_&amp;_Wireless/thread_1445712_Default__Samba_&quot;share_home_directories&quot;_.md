---
title: "Default  Samba &quot;share home directories&quot; + symbolic links?"
date: 2010-04-02
forum: Networking &amp; Wireless
---

### Post by Oblong_Cheese on 2010-04-02
I have set up a NAS-esque system, and I want to share five users' home directories automatically with Samba.

I had physically moved all the users home dirs to the other location using **usermod -d /var/data/username -m**, but then I thought "hang on, symlinks would be easier!" So I moved them all back again with **usermod -d /home/username** (without -m).

So I created four of those five users' directories with symbolic links, and sure enough, those four users' directories don't appear in the samba directory listing when viewed via network. :p

My question is: why? And how do I fix this?

Currently:

```

root@boxenmkiv:/home# ls -l
total 4
lrwxrwxrwx 1 brett brett   25 2010-04-03 08:48 brett -> /var/data/brett/
lrwxrwxrwx 1 carly carly   23 2010-04-03 08:48 carly -> /var/data/carly/
lrwxrwxrwx 1 dave  dave    21 2010-04-03 08:48 dave -> /var/data/dave/
lrwxrwxrwx 1 kate  kate    23 2010-04-03 08:47 kate -> /var/data/kate/
drwxr-xr-x 4 owen  owen  4096 2010-04-03 08:44 owen

```

My username (owen) is published fine via Samba. I can see it and login to it just fine on my Vista system.

Samba config:
```

[homes]
   comment = Home Directories
   browseable = yes
   # to try and see them, I set browseable to yes
   read only = no
   valid users = %S

```

This is the default "share home directories" config in Ubuntu Server 9.10, I've just uncommented it.

What have I broken, or what do I need to change, to make this work?

Thanks in advance!

---

### Post by capscrew on 2010-04-02
> **Oblong_Cheese said:**
> ...

So I created four of those five users' directories with symbolic links, and sure enough, those four users' directories don't appear in the samba directory listing when viewed via network. :p

My question is: why? And how do I fix this?

..

What have I broken, or what do I need to change, to make this work?

Thanks in advance!

Samba has changed the default settings for symlinks recently.  See [**_here_**]("http://ubuntuforums.org/showthread.php?t=1439092") for a fix.

See [**_here _**]("http://www.samba.org/samba/news/symlink_attack.html") for why.

---

### Post by Oblong_Cheese on 2010-04-03
OK, I fixed it myself.

If someone can explain why: all I did was log in to each user account (su'd from my own) and made the following addition to the [global] section of smb.conf: follow symlinks = yes

Though, apparently, in a newer version of Samba, an additional directive "wide symlink = yes" will need to be added, on account of [this](http://www.samba.org/samba/news/symlink_attack.html).

capscrew, thanks for the information - I guess that will apply to new versions of Samba; I have added that directive to my config but when doing an 'smbclient -L' now, it warns me that it is an unknown option.

---

### Post by capscrew on 2010-04-03
> **Oblong_Cheese said:**
> OK, I fixed it myself.

If someone can explain why: all I did was log in to each user account (su'd from my own) and made the following addition to the [global] section of smb.conf: follow symlinks = yes

Though, apparently, in a newer version of Samba, an additional directive "wide symlink = yes" will need to be added, on account of [this](http://www.samba.org/samba/news/symlink_attack.html).

capscrew, thanks for the information - I guess that will apply to new versions of Samba; I have added that directive to my config but when doing an 'smbclient -L' now, it warns me that it is an unknown option.

I guess they will have to re-write smbclient then. :D

---

