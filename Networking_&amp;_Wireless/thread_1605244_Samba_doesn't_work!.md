---
title: "Samba doesn't work!"
date: 2010-10-25
forum: Networking &amp; Wireless
---

### Post by xdominex on 2010-10-25
Hello,
I wanted to install Samba for file-sharing purposes on my home network, so I went ahead and installed the latest stable Samba release, but it doesn't respond to commands in terminal (i.e. sudo samba start, sudo samba stop, sudo samba restart, sudo samba /etc/init.d/samba restart...). My shared files are now viewable on other computers but completely unusable for file storage.

Samba DID respond when I was using Samba4, but when I used Samba 4 I got this:

```
matthew@Server:~$ samba restart
Unknown parameter encountered: "max log size"
Ignoring unknown parameter "max log size"
Unknown parameter encountered: "syslog"
Ignoring unknown parameter "syslog"
Unknown parameter encountered: "passdb backend"
Ignoring unknown parameter "passdb backend"
Unknown parameter encountered: "unix password sync"
Ignoring unknown parameter "unix password sync"
Unknown parameter encountered: "passwd program"
Ignoring unknown parameter "passwd program"
Unknown parameter encountered: "pam password change"
Ignoring unknown parameter "pam password change"
Unknown parameter encountered: "map to guest"
Ignoring unknown parameter "map to guest"
Unknown parameter encountered: "usershare allow guests"
Ignoring unknown parameter "usershare allow guests"
Unknown parameter encountered: "guest ok"
Ignoring unknown parameter "guest ok"
Unknown parameter encountered: "guest ok"
Ignoring unknown parameter "guest ok"
Unknown parameter encountered: "guest ok"
Ignoring unknown parameter "guest ok"
Unknown parameter encountered: "write list"
Ignoring unknown parameter "write list"
Unknown parameter encountered: "guest ok"
Ignoring unknown parameter "guest ok"
[Mon Oct 25 01:33:09 2010 CDT, 0 smbd/server.c:285:binary_smbd_main()]
samba version 4.0.0alpha9-GIT-9733816 started.
Copyright Andrew Tridgell and the Samba Team 1992-2009

```

So I either get a Samba that doesn't work at all (the current version), or a Samba that pretends to work but ignores all of my parameters, claiming that it doesn't recognize any of them. I searched through synaptic package manager to make sure I have every single code or management file that could possibly be helpful for using Samba.

Please help.

---

### Post by luvshines on 2010-10-25
I would suggest to downgrade from Samba 4 to Samba 3

Also, it will be ```
sudo service smbd restart/stop/start
```

---

### Post by xdominex on 2010-10-25
I've already downgraded to Samba 3. I will try reconfiguring my smb.conf file again, but I already tried this, and it didn't do anything.

---

### Post by Morbius1 on 2010-10-25
Samba3 is not a downgrade. It's the latest stable release. If you noticed Samba4 is in an alpha stage. After you configure your smb.conf again why not post it if you are still having problems:

> testparm -s
This will run a simulation of the smb.conf and output errors if it finds anything with the wrong syntax and also produce a very concise smb.conf for you to post to the forum.

---

### Post by luvshines on 2010-10-25
> **xdominex said:**
> I've already downgraded to Samba 3. I will try reconfiguring my smb.conf file again, but I already tried this, and it didn't do anything.

can you post output of```
testparm -sp
```

---

### Post by xdominex on 2010-10-25
Ah! I got it. Thank you for the time and help. I appreciate it a lot!

---

