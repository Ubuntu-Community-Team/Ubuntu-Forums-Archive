---
title: "Network (lan) folder synchronization"
date: 2010-09-04
forum: Networking &amp; Wireless
---

### Post by marsters256 on 2010-09-04
):P Working with ubuntu 10.04 LTS
I want to synchronize a folder on between two computers over my lan using the commandline or  script. 
Here is what I propose to do with the .sh, could you let me know if I'm aiming in the right direction please. 

1. Use samba to connect to the share from my other workstation
2. Mount the share
3. us Grsync to sync the local folder with the mounted folder. 

Is that what I need to figure out how to do? Is there an easier way?

---

### Post by procras on 2010-09-04
If both are ubuntu.

Set up ssh server on both
Use ssh-keygen to make public key
cat  public_key(from other box) >> ~/.ssh/authorized_keys on each box

Use rsync -e ssh /path/to/dir/ otherbox:/path/to/dir
in a cron job or manually.

---

### Post by clrg on 2010-09-04
If you just want to synchronize, there is no need for samba. rsync is able to connect to another computer all by itself :)

man rsync:


```
rsync(1)                                                              
NAME
       rsync — a fast, versatile, remote (and local) file-copying tool

SYNOPSIS
       Local:  rsync [OPTION...] SRC... [DEST]

       Access via remote shell:
         Pull: rsync [OPTION...] [USER@]HOST:SRC... [DEST]
         Push: rsync [OPTION...] SRC... [USER@]HOST:DEST

```

So you would do something like
```
rsync -av --update --delete --progress /source/directory user@remotehost:/target/directory
```

---

