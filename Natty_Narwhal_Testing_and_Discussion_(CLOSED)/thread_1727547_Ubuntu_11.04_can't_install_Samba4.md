---
title: "Ubuntu 11.04 can't install Samba4"
date: 2011-04-12
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by joaowojcikiewicz on 2011-04-12
Hello ubuntuforums' members!

I have upgraded ubuntu 10.10 to 11.04 (natty), and at the end of it's upgrade, I got a error message about samba4. The installation finish "successfully", then I rebooted my machine. It was alright at this point. 
After I login, the first missing feature I notice was my Emerald theme. I tried to run "emerald --replace", but all title bars of all windows gone. So I run "compiz --replace" and them didn't appear! I thought compiz was the default WM.
Alright, now at this point my problems just begun.
I have completely removed emerald, and when I reinstalled it, I got samba4 error message again.
Every time I try to install anything, it can't be installed just because samba4. 

Here's the Terminal output when I try to install samba4:
```
joaowojcikiewicz@ubuntu:~$ sudo apt-get install samba4
Reading package lists... Done
Building dependency tree       
Reading state information... Done
samba4 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? 
Setting up samba4 (4.0.0~alpha15~git20110124.dfsg1-2ubuntu1) ...
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
ldb: unable to stat module /usr/lib/samba/ldb/modules/samba : No such file or directory
ldb: failed to initialise module /usr/lib/samba/ldb/modules/samba : Unavailable
ldb: failed to initialise module /usr/lib/samba/ldb/modules : Unavailable
WARNING: Module [samba_dsdb] not found - do you need to set LDB_MODULES_PATH?
Unable to load modules for /var/lib/samba/private/sam.ldb: Failed to load modules from: /usr/lib/samba/ldb

Traceback (most recent call last):
  File "/usr/share/samba/setup/upgradeprovision", line 1597, in <module>
    ldbs = get_ldbs(paths, creds, session, lp)
  File "/usr/lib/python2.7/dist-packages/samba/upgradehelpers.py", line 159, in get_ldbs
    ldbs.sam = SamDB(paths.samdb, session_info=session, credentials=creds, lp=lp, options=["modules:samba_dsdb"])
  File "/usr/lib/python2.7/dist-packages/samba/samdb.py", line 53, in __init__
    options=options)
  File "/usr/lib/python2.7/dist-packages/samba/__init__.py", line 110, in __init__
    self.connect(url, flags, options)
  File "/usr/lib/python2.7/dist-packages/samba/samdb.py", line 66, in connect
    options=options)
_ldb.LdbError: (80, 'Failed to load modules from: /usr/lib/samba/ldb\n')
dpkg: error processing samba4 (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 samba4
E: Sub-process /usr/bin/dpkg returned an error code (1)
joaowojcikiewicz@ubuntu:~$ 
```I can't figure out what to do, and I haven't tried anything, because if I remove something I can't reinstall it later.
Anybody else have this problem and solved it?

Thank you.

---

### Post by wolfen69 on 2011-04-12
Upgrading can be touch and go normally, but when you upgrade to a Beta version, you are begging for problems. I suggest a clean install to set things right.

---

### Post by uRock on 2011-04-12
Moved to NNT&D

---

### Post by dvicino on 2011-04-19
hi, 
I had same issue, 
The only thing that worked for me was to-remove the samba4 package, it uninstalled a few libraries also, but nothing was really using, you still keep the samba-common and samba-lib from previous version anyway.

sudo aptitude remove samba4

be sure of read what you removing before comfirm

Damian

---

### Post by Morbius1 on 2011-04-19
This is the description of Samba4 in synaptic:
> These packages contain snapshot versions of Samba 4, the next-generation version of Samba. These should be considered _experimental_, and should not be used in production. In particular, no guarantees are made with regard to upgrades between versions. I don't know why it's in the repository. Unless you have a specific reason for needing Samba4 I wouldn't install it. Like many things in software newer != better.

---

