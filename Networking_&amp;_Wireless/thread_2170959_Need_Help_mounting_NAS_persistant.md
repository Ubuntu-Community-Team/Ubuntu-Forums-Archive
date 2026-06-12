---
title: "Need Help mounting NAS persistant"
date: 2013-08-28
forum: Networking &amp; Wireless
---

### Post by zerogamer100 on 2013-08-28
I have Ubuntu OS 10.04.3 LTS. 
and 
A Raid 5 Buffalo NAS

I am trying to mount the NAS so that I can retain files on it from a certain application (I don't want to use the server to keep the data). How Can I mount this persistently? If it powers down unexpected. I would like the NAS to mount when it automatically comes up)? Is it going to be the FSTAB conf? to help here is the output of my fstab and syslog. Just an FYI, I would like to call the new NAS: /data/bak.
 Bak1 and Bak2 are small USB drives that have filled up.

dataservices@nat-syslog:/etc$ more fstab # /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier # for a device; this may be used with UUID= as a more robust way to name # devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/mapper/nat--syslog-root /               ext4    errors=remount-ro 0       1
# /boot was on /dev/sda1 during installation
UUID=cbde0b39-d12c-4485-b38e-84ac223c1c4b /boot           ext2    defaults        0       2
/dev/mapper/nat--syslog-swap_1 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
/dev/sdb /data ext3 defaults 0 0
dataservices@nat-syslog:/etc$
 
 
dataservices@nat-syslog:/etc$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/mapper/nat--syslog-root
                       32G   32G     0 100% /
none                 1000M  232K 1000M   1% /dev
none                 1005M     0 1005M   0% /dev/shm
none                 1005M   40K 1005M   1% /var/run
none                 1005M     0 1005M   0% /var/lock
none                 1005M     0 1005M   0% /lib/init/rw
/dev/sdb              135G  121G  7.6G  95% /data
/dev/sda1             228M   17M  199M   8% /boot
/dev/sdc              1.8T  1.5T  293G  84% /data/bak1
/dev/sdd              1.8T  1.5T  293G  84% /data/bak2
dataservices@nat-syslog:/etc$


Any help would be greatly appreciated and hopefully I didn't post in the wrong section. Thanks in advance.

Sincerely, 

joseph

---

### Post by tgalati4 on 2013-08-28
I find the easiest way to get the correct switches is to do the following:

Open your file manager (probably Nautilus) and click on Network.  Navigate to your Buffalo NAS.  (It should be powered and booted properly.)  Click on it to open up the root directory of the file share that you want to be available.

```
cat /etc/mtab
cat /etc/fstab
gksudo gedit /etc/fstab
```

You want to cut and past the line in mtab that contains your share into your fstab then reboot.  You will have to delete the first word of the mtab line as that is the application that is using the mount.  It is not needed in fstab.

**mtab** contains a table of what is currently mounted on your linux system.  **[fstab]("https://help.ubuntu.com/community/Fstab")** is a table of file systems that will get loaded at boot time.  If successful all of the fstab entries will show up in mtab.  mtab will contain additional entries such as temporary shares, USB insertions, external drives added after boot, etc.  Anything in fstab is loaded at boot.  Any failures to mount will show up in /var/log/syslog.  If your Buffalo goes down, as long as you are not accessing any files or directories, the mount should be OK, as long as the NAS is alive when you click on it in Nautilus to access files.  You can probably set power settings on the Buffalo that allow the disks to sleep, but the NAS stays active, to reduce power draw.

---

### Post by zerogamer100 on 2013-08-28
Okay So just to be clear. Once the NAS is hooked up, find it in my Mtab and copy the NAS line, navigate to fstab and add the line !!wq, then restart. is this correct? Do I need to create the volume or mount name ? ex: dev/bak before i do anything?

---

### Post by tgalati4 on 2013-08-28
Yes, it helps to create the mount name locally in a location that is convenient.  Then you would use the *mount* command in a terminal.  Otherwise, you will get whatever strange name that Nautilus assigns.  Once the drive is mounted, examine /etc/mtab to see what switches are used in the mount.  As usual in linux, there are several ways of doing the same thing:

[https://help.ubuntu.com/community/AutomaticallyMountPartitions](https://help.ubuntu.com/community/AutomaticallyMountPartitions)

[https://help.ubuntu.com/community/MountDevicesTroubleshooting](https://help.ubuntu.com/community/MountDevicesTroubleshooting)

---

