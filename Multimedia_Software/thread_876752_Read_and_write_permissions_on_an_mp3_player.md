---
title: "Read and write permissions on an mp3 player"
date: 2008-08-01
forum: Multimedia Software
---

### Post by commbba on 2008-08-01
Hello , I bought an mp3 player ,Crypto UM-360 4GB ,and loaded with songs normally by drag and drop , but also by Rythmbox music player.Now the problem is that I can't delete some songs from the player.I've created folders and arranged them by the genre ,but it says that the file is a read only file.
I logged in as root but the problem still exists.I've tried to create an insertion by editing fstab , there's no entry for this disk in fstab ,adding the following:UUID=B8F2-7D6A /media/disk vfat uid=1000 gid=1000,rw,force,noauto,locale=el_GR.utf8 00 but the system recognised it as an unmount volume with no privileges and cannot mount it also as root.
Does anyone has an idea for solution ?:lolflag::lolflag::lolflag:

---

### Post by vanadium on 2008-08-01
Remove that line from your /etc/fstab and then reboot your system. With the device plugged in, run following commands and post the output here:

```

sudo fdisk -l
mount

```

This will just show how the device is recognized and mounted, and allow to have a hint of what could be wrong. My first guess is that it is a fat formatted device and that there is an inconsistency with the fat file system, which can be corrected by checking the file system.

---

### Post by commbba on 2008-08-01
The line that concerns this device is:
/dev/sdc on /media/disk-1 type vfat (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=1000,utf8,umask=077,flush)
The edited line in fstab  i've already deleted as I saw that things were getting  worst than better.
Probably is the type of file system that the device uses and don't work nice with Ubuntu , but (I forgot write it before) , the device has an option to delete a song through the device's menu and neither I can do that.

---

### Post by vanadium on 2008-08-01
File system is vfat (fat32) and Linux can work perfecty with that. I guess that inconsistencies in the file system are causing the issues. You need to check and repair the file system.

---

### Post by commbba on 2008-08-02
Sorry but now I saw the difference.It says ''read only filesystem '' and not ''read only file'' , so something is happening with the vfat filesystem.
Do you have any idea how I can check and repair it?
I google it and installed Testdisk by Synaptic but I can't launch it as there isn't any icon in the menu , and writing ''testdisk'' in run programm application neither do something.

---

### Post by vanadium on 2008-08-02
The command "dosfsck" is the counterpart of ms Windows' "chkdsk" for checking and optionally repairing fat volumes.

---

