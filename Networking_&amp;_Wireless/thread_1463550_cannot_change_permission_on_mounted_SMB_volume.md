---
title: "cannot change permission on mounted SMB volume"
date: 2010-04-27
forum: Networking &amp; Wireless
---

### Post by serge_k on 2010-04-27
Hi guys,
I am trying to mount Samba share with following command
```
mount.cifs //192.168.0.3/shmelevsky /mnt/tmp/ -o user=shmelevsky,uid=1000,gid=1000
```it works fine, I could create/edit files and folders, bu I could not change permission for them:
```

root@darkstar:/mnt# chmod 700 tmp/www/
chmod: changing permissions of `tmp/www/': Permission denied
root@darkstar:/mnt#

```Does anyone knows about such problem?

---

### Post by serge_k on 2010-04-28
up

---

### Post by redmk2 on 2010-04-28
> **serge_k said:**
> Hi guys,
I am trying to mount Samba share with following command
```
mount.cifs //192.168.0.3/shmelevsky /mnt/tmp/ -o user=shmelevsky,uid=1000,gid=1000
```it works fine, I could create/edit files and folders, bu I could not change permission for them:
```

root@darkstar:/mnt# chmod 700 tmp/www/
chmod: changing permissions of `tmp/www/': Permission denied
root@darkstar:/mnt#

```Does anyone knows about such problem?

Try the command as root.  Use ```
sudo chmod 700 tmp/www/
```

---

### Post by serge_k on 2010-04-28
[B]redmk2
[/B]all commands (mount and chmod) I did with root privileges :(

---

### Post by redmk2 on 2010-04-28
> **serge_k said:**
> [B]redmk2
[/B]all commands (mount and chmod) I did with root privileges :(

Is this a NTFS volume?

---

### Post by serge_k on 2010-05-01
no, volume is EXT3

---

### Post by redmk2 on 2010-05-01
> **serge_k said:**
> no, volume is EXT3

Hmmmm...  I can't really point to anything specific other than you use of "*mount.cifs*" in the command rather than "*mount -t cifs*".  I have always been under the impression that this is the correct form of the mount command when using cifs:```
mount -t cifs //server/share mount_point [-o options ]
```

A good description of CIFS mounts can be found [**_here_**]("http://book.opensourceproject.org.cn/sysadmin/samba/sambao3rd/opensource/0596007698/samba3-chp-11-sect-1.html").

---

