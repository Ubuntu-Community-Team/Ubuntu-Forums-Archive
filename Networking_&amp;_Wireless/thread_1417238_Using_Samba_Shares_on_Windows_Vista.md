---
title: "Using Samba Shares on Windows Vista"
date: 2010-02-27
forum: Networking &amp; Wireless
---

### Post by gpuckett on 2010-02-27
I setup shares on a fresh install of Ubuntu 9.10 via the shared folders application from here [https://help.ubuntu.com/9.10/internet/C/networking-shares.html](https://help.ubuntu.com/9.10/internet/C/networking-shares.html)

The shares are visible on my vista laptop but when I go to open them I get an error "you might not have permission to use this network resource".

I set the smbpswd to nothing via the method in the above article as well and my /etc/samba/smd.conf has the follow lines:

[300]
path = /media/Secondary Storage
available = yes
browsable = yes
public = yes
writable = no

[500]
path = /media/New Volume
available = yes
browsable = yes
public = yes
writable = no

Any help would be greatly appreciated.

---

### Post by Iowan on 2010-02-27
I'll need to check some other threads - but the spaces in the path names *might* be causing a problem.

---

### Post by gpuckett on 2010-02-27
That's what I had thought, I tried /media/'Secondary Storage' and no go.

---

### Post by gpuckett on 2010-02-27
Along with "/media/Secondary Storage"
and /media/Secondary\040Storage
and /media/"Secondary Storage"

"/media/Secondary Storage" is the only one that gives me the same error.  I get a cannot connect error from windows when I use any other method.

---

### Post by Morbius1 on 2010-02-27
Maybe this isn't a samba problem, maybe this is a linux file permissions problem. Post the output of the following command:

**ls -al /media**

---

### Post by gpuckett on 2010-02-27
total 32
drwxr-xr-x  6 root     root      4096 2010-02-26 23:58 .
drwxr-xr-x 22 root     root      4096 2010-02-26 23:51 ..
lrwxrwxrwx  1 root     root         6 2010-02-26 19:52 cdrom -> cdrom0
drwxr-xr-x  2 root     root      4096 2010-02-26 19:52 cdrom0
lrwxrwxrwx  1 root     root         7 2010-02-26 19:52 floppy -> floppy0
drwxr-xr-x  2 root     root      4096 2010-02-26 19:52 floppy0
drwx------  1 gpuckett gpuckett  4096 2010-02-18 08:02 New Volume
drwx------  1 gpuckett gpuckett 12288 2010-02-18 08:02 Secondary Storage

---

### Post by Morbius1 on 2010-02-27
Yep, 
> drwx------  1 gpuckett gpuckett  4096 2010-02-18 08:02 New Volume
drwx------  1 gpuckett gpuckett 12288 2010-02-18 08:02 Secondary Storage     Samba says that guests can access the share. Linux says no they can not. Lixux always wins these arguments.
In fact,  linux says that only one user can access the target directory and that's gpuckett.

The simplest fix is to add the following line to each share [300] and [500]
```
force user = gpuckett
```Save smb.conf, and in a Terminal issue a : [B]sudo service samba restart

[/B]This will create a mask that makes the guests look like you to linux but samba will still restrict permissions to read only.

---

### Post by gpuckett on 2010-02-27
THANK YOU, works perfectly now. Seems like a simple step that should be added to the documentation for shares to work with windows.

---

