---
title: "W800i mount automatically"
date: 2008-05-18
forum: Multimedia Software
---

### Post by co0lingFir3 on 2008-05-18
Hi folks!
If i plug in my Sony Ericsson W800i phone it is NOT mounted, although it is shown in the "Computer" location. If i doubleclick on the icon there, it says "Impossible mounting this point. File was not able to mount." (translated). I managed to mount it though via terminal with the command ```
sudo mount /dev/sdh1 -t vfat /media/w800i
```
So there has to be a way to mount my favourite phone automatically. Maybe via fstab? But then i need to assign a label to the phone or a UUID and dunno how to do that with fat filesystem?

Thx for your help in advance!
co0lingFir3

---

### Post by muranyia on 2010-02-25
Put this into your /etc/fstab (on a single line, match uid and gid with yours, type 'id' to see them) :
```
# W800i
obexfs#-u0	/media/W800i	fuse	noauto,users,fsname=obexfs#-u0,uid=1000,gid=1000	0	0 
```

This goes to /lib/udev/rules.d/45-fuse.rules :

```
# SonyEricsson W800i
ATTR{idVendor}=="0fce", ATTR{idProduct}=="d028", MODE="660", GROUP="audio", RUN+="/usr/bin/sudo -u yourusername /bin/mount obexfs#-u0
```

This will automount the internal memory. Needs openobex and obexfs.

I haven't tested yet this method for the card. You are supposed to use this fstab entry and modify the mountpoint above from obexfs to /media/MemoryStick, or simply add another RUN+= :

```
Label="Sony Eri Memory Stick"	/media/MemoryStick	vfat	noauto,users,uid=1000,gid=1000,sync	0	0
```

---

