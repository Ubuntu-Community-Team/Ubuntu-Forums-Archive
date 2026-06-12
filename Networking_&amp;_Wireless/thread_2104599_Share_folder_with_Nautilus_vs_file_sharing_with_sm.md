---
title: "Share folder with Nautilus vs file sharing with smb.conf"
date: 2013-01-13
forum: Networking &amp; Wireless
---

### Post by okos on 2013-01-13
Hello,

When I set a folder to be shared through Nautilus, what exactly gets changed?

Just to clarify, with smb.conf, I can set a folder to be shared. For example, I can add the following to smb.conf to share a folder in my home folder:
```
[okos]
path = /home/okos/dshare
available = yes
browsable = yes
public = no
writable = yes
comment = dshare
```

In order to edit smb.conf, I must have root authority. However, if I set my folder to share with Nautilus, I do it as a user instead of root. I do not think sharing a folder with nautilus changes smb.conf because, as a user, I am not escalating my authority to root. So my question is, what exactly happens when I share a folder using nautilus?

Thanks in advance.

---

### Post by okos on 2013-01-13
I found this thread which gives some explanation:
[http://ubuntuforums.org/showthread.php?t=1129647](http://ubuntuforums.org/showthread.php?t=1129647)

[http://ubuntuforums.org/showthread.php?t=1502265](http://ubuntuforums.org/showthread.php?t=1502265)

---

### Post by okos on 2013-01-13
Here is more info:

When you use nautilus to share a folder, a file is also created in /var/lib/samba/usershares. That folder directs the permissions.

---

### Post by sisco311 on 2013-01-13
> **okos said:**
> because, as a user, I am not escalating my authority to root. 


Are you sure?  

My understanding is that there are at least three ways to escalate privileges: 

1. setuid executables like sudo, su, gksu, mount, ping, chsh, passwd... ( mostly used in the CLI )

2. `server/client' method: the `server' runs as a privileged process and decides if an unprivileged process is allowed (and if so how) or not to escalate its privileges. Most modern GUI apps use this method. Take a look at polkit (formerly known as PolicyKit)


3. root exploit/vulnerability (not so common)  :)

---

### Post by bab1 on 2013-01-13
> **sisco311 said:**
> Are you sure?  

My understanding is that there are at least three ways to escalate privileges: 

1. setuid executables like sudo, su, gksu, mount, ping, chsh, passwd... ( mostly used in the CLI )

2. `server/client' method: the `server' runs as a privileged process and decides if an unprivileged process is allowed (and if so how) or not to escalate its privileges. Most modern GUI apps use this method. Take a look at polkit (formerly known as PolicyKit)


3. root exploit/vulnerability (not so common)  :)

Samba usershares were created specifically to allow a non-root user to create shares.  The shares normally are in the users home directory.  The permissions are either the user only or everyone AFAIK.  There is no root user escalation needed.

---

### Post by okos on 2013-01-13
Thank you for the information.

Okos

---

