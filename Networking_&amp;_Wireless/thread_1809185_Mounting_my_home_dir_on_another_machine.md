---
title: "Mounting my home dir on another machine"
date: 2011-07-21
forum: Networking &amp; Wireless
---

### Post by erezz on 2011-07-21
Hi,

I'm running Kubuntu 11.04 (although I think my question is not Kubuntu related). I want to mount my home dir on another machine and log in to the remote machine with the same username and home dir.

The problem is that the files on the mounted dir belong to userid 99 (nobody). For example:

on the local machine:

```
[erezz@erez-lx:~]$ ls -ln ~/.bashrc 
-rw-r--r-- 1 [COLOR="DeepSkyBlue"]1000[/COLOR] 1000 1644 2011-07-20 13:56 /home/erezz/.bashrc
```

on the remote machine:

```
[erezz@remote_machine:~]$ ls -ln ~/.bashrc 
-rw-r--r-- 1 [COLOR="Red"]99[/COLOR] 99 1644 Jul 20 13:56 /home/erezz/.bashrc
```

Here's what I did (and worked great for me in Kubuntu 10.04):

local machine:

/etc/exports:
```
/home/erezz/     *(rw,insecure,sync,all_squash,anonuid=1000,anongid=1000)
(also tried /home/erezz/     *(rw,insecure,sync,root_squash))
```

local user:
```
[erezz@erez-lx:~]$ id
uid=1000(erezz) gid=1000(erezz) groups=1000(erezz),4(adm),20(dialout),24(cdrom),46(plugdev),113(lpadmin),118(admin),120(sambashare)

```
remote machine:

/etc/fstab:

```
local_machine_ip:/home/erezz /home/erezz nfs bg,hard,intr 0 0
```

I've also created a user with the same name and user id on the remote machine:

```
[erezz@remote_machine:~]$ id
uid=1000(erezz) gid=1000(erezz) groups=1000(erezz)
```

Can anyone help me with this?

Thanks,
Erez

---

### Post by Lampi on 2011-07-21
shouldn't you chown the remote home from nobody:nogroup to erezz:erezz ?

---

### Post by erezz on 2011-07-21
If I do something like this:

```
chown -R erezz erezz/
chgrp -R erezz erezz/

```

and unmount the dir, I see the following:

```
drwxr-xr-x 2 erezz        erezz 4096 May 22 16:27 erezz
```

Now, I re-mount and get the same result:

```
drwxr-xr-x 31 nobody       nobody 4096 Jul 21 16:17 erezz

```

---

### Post by Lampi on 2011-07-21
I had your problem before, googled it - turned up with this solution:

You can change the user id and the group id of an existing user like this:

```

#!/bin/bash
usermod -u 1003 lampi
groupmod -g 1003 lampi
find / -user 1007 -exec chown 1003 {} \;
find / -group 1007 -exec chgrp 1003 {} \;
usermod -g 1003 lampi

```

In my example the user lampi had uid/gid 1007 - I wanted both changed to 1003.

These commands actually do the change, then they browse your system for the old uid/gid using find to change gid/uid of the files. In your case /home on your remote might be enough, I started from root (/)

edit: make sure to run this as root - only root can change uid/gid of another user

---

### Post by erezz on 2011-07-24
It doesn't work. I think that the problem is not that the files belong to user-id 1000 on my machine and to user-id 99 on the remote machine. It's something bad with the mount that shows the files on the remote machine with a bad user & group id.

Both users (on the local and remote machine) have the same user id and group id.

---

### Post by HermanAB on 2011-07-24
As you already figured out, for NFS to work properly, your users must have the same UID and GID on all machines.  So fix that, NFS is working correctly.

---

### Post by erezz on 2011-07-24
See one of my comments above. I have the same username, userid & groupid on both machines:

local machine:

```
[erezz@erez-lx:~]$ id
uid=[COLOR="Magenta"]1000[/COLOR](erezz) gid=[COLOR="DarkOrange"]1000[/COLOR](erezz) groups=1000(erezz),4(adm),20(dialout),24(cdrom),46(plugdev),113(lpadmin),118(admin),120(sambashare)
```

remote machine:

```
[erezz@remote_machine:~]$ id
uid=[COLOR="Magenta"]1000[/COLOR](erezz) gid=[COLOR="DarkOrange"]1000[/COLOR](erezz) groups=1000(erezz)
```

---

### Post by Lampi on 2011-07-27
@erez: looks good, so I it has to be related to your export options or your nfs mount options. Can you try my options? I know they work well with lucid:

```

#/etc/exports for Videos & Music:
/home/lampi/Videos/    192.168.1.0/24(rw,no_root_squash,no_all_squash,async,no_subtree_check)
/home/lampi/Music/    192.168.1.0/24(rw,no_root_squash,no_all_squash,async,no_subtree_check)
```

```
#mount options in /etc/fstab (Server IP is fixed to 192.168.1.2):
192.168.1.2:/home/lampi/Videos/ /home/lampi/share/Videos nfs noauto,user,rw,hard,intr         0      0
192.168.1.2:/home/lampi/Music/ /home/lampi/share/Music nfs noauto,user,rw,hard,intr         0      0
```

now mount the shares like this (-v is for verbose mounting):
```
/sbin/mount.nfs /home/lampi/share/Videos -v
/sbin/mount.nfs /home/lampi/share/Music -v
```

---

### Post by erezz on 2011-07-27
Just found the solution in another thread: [http://www.fedoraforum.org/forum/showthread.php?t=260972&page=2](http://www.fedoraforum.org/forum/showthread.php?t=260972&page=2)

> Edit /etc/idmapd.conf on both client and server.

Near the top in the [General] section I uncommented the line
#Domain = local.domain.edu
and changed it to
Domain=foo.home

Restarted both server and client's rpc.idmapd.


---

### Post by erezz on 2011-07-27
Lampi - thanks a lot for your help!

---

