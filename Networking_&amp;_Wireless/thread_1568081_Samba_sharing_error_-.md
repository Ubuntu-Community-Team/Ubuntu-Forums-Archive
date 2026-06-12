---
title: "Samba sharing error -"
date: 2010-09-04
forum: Networking &amp; Wireless
---

### Post by marsters256 on 2010-09-04
I can't share my /var/www folder on this machine - it worked fine on my Desktop, it just asked me to install the samba windows something. 
What's going wrong with this. 
I have searched for fixes to this issue with no luck. 

Here is the error I get after right clicking and going to sharing and trying to share the folder... 

```
Samba's testparm returned error 1: Load smb config files from /etc/samba/smb.conf
rlimit_max: rlimit_max (1024) below minimum Windows limit (16384)
Processing section "[printers]"
Processing section "[print$]"
Loaded services file OK.
WARNING: state directory /var/lib/samba should have permissions 0755 for browsing to work
WARNING: cache directory /var/cache/samba should have permissions 0755 for browsing to work

```have tried ```
sudo chmod 0755 /var/lib/samba
sudo chmod 0755 /var/cache/samba
```But no luck... Please help

---

### Post by marsters256 on 2010-09-04
Fixed it myself, thought I'd be nice and let you all know how I did it as per Ubuntu spirit.

```
sudo chmod 777 /etc/samba/smb.conf
sudo chmod 0755 /var/cache/samba
sudo chmod 0755 /var/lib/samba
```

added line 

```
usershare owner only = false ## added by ben
```

to global settings in /etc/samba/smb.conf file... 

If anyone knows why it didn't work straight away I'd love to know 'cas it worked on my desktop and I've updated ubuntu and restarted before I tried all this...

---

### Post by dmizer on 2010-09-04
Impossible to know now. We would have needed to see what the permissions were before you changed them.

---

### Post by marsters256 on 2010-09-05
Would the best way to see that be doing a ```
ls -la
``` on the directory/files?

---

### Post by dmizer on 2010-09-05
> **marsters256 said:**
> Would the best way to see that be doing a ```
ls -la
``` on the directory/files?

It will not matter because you have already changed them. You cannot see what they were before.

---

### Post by CharlesA on 2010-09-05
I checked what the permissions were set to on my clean server install:

```
charles@atlantis:~$ **ls -ld /var/lib/samba**
drwxr-xr-x 5 root root 4096 2010-09-04 22:43 /var/lib/samba
charles@atlantis:~$ **ls -ld /var/cache/samba/**
drwxr-xr-x 3 root root 4096 2010-09-04 22:43 /var/cache/samba/
charles@atlantis:~$ **ls -l /etc/samba/smb.conf**
-rw-r--r-- 1 root root 12416 2010-09-04 22:43 /etc/samba/smb.conf
charles@atlantis:~$
```

So unless you changed the permissions somehow, they should have been fine by default.

EDIT: Also, don't forget to make the thread as solved under thread tools. :)

---

### Post by cadcam on 2011-12-01
Dude, thank you.  Super useful......

A.

---

