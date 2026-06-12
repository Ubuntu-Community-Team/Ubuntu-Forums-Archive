---
title: "Problems ejecting my iPod"
date: 2009-01-23
forum: Multimedia Software
---

### Post by danduq on 2009-01-23
Hi,

I'm trying to get Amarok to eject my iPod using gnome-eject. I've tried it form a command line and if I specify the mount point it fails, although it is shown in df;
```
:~$ gnome-eject -t -v -d /media/ipod
gnome-mount 0.8
** Message: Given device '/media/ipod' is not a volume or a drive.

```

If I specify the device it's OK;
```
:~$ gnome-eject -t -v -d /dev/sdb1
gnome-mount 0.8
** (gnome-eject:20889): DEBUG: Ejecting /org/freedesktop/Hal/devices/volume_uuid_3141_5926
** (gnome-eject:20889): DEBUG: Setting up 750ms timer for Flushing Cache dialog
** (gnome-eject:20889): DEBUG: in unmount_done : user_data = 0x0
Ejected /dev/sdb1
```

Can I get it to work with the mount point? The man page says "don’t include /media as this is automatically appended by the mechanism used to mount"

Should I even be doing that? Or should I just put /dev/sdb1 in?

Thanks.

---

### Post by danduq on 2009-05-07
This can be deleted. I realised I should be using -p instead of -d.

---

