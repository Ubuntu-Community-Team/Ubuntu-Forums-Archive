---
title: "Can not mount ipod or use gtkpod"
date: 2010-01-22
forum: Multimedia Software
---

### Post by Nbala on 2010-01-22
I am using 9.10 Karmic Koala Oct 2009 release.
 Gtkpod does not show my ipod touch, and I can not mount the ipod.
 I realise there were problems with the ipod touch syncing/mounting but gtkpod has the touch option, and I have all the files from synaptic for using an ipod touch.
 

 When I run gtkpod its just blank, no music files show up.
 If I click load ipod I get the error:
 

 “Ipod Directory Structure not found”
 Could not find iPod directory structure at '/dev/sdc2'. 
 If you are sure that the iPod is properly mounted at '/dev/sdc2', it may not be initialized for use. In this case, gtkpod can initialize it for you. 
 Do you want to create the directory structure now?
 Then I choose ipod model and mount point and get the msg:
 Error initializing ipod: problem creating iPod directory or file: 'dev/sdc2'
 

 ALSO there is an secondary static ipod icon in file browser but if I try to mount or use it I get:
 Unable to mount location  
 Mount: special device /dev/sdc2 does not exist
 [this is probably from when I tried to manually mount it in the beginning – now I cant get rid of it, any advice on that would also help]
 

 Ive tried gtkpod from sudo, Ive also tried other apps, and all the packages supposed to enable USB connections for this very purpose etc.
 

 

 FSTAB:
 # /etc/fstab: static file system information. 
 # 
 # Use 'blkid -o value -s UUID' to print the universally unique identifier 
 # for a device; this may be used with UUID= as a more robust way to name 
 # devices that works even if disks are added and removed. See fstab(5). 
 # 
 # <file system> <mount point>   <type>  <options>       <dump>  <pass> 
 proc            /proc           proc    defaults        0       0 
 # / was on /dev/sda1 during installation 
 UUID=b9d57231-8a16-40f3-af45-edece8976ea7 /               ext4    errors=remount-ro 0       1 
 # swap was on /dev/sda5 during installation 
 UUID=a435018d-13d8-48f0-83c9-dedb5f5ee58e none            swap    sw              0       0 
 /dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0 
 /dev/sdc2 /media/iPod vfat nosuid,nodev,rw,umask=077,gid=1000,uid=1000,user,defaults,noatime,iocharset=utf8 0 0
 [ yes I removed noauto on the advice of a netizen ]  
 

 MTAB:
 /dev/sda1 / ext4 rw,errors=remount-ro 0 0 
 proc /proc proc rw 0 0 
 none /sys sysfs rw,noexec,nosuid,nodev 0 0 
 none /sys/fs/fuse/connections fusectl rw 0 0 
 none /sys/kernel/debug debugfs rw 0 0 
 none /sys/kernel/security securityfs rw 0 0 
 udev /dev tmpfs rw,mode=0755 0 0 
 none /dev/pts devpts rw,noexec,nosuid,gid=5,mode=0620 0 0 
 none /dev/shm tmpfs rw,nosuid,nodev 0 0 
 none /var/run tmpfs rw,nosuid,mode=0755 0 0 
 none /var/lock tmpfs rw,noexec,nosuid,nodev 0 0 
 none /lib/init/rw tmpfs rw,nosuid,mode=0755 0 0 
 binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw,noexec,nosuid,nodev 0 0 
 gvfs-fuse-daemon /home/ablanathanalba/.gvfs fuse.gvfs-fuse-daemon rw,nosuid,nodev,user=ablanathanalba 0 0 
 /dev/sr0 /media/cdrom0 iso9660 ro,nosuid,nodev,utf8,user=ablanathanalba 0 0
  
 When I run gtkpod from terminal with sudo I receive:
 (gtkpod:31159): Gtk-WARNING **: gtk_menu_attach_to_widget(): menu already attached to GtkImageMenuItem 
 (gtkpod:31159): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated 
 

 -seems like graphical errors (from a theme) and unrelated but thought I'd mention it
 

 I really want to update my ipod Im using music from 2 years ago, any ideas greatly appreciated! :)

---

### Post by Amzo2 on 2010-02-13
Yeah I had the same problem, but when I mounted the ipod else where, like /mnt/, it worked like a charm. Hope this helps

---

### Post by ootawata on 2010-05-30
> **Amzo2 said:**
> Yeah I had the same problem, but when I mounted the ipod else where, like /mnt/, it worked like a charm. Hope this helps

Thank you, this does help.  I use Arch, and in their wiki I remember seeing them say something like "mount to ~/ipod".  An Ubuntu guide said "mount to /media/ipod" or "/mnt/ipod".  Anyway, I've noticed that, due to privileges, gtkpod could not connect to the mount point.  For example, even "ls" couldn't read it without being super user:
```
/media$ ls
ls: cannot access ipod: Permission denied
cd/  disk/  dvd/  fl/  ipod/

```
which I found strange.  So the solution is to do this (assuming ~/ipod isn't made yet):
```
$ mkdir ~/ipod
$ sudo ifuse ~/ipod
```
if you have gtkpod already running, it'll detect it, which I thought was neat.

---

