---
title: "Hard Disk sharing problem UBUNTU 9.1"
date: 2009-11-05
forum: Networking &amp; Wireless
---

### Post by field3d on 2009-11-05
Hello i hope someone can help me i have a trouble on my ubuntu i have 2 dirs for sharing. One directory is on the boot hard disk where is installed UBUNTU, i made a share and works perfect accesing trough Windows XP machines now i bought a second hard disk i made a format on linux file system and i made on that new hard disk the second directory i want to share but after made the sharing options the Windows XP machines can see the directory but if i click tell me i have not permissions to acess the directory anyone know how can i solve this. Time ago see on a forum (i don't remember where) a similar thing and the guy solved adding the second new hard disk to the the system but really don't know what to do. Can someone can help me? 
Note when i made the sharing options i used the check GUEST to avoid passwords prompts on the dir. But like said the only one is working is the dir running on the boot disk of UBUNTU.
with command mount i have this:

/dev/sda1 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
none on /proc/bus/usb type usbfs (rw,devgid=46,devmode=664)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/server/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=server)
/dev/sdb1 on /media/UBUNTU2 type ext4 (rw,nosuid,nodev,uhelper=devkit)

where sdb1 is the drive i can't put dirs to share.

And with the command: sudo fdisk -l i have this:

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x20fb20fa

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       13995   112414806   83  Linux
/dev/sda2           13996       14593     4803435    5  Extended
/dev/sda5           13996       14593     4803403+  82  Linux swap / Solaris

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00029563

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        9729    78148161   83  Linux

Note: Each time i login UBUNTU 9.1 when i try to browse my secondary hard disk request me password from my login account, after give the password can see dirs and never request me password again until turn off the machine again. Something similar when you access via Terminal and a command requires password.



Thank you

---

### Post by field3d on 2009-11-06
I solved the access with this command sudo adduser mymainuser grouponallmynetworkXP
But the thing is now i can't automount the harddisk because each time i turn off and turn on the machine i need to access the hard disk and give the password of my main user, once the correct password is given the hard disk appear on the the desktop and is when i can access via network. How can i then automount to avoid call the hard disjs and give the password each time i login the computer?
Thank you

---

