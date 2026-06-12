---
title: "Cant view some NFS Exports from Ubuntu to Ubuntu machine"
date: 2013-04-05
forum: Networking &amp; Wireless
---

### Post by wt9bind on 2013-04-05
Hi,

I am running NFS Exports on my "server" (Running 12.04 LTS Desktop) to my "Client machine) (Also Running 12.04 LTS Desktop).


[COLOR=#ff0000][SIZE=4]Server Side:[/SIZE][/COLOR]
Exports look like this:

```
# /etc/exports: the access control list for filesystems which may be exported
#               to NFS clients.  See exports(5).
#
# Example for NFSv2 and NFSv3:
# /srv/homes       hostname1(rw,sync,no_subtree_check) hostname2(ro,sync,no_sub$
#
# Example for NFSv4:
# /srv/nfs4        gss/krb5i(rw,sync,fsid=0,crossmnt,no_subtree_check)
# /srv/nfs4/homes  gss/krb5i(rw,sync,no_subtree_check)
#
/export *(insecure,no_subtree_check,rw,nohide,fsid=0)
/export/TVExtra    192.168.1.0/255.255.255.0(rw,sync,all_squash,insecure,anonui$
/export/Movies  192.168.1.0/255.255.255.0(rw,sync,all_squash,insecure,anonuid=1$
/export/Misc    192.168.1.0/255.255.255.0(rw,sync,all_squash,insecure,anonuid=1$
/export/TV/TV   192.168.1.0/255.255.255.0(rw,sync,all_squash,insecure,anonuid=1$
/export/FTP 192.168.1.0/255.255.255.0(rw,sync,all_squash,insecure,anonuid=1000,$
/export/Torrent 192.168.1.0/255.255.255.0(rw,sync,all_squash,insecure,anonuid=1$



```

FSTAB Looks like this:

```
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=f4fff3f1-1007-48df-b4c4-a59acd621102 /               ext4    errors=remoun$
# swap was on /dev/sda5 during installation
UUID=225e9a95-7f10-4fe6-8495-c47ba1d608a9 none            swap    sw           $
# movies entry
UUID=0000a369-1d53-49de-914d-0ae8b7b1c53c /media/Movies ext4    auto,rw 0      $
# TV Entry
UUID=900d9a55-413f-43a7-b473-3ebe7abcecc0 /media/TV     ext4    auto,rw 0      $
# Misc Entry
UUID=36aef72e-188f-4679-8f44-01e1a8a5a63f /media/Misc   ext4    auto,rw 0      $
# Kids Entry
UUID=025dc5a7-c33e-4727-bee8-81eb1fb46c64 /media/Kids   ext4    auto,rw 0      $

/media/Kids/TV  /export/TVExtra bind    bind    0
/media/Movies   /export/Movies  bind    bind    0
/media/Misc     /export/Misc    bind    bind    0
/media/TV       /export/TV      bind    bind    0
/home/ftp       /export/FTP     bind    bind    0
/var/lib/deluge /export/Torrent bind    bind    0

```
[B]
On My mac, I can access all NFS Exports perfectly fine[/B]

On my Ubuntu Client machine, I can't access the Kids or TV Directories

```
daniel@Jungceylon:/netfs$ ls -l
total 28
drwxrwxrwx  3 root   root   4096 Mar 26 20:20 FTP
drwxr-xr-x  2 root   root   4096 Mar  1 13:34 Kids
drwxrwxrwx 15 daniel daniel 4096 Oct  3  2012 Misc
drwxrwxrwx  5 daniel daniel 4096 Feb  2 20:36 Movies
drwxrwxrwx 13    116    125 4096 Mar  7 19:35 Torrent
drwxr-xr-x  2 root   root   4096 Mar  1 13:44 TV
drwxrwxrwx  5 daniel daniel 4096 Mar  1 17:29 TVExtra


```

How it looks on the server Side:

```
daniel@SVR1:/export$ ls -l
total 28
drwxrwxrwx  3 root   root   4096 Mar 26 20:20 FTP
drwxr-xr-x  2 root   root   4096 Mar  1 13:34 Kids
drwxrwxrwx 15 daniel daniel 4096 Oct  3  2012 Misc
drwxrwxrwx  5 daniel daniel 4096 Feb  2 20:36 Movies
drwxrwxrwx 13 deluge deluge 4096 Mar  7 19:35 Torrent
drwxrwxrwx  6 daniel daniel 4096 Dec  8 08:48 TV
drwxrwxrwx  5 daniel daniel 4096 Mar  1 17:29 TVExtra


```

I can see that the Kids Folder is not write in spots but the TV is full read write and can't be accessed from the Ubuntu Client machine.

Can anybody give me any suggestions?

Thanks.

---

### Post by lvlint67 on 2013-04-05
Can you post the fstab / mount command on the Linux client?

---

### Post by wt9bind on 2013-04-05
> **lvlint67 said:**
> Can you post the fstab / mount command on the Linux client?

Sure:

FSTAB:
```
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=6f9631f1-ef03-442f-a399-a1ef413d2c46 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=e38c41e0-f23c-4e95-ab49-423084e55d42 none            swap    sw              0       0
```

The Command I am using is:

```
daniel@Jungceylon:~$ sudo mount 192.168.1.99:/ /netfs


```

---

### Post by lvlint67 on 2013-04-05
Any luck if you try
sudo mount 192.168.x.x:/export /netfs

It looks like you are trying to mount the root of the server fs... Which afaict... Is not exported...

---

### Post by wt9bind on 2013-04-05
Thanks. I did this:

sudo mount 192.168.1.99:/export /netfs

daniel@Jungceylon:/$ cd netfs
daniel@Jungceylon:/netfs$ ls
FTP  Kids  Misc  Movies  Torrent  TV  TVExtra

All listed are Green except Kids and TV. I still can't get a directory listing in either of those directories.

Client:
daniel@Jungceylon:/netfs/TV$ ls -l
total 0

Server:
daniel@SVR1:/export/TV$ ls -l
total 20
drwxrwxrwx  2 root   root   16384 Sep  2  2012 lost+found
drwxrwxrwx 69 daniel daniel  4096 Mar 22 06:27 TV

---

### Post by SeijiSensei on 2013-04-05
Do you have identical copies of /etc/passwd and /etc/group on both machines so the user and group IDs are the same on both?

On the client, the directory Kids is owned by root, but the export has all_squash.  If you need to mount something as root on the client, you must use no_root_squash on the server.

---

### Post by wt9bind on 2013-04-05
> **SeijiSensei said:**
> Do you have identical copies of /etc/passwd and /etc/group on both machines so the user and group IDs are the same on both?

On the client, the directory Kids is owned by root, but the export has all_squash.  If you need to mount something as root on the client, you must use no_root_squash on the server.

Hi, no, I don't have identical copies of /etc/passwd or /etc/group. Do I actually have to have identical copies?

I have changed the Exports and it not looks like this:

```
# /etc/exports: the access control list for filesystems which may be exported
#               to NFS clients.  See exports(5).
#
# Example for NFSv2 and NFSv3:
# /srv/homes       hostname1(rw,sync,no_subtree_check) hostname2(ro,sync,no_subtree_check)
#
# Example for NFSv4:
# /srv/nfs4        gss/krb5i(rw,sync,fsid=0,crossmnt,no_subtree_check)
# /srv/nfs4/homes  gss/krb5i(rw,sync,no_subtree_check)
#
/export *(insecure,no_subtree_check,rw,nohide,fsid=0)
/export/TVExtra    192.168.1.0/255.255.255.0(rw,sync,no_root_squash,insecure,anonuid=1000,anongid=1000,no$
/export/Movies  192.168.1.0/255.255.255.0(rw,sync,no_root_squash,insecure,anonuid=1000,anongid=1000,no_su$
/export/Misc    192.168.1.0/255.255.255.0(rw,sync,no_root_squash,insecure,anonuid=1000,anongid=1000,no_su$
/export/TV/TV   192.168.1.0/255.255.255.0(rw,sync,no_root_squash,insecure,anonuid=1000,anongid=1000,no_su$
/export/FTP 192.168.1.0/255.255.255.0(rw,sync,no_root_squash,insecure,anonuid=1000,anongid=1000,no_subtre$
/export/Torrent 192.168.1.0/255.255.255.0(rw,sync,no_root_squash,insecure,anonuid=1000,anongid=1000,no_su$


```

I then ran on the server:

sudo exportfs -a

I then changed my password on my client machine to match the same password as the same user on the server being "daniel" as the username.

I then remounted /netfs but still have the same issue.

---

### Post by SeijiSensei on 2013-04-05
Get rid of anonuid and anongid.  My server has just rw, async, no_root_squash, and insecure as options.  "Insecure" allows connections where the client uses a port >1023 to connect to the server.  I mount everything as root, but access is still controlled since a user joe can only see files and directories that he or she has permissions for on the server.

The user and group IDs need to match on client and server if you need to preserve ownerships and permissions.

---

### Post by wt9bind on 2013-04-05
> **SeijiSensei said:**
> Get rid of anonuid and anongid.  My server has just rw, async, no_root_squash, and insecure as options.  "Insecure" allows connections where the client uses a port >1023 to connect to the server.  I mount everything as root, but access is still controlled since a user joe can only see files and directories that he or she has permissions for on the server.

The user and group IDs need to match on client and server if you need to preserve ownerships and permissions.

Thanks for the help.

I just changed it to:

```

# /etc/exports: the access control list for filesystems which may be exported
#               to NFS clients.  See exports(5).
#
# Example for NFSv2 and NFSv3:
# /srv/homes       hostname1(rw,sync,no_subtree_check) hostname2(ro,sync,no_subtree_check)
#
# Example for NFSv4:
# /srv/nfs4        gss/krb5i(rw,sync,fsid=0,crossmnt,no_subtree_check)
# /srv/nfs4/homes  gss/krb5i(rw,sync,no_subtree_check)
#
/export *(insecure,no_subtree_check,rw,nohide,fsid=0)
/export/TVExtra    192.168.1.0/255.255.255.0(rw,async,no_root_squash,insecure)
/export/Movies  192.168.1.0/255.255.255.0(rw,async,no_root_squash,insecure)
/export/Misc    192.168.1.0/255.255.255.0(rw,async,no_root_squash,insecure)
/export/TV/TV   192.168.1.0/255.255.255.0(rw,async,no_root_squash,insecure)
/export/FTP 192.168.1.0/255.255.255.0(rw,async,no_root_squash,insecure)
/export/Torrent 192.168.1.0/255.255.255.0(rw,async,no_root_squash,insecure)



```

I got this when running exportfs

```
sudo exportfs -a
exportfs: /etc/exports [2]: Neither 'subtree_check' or 'no_subtree_check' specified for export "192.168.1.0/255.255.255.0:/export/TVExtra".
  Assuming default behaviour ('no_subtree_check').
  NOTE: this default has changed since nfs-utils version 1.0.x

exportfs: /etc/exports [3]: Neither 'subtree_check' or 'no_subtree_check' specified for export "192.168.1.0/255.255.255.0:/export/Movies".
  Assuming default behaviour ('no_subtree_check').
  NOTE: this default has changed since nfs-utils version 1.0.x

exportfs: /etc/exports [4]: Neither 'subtree_check' or 'no_subtree_check' specified for export "192.168.1.0/255.255.255.0:/export/Misc".
  Assuming default behaviour ('no_subtree_check').
  NOTE: this default has changed since nfs-utils version 1.0.x

exportfs: /etc/exports [5]: Neither 'subtree_check' or 'no_subtree_check' specified for export "192.168.1.0/255.255.255.0:/export/TV/TV".
  Assuming default behaviour ('no_subtree_check').
  NOTE: this default has changed since nfs-utils version 1.0.x

exportfs: /etc/exports [6]: Neither 'subtree_check' or 'no_subtree_check' specified for export "192.168.1.0/255.255.255.0:/export/FTP".
  Assuming default behaviour ('no_subtree_check').
  NOTE: this default has changed since nfs-utils version 1.0.x

exportfs: /etc/exports [7]: Neither 'subtree_check' or 'no_subtree_check' specified for export "192.168.1.0/255.255.255.0:/export/Torrent".
  Assuming default behaviour ('no_subtree_check').
  NOTE: this default has changed since nfs-utils version 1.0.x


```

Now nothing is accessible.

---

### Post by SeijiSensei on 2013-04-07
The no_subtree_check replies are just warnings, I believe. Adding it back into the options list will make the warning go away.

I have no idea why you cannot now connect.  Is there some reason you need to export /export as well as the directories below it?  I only include specific declarations for the exported directories and nothing else, for instance:

```

/media/storage     192.168.0.0/16(rw,no_root_squash,async,insecure)
/media/external    192.168.0.0/16(rw,no_root_squash,async,insecure)

```

I'm pretty sure the old-style 192.168.1.0/255.255.255.0 syntax still works, but I prefer CIDR-addressing like the examples above.

---

