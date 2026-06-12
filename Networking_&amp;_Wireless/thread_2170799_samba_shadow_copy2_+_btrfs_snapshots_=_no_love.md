---
title: "samba shadow_copy2 + btrfs snapshots = no love"
date: 2013-08-27
forum: Networking &amp; Wireless
---

### Post by andriy-golovnya on 2013-08-27
Hi everyone!

I'm trying to use **btrfs snapshot** feature together with **samba shadow_copy2** to add the snapshots to **'previous version'** properties tab on windows client PCs.
Unfortunately these snapshots does not show up there...

Samba drops following error an access log file:

[INDENT][2013/08/25 19:25:08.425644,  0] modules/vfs_shadow_copy2.c:1088(shadow_copy2_get_shadow_copy_data)
  shadow:snapdir not found for /data/share/Public in get_shadow_copy_data
[2013/08/25 19:25:08.425811,  0] smbd/nttrans.c:2286(smb_fsctl)
  FSCTL_GET_SHADOW_COPY_DATA: connectpath /data/share/Public, failed.[/INDENT]

Mentioned snapshots are in place:

[INDENT]root@ubox:~# btrfs su list /data
ID 7903 gen 13960 top level 5 path share
ID 8267 gen 13958 top level 5 path .share/@GMT-2013.08.25-17.38.39
ID 8268 gen 13959 top level 5 path .share/@GMT-2013.08.25-17.38.44
ID 8269 gen 13960 top level 5 path .share/@GMT-2013.08.25-17.38.47
...
root@ubox:~# ls -l /data/share/
total 0
drwxrwxrwx 1 root root  386 Aug 23 08:11 Public
root@ubox:~# ls -l /data/.share/@GMT-2013.08.25-17.38.39/
total 0
drwxrwxrwx 1 root root  386 Aug 23 08:11 Public
...
root@ubox:~# uname -a
Linux ubox 3.8.0-29-generic #42-Ubuntu SMP Tue Aug 13 19:40:39 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux
...
root@ubox:~# smbclient --version
Version 3.6.9[/INDENT]

Samba config looks ok to me:

[INDENT][global]
    log file = /var/log/samba/log.%m
    passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
    obey pam restrictions = yes
    map to guest = bad user
    encrypt passwords = true
    passwd program = /usr/bin/passwd %u
    passdb backend = tdbsam
    dns proxy = no
    netbios name = ubox
    server string = %h server (Samba, Ubuntu)
    unix password sync = yes
    workgroup = HOME
    os level = 20
    create mode = 777
    syslog = 0
    usershare allow guests = yes
    panic action = /usr/share/samba/panic-action %d
    max log size = 1000
    directory mode = 777
    pam password change = yes
    unix extensions = no

[Public]
    path = /data/share/Public
    vfs objects = shadow_copy2
    shadow:snapdir = /data/.share
    shadow:basedir = /data/share
    shadow:sort = desc
    follow symlinks = yes
    wide links = yes
    valid users = ubox
    writeable = yes
    write list = ubox[/INDENT]

What can be a reason for such misbehavior?
According to the failure message samba cant find **shadow:snapdir** parameter for **'Public'** share which is present in config...

[INDENT][2013/08/25 19:25:08.425644,  0] modules/vfs_shadow_copy2.c:1088(shadow_copy2_get_shadow_copy_data)
  _shadow:snapdir_ not found for _/data/share/Public_ in get_shadow_copy_data
[2013/08/25 19:25:08.425811,  0] smbd/nttrans.c:2286(smb_fsctl)
  FSCTL_GET_SHADOW_COPY_DATA: connectpath /data/share/Public, failed.[/INDENT]

How this can be fixed?
Thanks in advance!

---

### Post by andriy-golovnya on 2013-08-28
Answer is found!
Somehow **shadow:snapdir** works only as a relative path from **shadow:basedir**.

shadow:snapdir = _../.share_
shadow:basedir = /data/share

Probably it's a bug in samba 3.6.9...

---

