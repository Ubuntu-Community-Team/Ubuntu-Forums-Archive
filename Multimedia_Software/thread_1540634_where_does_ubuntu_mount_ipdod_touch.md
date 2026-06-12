---
title: "where does ubuntu mount ipdod touch?"
date: 2010-07-28
forum: Multimedia Software
---

### Post by confused_user on 2010-07-28
I got a new ipod touch the other day and have been unable to get anything to read it properly.

it automounts just fine and i can browse the file system.  Normally with my old ipod i just used gtkpod and it worked fine.

With gtkpod you have to tell it where the ipod is mounted.

The problem is that i cannot see where the ipod touch is mounted

It is connected right now and i can see it in nautilus and i can browse the file system, however...

```
matt@matt-netbook:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda7              11G  3.6G  6.0G  38% /
none                  999M  304K  998M   1% /dev
none                 1003M  324K 1002M   1% /dev/shm
none                 1003M  220K 1002M   1% /var/run
none                 1003M     0 1003M   0% /var/lock
none                 1003M     0 1003M   0% /lib/init/rw
/dev/sda6              98G   84G  9.5G  90% /home
/dev/sda5              38G   29G  9.1G  76% /media/84E8FC48E8FC3A4E

```

```
matt@matt-netbook:~$ cat /etc/mt
mtab           mtab.fuselock  mtools.conf    
matt@matt-netbook:~$ cat /etc/mtab
/dev/sda7 / ext3 rw,errors=remount-ro 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
none /sys sysfs rw,noexec,nosuid,nodev 0 0
none /sys/fs/fuse/connections fusectl rw 0 0
none /sys/kernel/debug debugfs rw 0 0
none /sys/kernel/security securityfs rw 0 0
none /dev devtmpfs rw,mode=0755 0 0
none /dev/pts devpts rw,noexec,nosuid,gid=5,mode=0620 0 0
none /dev/shm tmpfs rw,nosuid,nodev 0 0
none /var/run tmpfs rw,nosuid,mode=0755 0 0
none /var/lock tmpfs rw,noexec,nosuid,nodev 0 0
none /lib/init/rw tmpfs rw,nosuid,mode=0755 0 0
/dev/sda6 /home ext3 rw 0 0
gvfs-fuse-daemon /home/matt/.gvfs fuse.gvfs-fuse-daemon rw,nosuid,nodev,user=matt 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw,noexec,nosuid,nodev 0 0
/dev/sda5 /media/84E8FC48E8FC3A4E fuseblk rw,nosuid,nodev,allow_other,blksize=4096,default_permissions 0 0

```

```
matt@matt-netbook:~$ sudo fdisk -l
[sudo] password for matt: 

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x531d0b5b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         129     1035168+  82  Linux swap / Solaris
/dev/sda2   *         130         249      963900    7  HPFS/NTFS
/dev/sda4             250       19457   154287457+   5  Extended
/dev/sda5            1588        6471    39230730    7  HPFS/NTFS
/dev/sda6            6472       19457   104310013+  83  Linux
/dev/sda7             250        1587    10740736   83  Linux

Partition table entries are not in disk order

```

what the...?

anyone know where it is?

---

### Post by Chronon on 2010-07-28
The iPod Touch does not have an MSC interface.  Thus it does not expose a file system to the host: The file system of the iPod Touch does not actually get mounted to a directory on your system.  The iPod Touch uses some other protocol to handle file transfers and to provide a description of accessible media.

---

### Post by confused_user on 2010-07-28
right ok, so when gtkpod asks where it is mounted what should i say?

---

### Post by Chronon on 2010-07-28
From the gtkpod website:
> **What is gtkpod?**

gtkpod is a platform independent Graphical User Interface for Apple's iPod using GTK2. It supports the first to fifth Generation including the iPod mini, iPod Photo, iPod Shuffle, iPod nano, and iPod Video..

The latest stable version is V0.99.14, released on January 18th 2009. Click here for details.

[B]What is libgpod?
[/B]
libgpod is a shared library to access the contents of an iPod. You are welcome to use this library in your own projects.

The latest stable version is V0.7.2, released on April 15th, 2009.

V0.6.0 was the first release to support the iPod Classic and Nano Video. These models require a one-time setup of the iPod however, see the libgpod page for more details.

There's also preliminary support for the iPhone and the iPod Touch but they must be jailbroken to work. You'll find more details in the NEWS file.

It sounds like gtkpod doesn't support the iPod Touch.  However, try the community documentation page here:
[https://help.ubuntu.com/community/PortableDevices/iPhone](https://help.ubuntu.com/community/PortableDevices/iPhone)

It gives advice on using the iPod Touch in Ubuntu.

---

### Post by confused_user on 2010-07-28
i cant get it to read on rythmbox but thats about it, cant write to it, rythmbox just crashes.

oh well, guess i need to keep windows on dual boot after all

---

### Post by confused_user on 2010-08-03
ok by sheer chance i was doing an rsync backup of my /home and noticed that it was a lot larger than it usually is.

My ipod touch was connected at the time and whilst backing up /home i also backed up the ipod touch.

So a little digging reveals that the ipod touch 4g get's mounted here

~/.gvfs/matt’s iPod Touch

Now that i know where to tell gtkpod where it is mounted i am able to manage the ipod touch , add playlists and music + video

also the filesystem is writable, i can put files on it no problem.

---

