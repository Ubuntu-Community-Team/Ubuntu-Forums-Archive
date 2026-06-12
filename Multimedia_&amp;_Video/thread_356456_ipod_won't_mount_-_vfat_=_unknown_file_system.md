---
title: "ipod won't mount - vfat = unknown file system?"
date: 2007-02-08
forum: Multimedia &amp; Video
---

### Post by mb26 on 2007-02-08
My ipod won't mount. it comes up as 'Apple ipod music player' in places>computer, but clicking on it gives;
"unable to mount the selected volume"
[details]
mount: unknown filesystem type 'vfat'
error: could not delete mount point: no such file or directory
error: could not execute pmount

i have also tried doing it 'manually'
sudo mount -t vfat /dev/sdc2 /media/ipod

gives

mount: unknown filesystem type 'vfat'

help? please.

---

### Post by mb26 on 2007-02-09
just to add to this; its not just an ipod issue.
no usb hdd will mount.
and its not just vfat, ntfs aswell.
i *can* mount a DVD however.

FYI this is my fstab;
```
#  /etc/fstab: static file system information.
# file system mount point type options dump pass
LABEL=/ / ext3 defaults 0 0
LABEL=/boot /boot  ext2 defaults 0 2
LABEL=SWAP SWAP swap sw 0 0
proc /proc proc defaults 0 0
sys /sys sysfs defaults 0 0
/dev/cdrom /mnt/cdrom iso9660 noauto,ro,user,exec 0 0
###### /etc/fstab done
```

PLEASE HELP!!

[edit: if this could be moved somewhere more appropriate then that would be great! doesn't seem like the right place now.]

---

### Post by nitu14 on 2007-02-13
Hi, I have the same problem, I have installaded all these packages from:

[http://gamesplace.info/opensource/ubuntu/hal/ipod-nano-fix/](http://gamesplace.info/opensource/ubuntu/hal/ipod-nano-fix/)

follow the instructions.

Now I can see the Ipod icon on my Desktop.

Thanks martin.

---

