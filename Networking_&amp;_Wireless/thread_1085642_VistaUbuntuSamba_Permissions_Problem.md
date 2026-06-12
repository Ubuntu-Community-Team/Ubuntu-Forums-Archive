---
title: "Vista/Ubuntu/Samba Permissions Problem"
date: 2009-03-03
forum: Networking &amp; Wireless
---

### Post by phildacey on 2009-03-03
I have some files stored on my Ubuntu server. These are accessed via samba from my Vista laptop. For some reason that I can't work out, I can't manipulate the files in one of the folders.

The folder, 'Incoming' can be written to by a p2p program that runs on my vista laptop. However, I cannot write to this location in any other way. I can't move files about in Midnight Commander (run using sudo), I can't run sudo mkdir:

```
 server@fileserver:~$ sudo mkdir /mnt/tunes/Tunes/Incoming/test
[sudo] password for server:
mkdir: cannot create directory `/mnt/tunes/Tunes/Incoming/test': Read-only file system
```
 
The fstab entry doesn't seem to make it a read only file system:

```
UUID=038676d2-4264-4b78-a927-a0f62e0d62ad       /mnt/tunes              ext3    defaults        0       2

```

These are the permissions:

```
server@fileserver:~$ ls -l /mnt/tunes/Tunes/
drwxr-xr-x 203 server 1004 24576 2009-03-02 01:12 Incoming
```

And this is the smb.conf entry

```
[Tunes]
    path = /mnt/tunes
    browseable = yes
    read only = no
    guest ok = no
    create mask = 0644
    directory mask = 0755
```


I'm looking at other folders with the same permissions and I can use them as expected. I'm logging into my server from vista with the same u/n and password as the admin on the server (is that a good idea?)

Any help will be greatfully received :)

---

