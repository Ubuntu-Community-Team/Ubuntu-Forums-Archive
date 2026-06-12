---
title: "Access denied creating directories in Samba share"
date: 2010-04-26
forum: Networking &amp; Wireless
---

### Post by almightybunghole on 2010-04-26
Hi folks,

I've got a really weird problem which I'm hoping someone can explain. So here goes...

I have a Mythbuntu box on which I store all of my media. The media directories (all under /var/lib/mythtv) are shared via Samba to other machines in the house. On my Hardy desktop I have /home/me/Music mapped in the fstab to the share, so that it auto mounts when I start the machine.

When I try to copy new directories to the music share, I get access denied, although the folder is created. If I then retry the copy, it works, until another folder needs to be created, whereupon it fails again.

I've tried manually creating folders in ~/Music using nautilus and when the folder is first created, it has a padlock on it and under permissions the owner is set to HPLIP. If I refresh, the owner changes to my username and the padlock disappears. After this the folder is accessible and works as it should.

The line from fstab is as follows:

```
//myth.domain.net/music  /home/me/Music cifs guest,rw,iocharset=utf8,gid=1000,uid=1000,file_mode=0777,dir_mode=0777 0 0
```

And the Samba config looks like this:

```
[global]
workgroup = MSHOME
server string = %h server (Samba, Mythbuntu)
log file = /var/log/samba/log.%m
max log size = 1000
syslog = 0
panic action = /usr/share/samba/panic-action %d
dns proxy = no
security = share
map archive = yes


[music]
comment = Music
path = /var/lib/mythtv/music
public = yes
writable = yes
create mask = 0777
directory mask = 0777
force user = mythtv
force group = mythtv

```

Permissions on the /var/lib/mythtv/music folder Mythbuntu box are all set to 777.

Any input welcomed as I don't really know what to look at next!

Thanks.

---

