---
title: "Audacious can't open my second drive"
date: 2024-11-03
forum: Multimedia Software
---

### Post by peyre on 2024-11-03
On my desktop, I have an SSD for the system drive and an HDD for bulk storage, including my Music folder.  I just did a clean install of Xubuntu 22.04.1 and modified fstab to mount the HDD (labeled Storage) automatically.  However, it doesn't appear in Places and Audacious can't browse it.  It says **Could not read the contents of Storage** Error opening directory '/mnt/Storage': Permission denied.

I made myself the owner of /mnt but that doesn't help.  I read somewhere that this can be fixed by mounting the drive in /media instead, but that didn't help, even after I made myself the owner of that too.  Anyone know how to fix this?  I want to be play some tunes on my main system!

```
drwxr-xr-x   6 peyre root       4096 Nov  3 07:31 media
drwxr-xr-x   4 peyre root       4096 Nov  2 12:31 mnt
```

For reference, here's my fstab:

```
UUID=7be391dc-8c99-41f9-b846-d2da61196ccc /               ext4    errors=remount-ro 0       1
# / was on /dev/sda2 during curtin installation
/dev/disk/by-uuid/7be391dc-8c99-41f9-b846-d2da61196ccc / ext4 defaults 0 1
# /boot/efi was on /dev/sda1 during installation
#/dev/disk/by-uuid/4287-16F9 /boot/efi vfat defaults 0 1
/dev/disk/by-path/pci-0000:00:1f.1-ata-1.1 /media/pci-0000:00:1f.1-ata-1.1 auto nosuid,nodev,user,sync,nofail,noauto,x-gvfs-show 0 0
/swap.img	none	swap	sw	0	0
/dev/fd0 /media/floppy0 auto rw,user,sync,noauto,exec,umask=0,utf8 0 0
LABEL=Storage /media/Storage auto nosuid,nodev,nofail,x-gvfs-show 0 0
/dev/disk/by-id/usb-TEAC_TEAC_FD-05PUB /mnt/usb-TEAC_TEAC_FD-05PUB auto user,nosuid,nodev,nofail,sync,noauto,x-gvfs-show,rw 0 0
```

I also deleted ~/Music and created a symlink to /media/Storage/Music.  In Thunar, double-clicking on Music in my home folder opens /media/Storage/Music and I can see all my music folders.  But Audacious refuses to open them symlink too.

Edit: Ok, I got Storage to appear in Places by creating a shortcut to it under Places in the lefthand pane of Thunar.  But Audacious remains stubborn.

---

### Post by peyre on 2024-11-03
**Fixed it!**  I had installed this in the App Center from the Snap repository.

A few minutes ago it occurred to me to uninstall it, and install Audacious from the Debian repository instead.  Now I'm having no problems pulling up my other drive.  There must be something wrong with the program in the Snap repository.

---

### Post by ajgreeny on 2024-11-03
Why did you install audacious from the Debian repos?
It is still in the Ubuntu repos and can be installed with the **sudo apt install audacious** command which is how I did it.

---

