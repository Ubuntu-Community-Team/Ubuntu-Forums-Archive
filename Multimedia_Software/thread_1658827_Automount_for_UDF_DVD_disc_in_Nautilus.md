---
title: "Automount for UDF DVD disc in Nautilus"
date: 2011-01-03
forum: Multimedia Software
---

### Post by RomanIvanov on 2011-01-03
Ubuntu 10.04, 10.10.
When you insert DVD with UDF file system, Nautilus is failed to mount it and show its content.

Bugs: [https://bugs.edge.launchpad.net/ubuntu/+source/linux/+bug/635499](https://bugs.edge.launchpad.net/ubuntu/+source/linux/+bug/635499)
[https://bugs.launchpad.net/ubuntu/+source/util-linux/+bug/10550](https://bugs.launchpad.net/ubuntu/+source/util-linux/+bug/10550)

Workaround:
to support UDF and ISO in the same time, and auto mount in Nautilus:

```
sudo mkdir /media/cdrom0
```
```
sudo gedit /etc/fstab
```

add to the end of file:
```
/dev/scd0 /media/cdrom0 udf,iso9660 users,noauto,uid=0,gid=46,mode=0777,dmode=0777,nosuid,noexec 0 0

```

Restart PC or 
```
mount /dev/scd0
```

---

### Post by ghostborg on 2011-04-06
Thanks, Worked for me.
I just had to change my mount device to sr0.

---

### Post by SavvasKatseas on 2011-11-28
Worked for me too. Thanks a lot for the advice :)

---

### Post by michaell4 on 2012-03-16
Worked perfectly!

Thanks for your help!

:guitar:

---

