---
title: "Only root can write to cifs mount?"
date: 2010-02-17
forum: Networking &amp; Wireless
---

### Post by jorx on 2010-02-17
Hi everybody!

I'm trying to talk the studio I work at into switching one of the departments to linux. (likely kubuntu). So I'm trialling it, but having issues mounting windows shares.

It's working great; all except that only Root can write to the mount.  I've tried a few different things with fstab, no go.

Below is my fstab so far, and you can see the mountpoints.


```
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda5 during installation
UUID=4c6a53a9-8e35-4d40-886b-b4ad244d43c8 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=e88dbe14-f66a-4049-9406-550dc278fa01 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

# added by jorx
//172.17.255.2/projects    /mainserv/main/projects        cifs credentials=/etc/samba/auth.smb,rw    0 0

```

I've tried adding (,rw) to the options as you can see, also UID=1000.  Also, the auth.smb file indicated contains my windows login, which has write access from windows xp.

I eagerly anticipate your advice!
Cheers,
Jordan/Jorx

---

### Post by suseendran.rengabashyam on 2010-02-18
Hi,

Try the following steps in your Ubuntu machine and let me know if it works

1) Open a Terminal and enter the following:

```
sudo id user_name
```

The output will be something similar to:

```
uid=1000(user_name) gid=1000(user_name) groups=...
```

Make a note of the uid and gid.

2) Make the following entry in your /etc/fstab file :

If you don't need a user name and password to access a samba share add this line:

```
//server_name/share_name /mount_path cifs defaults,uid=1000,gid=1000 0 0
```

If you need a user name and password to access a samba share add this line and proceed to the next 2 steps:

```
//server_name/share_name /mount_path cifs defaults,uid=1000,gid=1000,credentials=/root/.smbcredentials 0 0
```

Modify the server_name, share_name, mount_path, UID value and GID value to suit your environment.

"uid=1000,gid=1000" entry will result in mounted share being owned by the uid=1000 and gid=1000.

4) Add the following in /root/.smbcredentials:

```
username=myusername
password=mypassword
```

Where myusername and mypassword is the user name and password to access the samba share.

5) Set the following permission to /root/.smbcredentials

```
chmod 600 /root/.smbcredentials
```

6) Now try to login as a particular user and see whether you able to read and write to the share.

---

### Post by jorx on 2010-02-18
Suseendran!

That works perfectly!

I had been googling for ways to look up the UID; but not really knowing the right keywords so I couldn't figure it out.
Your steps worked perfectly in my case; and made a bit better sense then the ubuntu documentation.

Thank you very very much! I have learned alot, and am excited to be working under linux (mint)!

---

