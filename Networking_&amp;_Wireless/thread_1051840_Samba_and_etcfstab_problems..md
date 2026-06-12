---
title: "Samba and /etc/fstab: problems."
date: 2009-01-27
forum: Networking &amp; Wireless
---

### Post by ienabellamy on 2009-01-27
Hello everyone.

Platform: Ubuntu 8.10 AMD64
Problem:

when i try to mount a directory on Windows Server 2003 with this command:

```
user@ubuntu810server:~$ sudo smbmount //10.0.0.100/christopher /mnt/backup -o user=Christopher
```

this prompt me the password, i put in and _all works fine_. 

When i try to mount it with this line in fstab

```
//10.0.0.100/christopher /mnt/backup cifs user,credentials=/root/.credentials 0 0
```

or use the option "credentials", **this happens:**

```
user@ubuntu810server:~$ sudo smbmount //10.0.0.100/christopher /mnt/backup -o credentials=/root/.credentials
[B]mount error 13 = Permission denied
Refer to the mount.cifs(8) manual page (e.g.man mount.cifs)[/B]
```

Naturally the credentials file (/root/.credentials) is owned by root, 400 of permissions and respect the format:
```
user=Christopher
password=rotfl
```

The error in /var/log/messages is this:

```
[78465.762172] Status code returned 0xc000006d NT_STATUS_LOGON_FAILURE
[78465.762184]  CIFS VFS: Send error in SessSetup = -13
[78465.903886]  CIFS VFS: cifs_mount failed w/return code = -13
78498.812426]  CIFS VFS: Unexpected SMB signature

```

I must use a credentials file, because i wish mount the windows dir from fstab.

Another information is this strange thing:
i've a password long. If i try to do this:
```
user@ubuntu810server:~$ sudo smbmount //10.0.0.100/christopher /mnt/backup -o user=Christopher,password=22charslenghtpassword
**password too long**
```

But i remember you that:
```
user@ubuntu810server:~$ sudo smbmount //10.0.0.100/christopher /mnt/backup -o user=Christopher
```

and prompting the password, works perfectly.

i wish only mount that damn directory from fstab, using a credentials file :-(

Any helps would be appreciate. very very thanks

---

### Post by Iowan on 2009-01-27
Certainly not my specialty - my info comes from [here]("http://ubuntuforums.org/showthread.php?t=288534").
I notice **dmizer** has "sudo chmod 700 /root/.smbcredentials". Also, he has fstab line:```
//netbiosname/sharename    /media/sharename        cifs    credentials=/root/.smbcredentials,iocharset=utf8,file_mode=0777,dir_mode=0777 0 0
```

---

### Post by ienabellamy on 2009-01-28
Thanks for the reply Iowan: i've tried, but it's the same...same errors :-/

Anyone ? this problem make me crazy :(

edit: i've tried to insert the option "nounix" in fstab, as the tutorial that you have linked say...but...it's the same :-/

---

### Post by ienabellamy on 2009-01-29
UP !

help me, please !:(

---

### Post by ienabellamy on 2009-01-29
I've resolved !!!!!!!!!!


the credentials file was:
```
user=jessicaalba
password=shessohot
```


WAS WRONG !!!!!

the correct format IS.

```
username=jessicaalba
password=shessohot
```


RTFM, RTFM,RTFM, RTFM,RTFM, RTFM,RTFM, RTFM,RTFM, RTFM,RTFM, RTFM,RTFM, RTFM,RTFM, RTFM,RTFM, RTFM,RTFM, RTFM,RTFM, RTFM,RTFM, RTFM,RTFM, RTFM,RTFM, RTFM,RTFM, RTFM,RTFM, RTFM,RTFM, RTFM,RTFM, RTFM,RTFM, RTFM,RTFM, RTFM,RTFM, RTFM

---

### Post by MorayJ on 2010-03-30
Thank you for 'fessing up! Been banging my head against a very similar problem with a very similar solution.

Many thanks.
Moray

---

