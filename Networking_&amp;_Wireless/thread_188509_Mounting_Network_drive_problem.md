---
title: "Mounting Network drive problem"
date: 2006-06-04
forum: Networking &amp; Wireless
---

### Post by blkno1 on 2006-06-04
Well I got it to work, silly me.  I didn't have smbfs installed.  A simple apt-get smbfs and presto, did a quick mount -a and my network drive appeared.


I Have a Buffalo 250G LinkStation on my network.  I have a Breezy box next to the new Dapper one and everything works fine.

My /ect/fstab on both machines are the same concerning the network drive.
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
//192.168.1.111/multimedia   /media/landrive   smbfs credentials=/root/credentials,uid=jim     0       0

```

The credentials file looks like this FYI

```
Username=xxx
Password=xxx
```

But when I type sudo mount -a I get

```
mount: wrong fs type, bad option, bad superblock on //192.168.1.111/multimedia,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
```

The output of dmesg | tail gives me this output...

root@Prime:/home/jim# dmesg | tail
```
[4294711.301000] Bluetooth: HCI socket layer initialized
[4294711.363000] Bluetooth: L2CAP ver 2.8
[4294711.363000] Bluetooth: L2CAP socket layer initialized
[4294711.366000] Bluetooth: RFCOMM socket layer initialized
[4294711.366000] Bluetooth: RFCOMM TTY layer initialized
[4294711.366000] Bluetooth: RFCOMM ver 1.7
[4295017.858000] ibm_acpi: ec object not found
[4295972.603000] smbfs: mount_data version 1684370019 is not supported
```

---

### Post by s31523 on 2006-06-04
That error usually means the wrong version of smbfs is installed.  Try installing it again.  Also, check out:
[http://ubuntuforums.org/showthread.php?t=187475](http://ubuntuforums.org/showthread.php?t=187475)

---

### Post by thisispeace on 2007-09-24
I'm having an issue with permissions.  i've edited my fstab file, adding

//address/share /media/netDrive    smbfs   username=username,password=password   0   0


But nothing mounts.  When i go to Places -> Network in Gnome, I see "netDrive", but when I click on it, I'm told that only root may mount the drive.  What can I do?

---

