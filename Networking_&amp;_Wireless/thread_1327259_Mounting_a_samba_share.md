---
title: "Mounting a samba share"
date: 2009-11-15
forum: Networking &amp; Wireless
---

### Post by Urob on 2009-11-15
sudo mount -t cifs -o password= //192.168.0.100/backups/ /home/rob/Bureaublad/tc

This command that i found in some forum does indeed mount the folder 'backups' onto my 'tc' folder.
In 'tc' i have access to subfolders A, B, C, D as expected.
On opening one of the subfolders they show empty, but i know they are not.

---

### Post by dmizer on 2009-11-15
Please see the 2nd link in my sig.

---

### Post by Urob on 2009-11-15
sudo mount -t cifs //iomega-09c8e3/backups/ /media/tc -o guest,rw,iocharset=utf8,file_mode=0777,dir_mode=0777

Same result :-(

In fact i try to access a NAS (Iomega home media server)

Mounting succeeds, i even can create folders/files in the share, but the subfolders show empty while they are not.

---

### Post by dmizer on 2009-11-15
Be sure to look at the troubleshooting section. Particularly the sections which read: Files owned by root / "The folder contents could not be displayed"

---

### Post by Urob on 2009-11-15
cat /etc/passwd | grep did output 1000 for gid and uid.

Here my fstab file:

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdb5 during installation
UUID=5e86c805-2582-450e-9920-d121a68f1b03 /               ext4    relatime,errors=remount-ro 0       1
# /home was on /dev/sdb7 during installation
UUID=5d48f17b-efd6-4b42-ac19-0b3cb47c4336 /home           ext4    relatime        0       2
# swap was on /dev/sdb6 during installation
UUID=352b4a4a-8a45-416c-b3c0-09ef483f259c none            swap    sw              0       0
# swap was on /dev/sdc2 during installation
UUID=208eaf45-7e97-485f-8249-4f1f8ba13b74 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
#
//iomega-09c8e3/backups/    /media/tc        cifs    credentials=/root/.smbcredentials,iocharset=utf8,noserverino,gid=1000,uid=1000,nounix,file_mode=0777,dir_mode=0777 0 0

---

### Post by dmizer on 2009-11-15
Please provide the make and model of your NAS device.

---

### Post by Urob on 2009-11-15
Ok

Got it working, Dunno why it works now and not before.
I think all i changed in meantime is fstab

//iomega-09c8e3/backups/    /media/tc       cifs    guest,rw,iocharset=utf8,noserverino,gid=1000,uid=1000,nounix,file_mode=0777,dir_mode=0777 0 0
//iomega-09c8e3/roby/    /media/tc2       cifs    guest,rw,iocharset=utf8,noserverino,gid=1000,uid=1000,nounix,file_mode=0777,dir_mode=0777 0 0

 TYVM.

Only issue remaining: 

When shutting down, now ubuntu 9.04 switches to text console and displays:

CIFS VFS: server not responding
CIFS VFS: No response for cmd 50 & 51

Hangs for 1 minute, then shuts down finally

---

### Post by dmizer on 2009-11-15
> **Urob said:**
> When shutting down, now ubuntu 9.04 switches to text console and displays:

CIFS VFS: server not responding
CIFS VFS: No response for cmd 50 & 51

Hangs for 1 minute, then shuts down finally

There is also a fix for this in the troubleshooting section :)

---

### Post by Urob on 2009-11-15
dmizer your guides are great !

In fact I had 2 problems linked to this samba share and nearly had given up:

1. i could not backup my data to the NAS 
   (using luckybackup software)
2. i could not access truecrypt containers on the NAS

Both are solved now, thx to your helping hand :-)

PS: and shutdown working fine too now :-)

---

