---
title: "Sharing external HDD"
date: 2009-02-08
forum: Networking &amp; Wireless
---

### Post by detroit/zero on 2009-02-08
I have two laptops, both running Hardy. File & printer sharing works without a hitch, except for an external USB HDD.

The disk is formatted FAT32. On whichever computer it is attached to, it will show up in the list of shared files/folders available on that computer, but when trying to access it, the person attempting to access it is prompted for a password that doesn't correspond to the user/sudo password for either user of either computer.

Confused? Me too. To illustrate:

User1----Laptop1
User2----Laptop2
              |___Disk

When the drive is plugged into Laptop2 and User1 tries to access it via network shares, User1 is prompted for a password that doesn't correspond to User1's account on Laptop2, or User2's account on Laptop2.

As "administrator" of both computers, I know what both passwords are and have root/su access on both machines. I have no problems using ssh to do anything I want on either laptop from either laptop.

In trying to change sharing options for the disk, in a Root Nautilus window, I'm told I don't have proper permissions to alter/change sharing abilities. I also don't have proper permissions to alter/change permissions of the files on the disk, even though (from my understanding) FAT32 doesn't really have permissions in the same sense as NTFS or EXTx does.

It's been a long day and maybe I'm over-analyzing this one. Can somebody tell me how to share an external USB HDD formatted as a FAT32 FS?

---

### Post by detroit/zero on 2009-02-10
Bump.

---

### Post by detroit/zero on 2009-02-11
3 day bump.

---

### Post by Gramps on 2009-02-11
Okay if I understand this right you have the external hd mounted on Laptop 1 and you are trying to access it from Laptop 2.

Can you read/write to the drive on the LT that the drive is mounted on?

Posting the output from the mount command on the LT with the FAT32 drive mounted might help too.

This may also give you some ideas as to the problem [http://skillfulness.blogspot.com/2008/11/working-with-fat32-in-ubuntu-linux.html](http://skillfulness.blogspot.com/2008/11/working-with-fat32-in-ubuntu-linux.html)

This may also help [http://skillfulness.blogspot.com/2008/11/creating-home-web-and-file-server-with.html](http://skillfulness.blogspot.com/2008/11/creating-home-web-and-file-server-with.html)

---

### Post by detroit/zero on 2009-02-12
That's half correct. The problem is exactly the same no matter which laptop the drive is mounted on. I assume a solution to the problem on one laptop running Hardy will allow me to fix the problem on both...

To answer your question: Yes - whichever laptop the drive is on has full read/write access to the user signed into that computer. If, for example, the drive is mounted to Laptop2 and I SSH into Laptop2 as User1, I still have full read/write access.

Here's the output of the *mount* command with the drive attached:```
zero@zero-laptop:~$ mount
/dev/sda6 on / type ext3 (rw,relatime,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.24-23-generic/volatile type tmpfs (rw)
/dev/sda7 on /home type ext3 (rw,relatime)
none on /proc/bus/usb type usbfs (rw,devgid=46,devmode=666)
securityfs on /sys/kernel/security type securityfs (rw)
rpc_pipefs on /var/lib/nfs/rpc_pipefs type rpc_pipefs (rw)
nfsd on /proc/fs/nfsd type nfsd (rw)
gvfs-fuse-daemon on /home/zero/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=zero)
/dev/scd0 on /media/cdrom0 type iso9660 (ro,nosuid,nodev,utf8,user=zero)
** /dev/sdb1 on /media/disk type vfat (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=1000,utf8,umask=077,flush)**

```I see the uid is set at 1000, but the umask is 077. I would think that would enable sharing, especially after selecting the option in a root nautilus window.

I don't have the disk added to fstab; I just let it automount when it gets plugged in, and those are the settings it gets.

As an aside, here's an* ls -la* output inside */media*:```
zero@zero-laptop:~$ cd /media
zero@zero-laptop:/media$ ls -la
total 30
drwxr-xr-x  4 root root  4096 2009-02-12 11:15 .
drwxr-xr-x 22 root root  4096 2009-02-05 15:29 ..
lrwxrwxrwx  1 root root     6 2008-10-24 16:18 cdrom -> cdrom0
dr-xr-xr-x  4 root root  2048 2008-06-18 17:58 cdrom0
**drwx------  5 zero root 16384 1970-01-01 01:00 disk**
-rw-r--r--  1 root root   110 2009-02-12 11:15 .hal-mtab
-rw-------  1 root root     0 2009-02-12 01:35 .hal-mtab-lock
```I see there that I'm the owner, but the group is set to root. Maybe that's the problem? Of course, trying to change it doesn't work:```
zero@zero-laptop:/media$ sudo chown zero:zero disk
chown: changing ownership of `disk': Operation not permitted
```

I'll go check out the links you provide... Thanks for the help!

---

### Post by detroit/zero on 2009-02-12
I'm not sure what happened, but some time between posting that last message and now - without changing or so much as looking at a single setting - I've completely lost all file and printer sharing between my two computers. I can't even see my own shared files on the network.

---

