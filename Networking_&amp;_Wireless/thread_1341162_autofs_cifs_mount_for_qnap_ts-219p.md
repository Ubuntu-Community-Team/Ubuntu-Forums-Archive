---
title: "autofs cifs mount for qnap ts-219p"
date: 2009-11-29
forum: Networking &amp; Wireless
---

### Post by kja999 on 2009-11-29
Hi,

I am struggling to work out where I am going wrong with an autofs mount to my nas.

The nas is called bigdisk (hosts file maps the ip, so no resolution issues), and for simplicity sake, would like to map to the Public share.

Functionally everything seems ok, I.e autofs trys to map the drive, it just fails

/etc/auto.master has this:
/mnt/bigdisk /etc/auto.bigdisk --timeout=60

/etc/auto.bigdisk is this:
Public     -fstype=cifs,username=xxxxxxxx,password=xxxxxxx,file_mode=0644,iocharset=utf8,dir_mode=0755   bigdisk://Public/

After an autofs restart, doing a ls /mnt/bigdisk/Public gives this error in syslog:

Nov 29 18:00:15 eee kernel: [11922.847520]  CIFS VFS: cifs_mount failed w/return code = -6
Nov 29 18:00:15 eee automount[16624]: mount(generic): failed to mount bigdisk://Public/ (type cifs) on /mnt/bigdisk/Public
Nov 29 18:00:15 eee automount[16624]: failed to mount /mnt/bigdisk/Public


Can anyone spot my error ?

Cheers

---

### Post by kja999 on 2009-11-29
ok, so sometimes, banging your head against a wall will bring the wall down!

problem seemed to be the extra backslash before the word Public:
bigdisk:public/

resulting line is this ....

Public     -fstype=cifs,username=xxxxxx,password=xxxxxx,file_mode=0644,iocharset=utf8,dir_mode=0755   bigdisk:public/

---

