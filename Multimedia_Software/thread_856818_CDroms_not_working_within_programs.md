---
title: "CDroms not working within programs"
date: 2008-07-11
forum: Multimedia Software
---

### Post by rMatey on 2008-07-11
Hi!  Working on Hardy 8.04 with dual boot.  Using two Seagate SATA drives.  Using a TDK CDr/w and a BENQ DVDr/w.  My problems is that the drives don't work or show up under any other programs other than K3B, serpentine and Rhythmbox.  How do you get the drive to show up other  than in PLACES and on the desktop with the other programs????
  I've read other posts.  here are my Terminal outputs.
dan@ubuntu:~$ df
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda1            304682836  24416480 264789340   9% /
varrun                 1037356       100   1037256   1% /var/run
varlock                1037356         0   1037356   0% /var/lock
udev                   1037356        68   1037288   1% /dev
devshm                 1037356        36   1037320   1% /dev/shm
lrm                    1037356     39760    997596   4% /lib/modules/2.6.24-19-generic/volatile
/dev/sdb5            125740720   4645568 121095152   4% /media/disk
dan@ubuntu:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=f84b4721-3570-4291-9b91-48ea0240f3ce /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=88ede7b3-5188-4196-b5cd-29033b468cba none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0
dan@ubuntu:~$ ls -l /dev/cd*  /dev/scd*  /dev/dvd*
lrwxrwxrwx  1 root root      4 2008-07-11 19:09 /dev/cdrom4 -> scd1
lrwxrwxrwx  1 root root      4 2008-07-11 19:09 /dev/cdrom5 -> scd0
lrwxrwxrwx  1 root root      4 2008-07-11 19:09 /dev/cdrw4 -> scd1
lrwxrwxrwx  1 root root      4 2008-07-11 19:09 /dev/cdrw5 -> scd0
lrwxrwxrwx  1 root root      4 2008-07-11 19:09 /dev/dvd4 -> scd1
lrwxrwxrwx  1 root root      4 2008-07-11 19:09 /dev/dvdrw4 -> scd1
brw-rw----+ 1 root cdrom 11, 0 2008-07-11 15:09 /dev/scd0
brw-rw----+ 1 root cdrom 11, 1 2008-07-11 15:09 /dev/scd1
dan@ubuntu:~$ sudo lshw -C disk
  *-disk:0                
       description: ATA Disk
       product: ST3320620AS
       vendor: Seagate
       physical id: 0
       bus info: scsi@2:0.0.0
       logical name: /dev/sda
       version: 3.AA
       serial: 6QF1LDVM
       size: 298GiB (320GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=a4090686
  *-disk:1
       description: ATA Disk
       product: ST3320620AS
       vendor: Seagate
       physical id: 1
       bus info: scsi@3:0.0.0
       logical name: /dev/sdb
       version: 3.AA
       serial: 6QF29QMP
       size: 298GiB (320GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=f4355ad2
  *-cdrom:0
       description: CD-R/CD-RW writer
       product: CDRW4800B
       vendor: TDK
       physical id: 0.0.0
       bus info: scsi@1:0.0.0
       logical name: /dev/scd0
       logical name: /dev/sr0
       version: S7S5
       capabilities: removable audio cd-r cd-rw
       configuration: ansiversion=5 status=ready
     *-medium
          physical id: 0
          logical name: /dev/scd0
  *-cdrom:1
       description: DVD writer
       product: DVD DD DW1620
       vendor: BENQ
       physical id: 0.1.0
       bus info: scsi@1:0.1.0
       logical name: /dev/scd1
       logical name: /dev/sr1
       version: B7V9
       capabilities: removable audio cd-r cd-rw dvd dvd-r
       configuration: ansiversion=5 status=open
dan@ubuntu:~$ sudo mount -v /media/cdrom0
mount: special device /dev/hdc does not exist
dan@ubuntu:~$ sudo mount -v /media/cdrom0
mount: special device /dev/hdc does not exist
dan@ubuntu:~$ mtab
bash: mtab: command not found
dan@ubuntu:~$ nautilus /media/cdrom0
dan@ubuntu:~$ ls -l /media/cdrom0
total 0
dan@ubuntu:~$ df
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda1            304682836  24416524 264789296   9% /
varrun                 1037356       100   1037256   1% /var/run
varlock                1037356         0   1037356   0% /var/lock
udev                   1037356        68   1037288   1% /dev
devshm                 1037356        36   1037320   1% /dev/shm
lrm                    1037356     39760    997596   4% /lib/modules/2.6.24-19-generic/volatile
/dev/sdb5            125740720   4645568 121095152   4% /media/disk
dan@ubuntu:~$ mount
/dev/sda1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.24-19-generic/volatile type tmpfs (rw)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
/dev/sdb5 on /media/disk type fuseblk (rw,nosuid,nodev,noatime,allow_other,blksize=4096)

  Music Cd currently in CDROM 0.
  Also, when using Nautilus for /media/cdrom it shows a cdrom-shortcut, a cdrom0, cdrom1, floppy-shortcut and a floppy0.  Clicking on the cdroms opens up an empty directory.  But in the left column it shows Audio Disk, and clicking it brings up the directory.

 Whats not linking the CDROM drives????
:confused:

---

### Post by unutbu on 2008-07-11
Change these two lines in your fstab 
```
/dev/hdc /media/cdrom0 udf,iso9660 user,noauto,exec 0 0
/dev/hdd /media/cdrom1 udf,iso9660 user,noauto,exec 0 0
```

to
```
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec 0       0
```

---

### Post by mc4man on 2008-07-11
r> wxrwxrwx 1 root root 4 2008-07-11 19:09 /dev/cdrom4 -> scd1
lrwxrwxrwx 1 root root 4 2008-07-11 19:09 /dev/cdrom5 -> scd0
lrwxrwxrwx 1 root root 4 2008-07-11 19:09 /dev/cdrw4 -> scd1
lrwxrwxrwx 1 root root 4 2008-07-11 19:09 /dev/cdrw5 -> scd0
lrwxrwxrwx 1 root root 4 2008-07-11 19:09 /dev/dvd4 -> scd1
lrwxrwxrwx 1 root root 4 2008-07-11 19:09 /dev/dvdrw4 -> scd1
Your /dev/links are bumped way up also, in all likelihood you have duplicate entries in  /etc/udev/rules.d/70-persistent-cd.rules. If so in the long run it's good to clean that up.
If you wish post the contents of that file
related threads
[http://ubuntuforums.org/showthread.php?t=801771](http://ubuntuforums.org/showthread.php?t=801771)
[http://ubuntuforums.org/showthread.php?t=855535](http://ubuntuforums.org/showthread.php?t=855535)

---

### Post by rMatey on 2008-07-12
> **mc4man said:**
> r
Your /dev/links are bumped way up also, in all likelihood you have duplicate entries in  /etc/udev/rules.d/70-persistent-cd.rules. If so in the long run it's good to clean that up.
If you wish post the contents of that file
related threads
[http://ubuntuforums.org/showthread.php?t=801771](http://ubuntuforums.org/showthread.php?t=801771)
[http://ubuntuforums.org/showthread.php?t=855535](http://ubuntuforums.org/showthread.php?t=855535)

Here's the file listing.  It ALL looks the same to me.


# TDK_CDRW4800B (pci-0000:00:0f.1-ide-0:0)
ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:0f.1-ide-0:0", SYMLINK+="cdrom", ENV{GENERATED}="1"
ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:0f.1-ide-0:0", SYMLINK+="cdrw", ENV{GENERATED}="1"
# BENQ_DVD_DD_DW1620 (pci-0000:00:0f.1-ide-0:1)
ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:0f.1-ide-0:1", SYMLINK+="cdrom1", ENV{GENERATED}="1"
ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:0f.1-ide-0:1", SYMLINK+="cdrw1", ENV{GENERATED}="1"
ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:0f.1-ide-0:1", SYMLINK+="dvd1", ENV{GENERATED}="1"
ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:0f.1-ide-0:1", SYMLINK+="dvdrw1", ENV{GENERATED}="1"
# BENQ_DVD_DD_DW1620 (pci-0000:00:0f.1-ide-1:1)
ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:0f.1-ide-1:1", SYMLINK+="cdrom2", ENV{GENERATED}="1"
ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:0f.1-ide-1:1", SYMLINK+="cdrw2", ENV{GENERATED}="1"
ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:0f.1-ide-1:1", SYMLINK+="dvd2", ENV{GENERATED}="1"
ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:0f.1-ide-1:1", SYMLINK+="dvdrw2", ENV{GENERATED}="1"
# TDK_CDRW4800B (pci-0000:00:0f.1-ide-1:0)
ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:0f.1-ide-1:0", SYMLINK+="cdrom3", ENV{GENERATED}="1"
ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:0f.1-ide-1:0", SYMLINK+="cdrw3", ENV{GENERATED}="1"
# DVD_DD_DW1620 (pci-0000:00:0f.1-scsi-1:0:1:0)
ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:0f.1-scsi-1:0:1:0", SYMLINK+="cdrom4", ENV{GENERATED}="1"
ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:0f.1-scsi-1:0:1:0", SYMLINK+="cdrw4", ENV{GENERATED}="1"
ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:0f.1-scsi-1:0:1:0", SYMLINK+="dvd4", ENV{GENERATED}="1"
ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:0f.1-scsi-1:0:1:0", SYMLINK+="dvdrw4", ENV{GENERATED}="1"
# CDRW4800B (pci-0000:00:0f.1-scsi-1:0:0:0)
ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:0f.1-scsi-1:0:0:0", SYMLINK+="cdrom5", ENV{GENERATED}="1"
ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:0f.1-scsi-1:0:0:0", SYMLINK+="cdrw5", ENV{GENERATED}="1"


 So, do I delete all but one of the drive entries each????  If, which ones to delete?

---

### Post by unutbu on 2008-07-12
First, make a back up of /etc/udev/rules.d/70-persistent-cd.rules:
```

sudo mv /etc/udev/rules.d/70-persistent-cd.rules /root/70-persistent-cd.rules
```

Next, make a new 70-persistent-cd.rules:
```

gksu gedit /etc/udev/rules.d/70-persistent-cd.rules

```
```
# TDK CDRW4800B (pci-0000:00:0f.1-scsi-1:0:0:0)
ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:0f.1-scsi-1:0:0:0", SYMLINK+="cdrom0", ENV{GENERATED}="1"
ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:0f.1-scsi-1:0:0:0", SYMLINK+="cdrw0", ENV{GENERATED}="1"

# BENQ DVD_DD_DW1620 (pci-0000:00:0f.1-scsi-1:0:1:0)
ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:0f.1-scsi-1:0:1:0", SYMLINK+="cdrom1", ENV{GENERATED}="1"
ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:0f.1-scsi-1:0:1:0", SYMLINK+="cdrw1", ENV{GENERATED}="1"
ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:0f.1-scsi-1:0:1:0", SYMLINK+="dvd", ENV{GENERATED}="1"
ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:0f.1-scsi-1:0:1:0", SYMLINK+="dvdrw", ENV{GENERATED}="1"
```

This should make symlinks between 
```
/dev/cdrom0 -> /dev/scd0
/dev/cdrw0 -> /dev/scd0
```
for the TDK CCDRW

and 
```

/dev/cdrom1 -> /dev/scd1
/dev/cdrw1 -> /dev/scd1
/dev/dvd -> /dev/scd1
/dev/dvdrw -> /dev/scd1
```
for the BENQ DVD

The TDK should be accessible at /media/cdrom0
and BENQ at /media/cdrom1

If it doesn't work, please post
```

for dev in `ls /sys/bus/scsi/devices`; do udevinfo -ap /sys/bus/scsi/devices/$dev; done > udevinfo.txt

```

---

### Post by mc4man on 2008-07-12
Actually no need to back it up or really even create a new one. Just delete all the entries and _reboot_. 70-.....rules is controlled/created by 75-....rules. Just leave 70-....rules looking like this.
```
# This file maintains persistent names for CD/DVD reader and writer devices.
# See udev(7) for syntax.
#
# Entries are automatically added by the 75-persistent-cd-generator.rules
# file; however you are also free to add your own entries provided you
# add the ENV{GENERATED}=1 flag to your own rules as well.
```

It's better to do this way rather than rewriting so you avoid mistakes (in this case maybe not a big deal, but if 75-...rules is going to make new entries for you ,let it)

> # TDK CDRW4800B (pci-0000:00:0f.1-scsi-1:0:0:0)
ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:0f.1-scsi-1:0:0:0", SYMLINK+="[COLOR="Red"]cdrom0[/COLOR]", ENV{GENERATED}="1"
ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:0f.1-scsi-1:0:0:0", SYMLINK+="[COLOR="Red"]cdrw0"[/COLOR], ENV{GENERATED}="1"

Optionally you could also gksudo nautilus to /dev and delete all related _links_. (cdrw, cdrom, dvd, dvdrw, sr0, cdrw1, dvd1 ect., ect, In your case some will go up to 5)
When you reboot you'll get a new 70-...rules and new links or if you don't delete the links the ones that are now being used will be rewritten to proper targets.(ie. cdrom,cdrom1,cdrw,cdrw1,dvd,sr0,sr1)

slightly Ot. You have your cdrw drive in a 'mastered' position over the dvdrw. If your using separate ide controllers for each of them then it doesn't really matter. If they're both on the same ide then you might consider moving the dvdrw to the end connector and the cdrw to the middle one if your comfortable doing so.

---

### Post by unutbu on 2008-07-12
Thank you for the corrections, mc4man.
Can I ask, what is wrong with cdrom0 and cdrw0? Aren't you free to name them anything you want?

Edit: I suppose if there is a program that is hard coded to access the cdrom at /dev/cdrom, then you'd have a problem. Is there an app that does this? I'm so command-line oriented, I don't know.

---

### Post by rMatey on 2008-07-12
> **unutbu said:**
> First, make a back up of /etc/udev/rules.d/70-persistent-cd.rules:
```

sudo mv /etc/udev/rules.d/70-persistent-cd.rules /root/70-persistent-cd.rules
```

Next, make a new 70-persistent-cd.rules:
```

gksu gedit /etc/udev/rules.d/70-persistent-cd.rules

```
```
# TDK CDRW4800B (pci-0000:00:0f.1-scsi-1:0:0:0)
ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:0f.1-scsi-1:0:0:0", SYMLINK+="cdrom0", ENV{GENERATED}="1"
ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:0f.1-scsi-1:0:0:0", SYMLINK+="cdrw0", ENV{GENERATED}="1"

# BENQ DVD_DD_DW1620 (pci-0000:00:0f.1-scsi-1:0:1:0)
ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:0f.1-scsi-1:0:1:0", SYMLINK+="cdrom1", ENV{GENERATED}="1"
ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:0f.1-scsi-1:0:1:0", SYMLINK+="cdrw1", ENV{GENERATED}="1"
ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:0f.1-scsi-1:0:1:0", SYMLINK+="dvd", ENV{GENERATED}="1"
ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:0f.1-scsi-1:0:1:0", SYMLINK+="dvdrw", ENV{GENERATED}="1"
```

This should make symlinks between 
```
/dev/cdrom0 -> /dev/scd0
/dev/cdrw0 -> /dev/scd0
```
for the TDK CCDRW

and 
```

/dev/cdrom1 -> /dev/scd1
/dev/cdrw1 -> /dev/scd1
/dev/dvd -> /dev/scd1
/dev/dvdrw -> /dev/scd1
```
for the BENQ DVD

The TDK should be accessible at /media/cdrom0
and BENQ at /media/cdrom1

If it doesn't work, please post
```

for dev in `ls /sys/bus/scsi/devices`; do udevinfo -ap /sys/bus/scsi/devices/$dev; done > udevinfo.txt

```

   Followed instructions.  Exaile still not finding disk or device.  Amarok the same.  Autoplay plugin for Gxine fails.  Nothing happens in Xine.  Guess I'll just have to survive on VLC K3B Rhythymbox and Serpentine.

Udevinfo starts with the device specified by the devpath and then
walks up the chain of parent devices. It prints for every device
found, all possible attributes in the udev rules key format.
A rule to match, can be composed by the attributes of the device
and the attributes from one single parent device.

  looking at device '/devices/pci0000:00/0000:00:0f.1/host1/target1:0:0/1:0:0:0':
    KERNEL=="1:0:0:0"
    SUBSYSTEM=="scsi"
    DRIVER=="sr"
    ATTR{device_blocked}=="0"
    ATTR{type}=="5"
    ATTR{scsi_level}=="6"
    ATTR{vendor}=="TDK     "
    ATTR{model}=="CDRW4800B       "
    ATTR{rev}=="S7S5"
    ATTR{state}=="running"
    ATTR{timeout}=="0"
    ATTR{iocounterbits}=="32"
    ATTR{iorequest_cnt}=="0x16a0"
    ATTR{iodone_cnt}=="0x15a4"
    ATTR{ioerr_cnt}=="0x0"
    ATTR{modalias}=="scsi:t-0x05"
    ATTR{evt_media_change}=="0"
    ATTR{queue_depth}=="1"
    ATTR{queue_type}=="none"

  looking at parent device '/devices/pci0000:00/0000:00:0f.1/host1/target1:0:0':
    KERNELS=="target1:0:0"
    SUBSYSTEMS==""
    DRIVERS==""

  looking at parent device '/devices/pci0000:00/0000:00:0f.1/host1':
    KERNELS=="host1"
    SUBSYSTEMS==""
    DRIVERS==""

  looking at parent device '/devices/pci0000:00/0000:00:0f.1':
    KERNELS=="0000:00:0f.1"
    SUBSYSTEMS=="pci"
    DRIVERS=="pata_via"
    ATTRS{vendor}=="0x1106"
    ATTRS{device}=="0x0571"
    ATTRS{subsystem_vendor}=="0x147b"
    ATTRS{subsystem_device}=="0x1413"
    ATTRS{class}=="0x01018a"
    ATTRS{irq}=="17"
    ATTRS{local_cpus}=="ff"
    ATTRS{modalias}=="pci:v00001106d00000571sv0000147Bsd00001413bc01sc01i8a"
    ATTRS{broken_parity_status}=="0"
    ATTRS{msi_bus}==""

  looking at parent device '/devices/pci0000:00':
    KERNELS=="pci0000:00"
    SUBSYSTEMS==""
    DRIVERS==""


Udevinfo starts with the device specified by the devpath and then
walks up the chain of parent devices. It prints for every device
found, all possible attributes in the udev rules key format.
A rule to match, can be composed by the attributes of the device
and the attributes from one single parent device.

  looking at device '/devices/pci0000:00/0000:00:0f.1/host1/target1:0:1/1:0:1:0':
    KERNEL=="1:0:1:0"
    SUBSYSTEM=="scsi"
    DRIVER=="sr"
    ATTR{device_blocked}=="0"
    ATTR{type}=="5"
    ATTR{scsi_level}=="6"
    ATTR{vendor}=="BENQ    "
    ATTR{model}=="DVD DD DW1620   "
    ATTR{rev}=="B7V9"
    ATTR{state}=="running"
    ATTR{timeout}=="0"
    ATTR{iocounterbits}=="32"
    ATTR{iorequest_cnt}=="0x1c56"
    ATTR{iodone_cnt}=="0x392"
    ATTR{ioerr_cnt}=="0x0"
    ATTR{modalias}=="scsi:t-0x05"
    ATTR{evt_media_change}=="0"
    ATTR{queue_depth}=="1"
    ATTR{queue_type}=="none"

  looking at parent device '/devices/pci0000:00/0000:00:0f.1/host1/target1:0:1':
    KERNELS=="target1:0:1"
    SUBSYSTEMS==""
    DRIVERS==""

  looking at parent device '/devices/pci0000:00/0000:00:0f.1/host1':
    KERNELS=="host1"
    SUBSYSTEMS==""
    DRIVERS==""

  looking at parent device '/devices/pci0000:00/0000:00:0f.1':
    KERNELS=="0000:00:0f.1"
    SUBSYSTEMS=="pci"
    DRIVERS=="pata_via"
    ATTRS{vendor}=="0x1106"
    ATTRS{device}=="0x0571"
    ATTRS{subsystem_vendor}=="0x147b"
    ATTRS{subsystem_device}=="0x1413"
    ATTRS{class}=="0x01018a"
    ATTRS{irq}=="17"
    ATTRS{local_cpus}=="ff"
    ATTRS{modalias}=="pci:v00001106d00000571sv0000147Bsd00001413bc01sc01i8a"
    ATTRS{broken_parity_status}=="0"
    ATTRS{msi_bus}==""

  looking at parent device '/devices/pci0000:00':
    KERNELS=="pci0000:00"
    SUBSYSTEMS==""
    DRIVERS==""


Udevinfo starts with the device specified by the devpath and then
walks up the chain of parent devices. It prints for every device
found, all possible attributes in the udev rules key format.
A rule to match, can be composed by the attributes of the device
and the attributes from one single parent device.

  looking at device '/devices/pci0000:00/0000:00:0f.0/host2/target2:0:0/2:0:0:0':
    KERNEL=="2:0:0:0"
    SUBSYSTEM=="scsi"
    DRIVER=="sd"
    ATTR{device_blocked}=="0"
    ATTR{type}=="0"
    ATTR{scsi_level}=="6"
    ATTR{vendor}=="ATA     "
    ATTR{model}=="ST3320620AS     "
    ATTR{rev}=="3.AA"
    ATTR{state}=="running"
    ATTR{timeout}=="30"
    ATTR{iocounterbits}=="32"
    ATTR{iorequest_cnt}=="0x6b8d"
    ATTR{iodone_cnt}=="0x6b8d"
    ATTR{ioerr_cnt}=="0x0"
    ATTR{modalias}=="scsi:t-0x00"
    ATTR{evt_media_change}=="0"
    ATTR{queue_depth}=="1"
    ATTR{queue_type}=="none"

  looking at parent device '/devices/pci0000:00/0000:00:0f.0/host2/target2:0:0':
    KERNELS=="target2:0:0"
    SUBSYSTEMS==""
    DRIVERS==""

  looking at parent device '/devices/pci0000:00/0000:00:0f.0/host2':
    KERNELS=="host2"
    SUBSYSTEMS==""
    DRIVERS==""

  looking at parent device '/devices/pci0000:00/0000:00:0f.0':
    KERNELS=="0000:00:0f.0"
    SUBSYSTEMS=="pci"
    DRIVERS=="sata_via"
    ATTRS{vendor}=="0x1106"
    ATTRS{device}=="0x3149"
    ATTRS{subsystem_vendor}=="0x147b"
    ATTRS{subsystem_device}=="0x1413"
    ATTRS{class}=="0x01018f"
    ATTRS{irq}=="17"
    ATTRS{local_cpus}=="ff"
    ATTRS{modalias}=="pci:v00001106d00003149sv0000147Bsd00001413bc01sc01i8f"
    ATTRS{broken_parity_status}=="0"
    ATTRS{msi_bus}==""

  looking at parent device '/devices/pci0000:00':
    KERNELS=="pci0000:00"
    SUBSYSTEMS==""
    DRIVERS==""


Udevinfo starts with the device specified by the devpath and then
walks up the chain of parent devices. It prints for every device
found, all possible attributes in the udev rules key format.
A rule to match, can be composed by the attributes of the device
and the attributes from one single parent device.

  looking at device '/devices/pci0000:00/0000:00:0f.0/host3/target3:0:0/3:0:0:0':
    KERNEL=="3:0:0:0"
    SUBSYSTEM=="scsi"
    DRIVER=="sd"
    ATTR{device_blocked}=="0"
    ATTR{type}=="0"
    ATTR{scsi_level}=="6"
    ATTR{vendor}=="ATA     "
    ATTR{model}=="ST3320620AS     "
    ATTR{rev}=="3.AA"
    ATTR{state}=="running"
    ATTR{timeout}=="30"
    ATTR{iocounterbits}=="32"
    ATTR{iorequest_cnt}=="0xc5"
    ATTR{iodone_cnt}=="0xc5"
    ATTR{ioerr_cnt}=="0x0"
    ATTR{modalias}=="scsi:t-0x00"
    ATTR{evt_media_change}=="0"
    ATTR{queue_depth}=="1"
    ATTR{queue_type}=="none"

  looking at parent device '/devices/pci0000:00/0000:00:0f.0/host3/target3:0:0':
    KERNELS=="target3:0:0"
    SUBSYSTEMS==""
    DRIVERS==""

  looking at parent device '/devices/pci0000:00/0000:00:0f.0/host3':
    KERNELS=="host3"
    SUBSYSTEMS==""
    DRIVERS==""

  looking at parent device '/devices/pci0000:00/0000:00:0f.0':
    KERNELS=="0000:00:0f.0"
    SUBSYSTEMS=="pci"
    DRIVERS=="sata_via"
    ATTRS{vendor}=="0x1106"
    ATTRS{device}=="0x3149"
    ATTRS{subsystem_vendor}=="0x147b"
    ATTRS{subsystem_device}=="0x1413"
    ATTRS{class}=="0x01018f"
    ATTRS{irq}=="17"
    ATTRS{local_cpus}=="ff"
    ATTRS{modalias}=="pci:v00001106d00003149sv0000147Bsd00001413bc01sc01i8f"
    ATTRS{broken_parity_status}=="0"
    ATTRS{msi_bus}==""

  looking at parent device '/devices/pci0000:00':
    KERNELS=="pci0000:00"
    SUBSYSTEMS==""
    DRIVERS==""

---

### Post by mc4man on 2008-07-12
> Can I ask, what is wrong with cdrom0 and cdrw0? Aren't you free to name them anything you want?
in 70...rules you can name them anything you want. My tthinking is that the entries are created for you so why take the chance on errant typing or copy and paste. In regards to the /dev/cdrom link there are some apps that default to that. Amarok comes to mind. While it wouldn't have come up in this instance with /dev/dvd most apps default to that. More a matter of keeping things simple with less chance of error.

Actually i was just a few min. ago feeling not right about how i posted that.

---

### Post by unutbu on 2008-07-12
rMatey, I think perhaps you need to reboot.
If it doesn't work after reboot, try mc4man's instructions in [post #6]("http://ubuntuforums.org/showpost.php?p=5373814&postcount=6").
Reboot again. If it still doesn't work, please post
```

ls -l /dev | grep scd
cat /etc/udev/rules.d/70-persistent-cd.rules   

```

---

### Post by rMatey on 2008-07-12
> **unutbu said:**
> rMatey, I think perhaps you need to reboot.
If it doesn't work after reboot, try mc4man's instructions in [post #6]("http://ubuntuforums.org/showpost.php?p=5373814&postcount=6").
Reboot again. If it still doesn't work, please post
```

ls -l /dev | grep scd
cat /etc/udev/rules.d/70-persistent-cd.rules   

```
...............................................................

  Was changing CDrom drives.  Changed to mc4manss' suggested chages.  Seems to act the same, in fact the large dev/links is back.  Here is output.
(Made the computer myself, so drives no big thing.  My third build.)

dan@ubuntu:~$ ls -l /dev/cd* /dev/scd* /dev/dvd*
lrwxrwxrwx  1 root root      4 2008-07-12 22:24 /dev/cdrom4 -> scd1
lrwxrwxrwx  1 root root      4 2008-07-12 22:24 /dev/cdrom5 -> scd0
lrwxrwxrwx  1 root root      4 2008-07-12 22:24 /dev/cdrw4 -> scd1
lrwxrwxrwx  1 root root      4 2008-07-12 22:24 /dev/cdrw5 -> scd0
lrwxrwxrwx  1 root root      4 2008-07-12 22:24 /dev/dvd4 -> scd1
lrwxrwxrwx  1 root root      4 2008-07-12 22:24 /dev/dvdrw4 -> scd1
brw-rw----+ 1 root cdrom 11, 0 2008-07-12 18:24 /dev/scd0
brw-rw----+ 1 root cdrom 11, 1 2008-07-12 18:24 /dev/scd1
dan@ubuntu:~$ sudo lshw -C disk
[sudo] password for dan: 
  *-disk:0                
       description: ATA Disk
       product: ST3320620AS
       vendor: Seagate
       physical id: 0
       bus info: scsi@2:0.0.0
       logical name: /dev/sda
       version: 3.AA
       serial: 6QF1LDVM
       size: 298GiB (320GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=a4090686
  *-disk:1
       description: ATA Disk
       product: ST3320620AS
       vendor: Seagate
       physical id: 1
       bus info: scsi@3:0.0.0
       logical name: /dev/sdb
       version: 3.AA
       serial: 6QF29QMP
       size: 298GiB (320GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=f4355ad2
  *-cdrom:0
       description: CD-R/CD-RW writer
       product: CDRW4800B
       vendor: TDK
       physical id: 0.0.0
       bus info: scsi@1:0.0.0
       logical name: /dev/scd0
       logical name: /dev/sr0
       version: S7S5
       capabilities: removable audio cd-r cd-rw
       configuration: ansiversion=5 status=open
  *-cdrom:1
       description: DVD writer
       product: DVD DD DW1620
       vendor: BENQ
       physical id: 0.1.0
       bus info: scsi@1:0.1.0
       logical name: /dev/scd1
       logical name: /dev/sr1
       version: B7V9
       capabilities: removable audio cd-r cd-rw dvd dvd-r
       configuration: ansiversion=5 status=open
dan@ubuntu:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=f84b4721-3570-4291-9b91-48ea0240f3ce /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=88ede7b3-5188-4196-b5cd-29033b468cba none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0
dan@ubuntu:~$ cat /etc/udev/rules.d/70-persistent-cd.rules
# This file maintains persistent names for CD/DVD reader and writer devices.
# See udev(7) for syntax.
#
# Entries are automatically added by the 75-persistent-cd-generator.rules
# file; however you are also free to add your own entries provided you
# add the ENV{GENERATED}=1 flag to your own rules as well.

---

### Post by unutbu on 2008-07-12
Let's just test if we can get things working before we worry about making the changes persistent.

Try

```
sudo ln -sf /dev/scd0 /dev/cdrom
```

This will make a link from /dev/cdrom to /dev/scd0.
Does this allow exaile, amarok and company to find your TDK CD drive?

---

### Post by mc4man on 2008-07-12
i'm gonna stay out of this but i can't help but say I think you all are making this much more complicated than it needs to be. Just delete all the entries  Stop switching drives about. Every time you remove or switch a drive the entries and /dev links are reserved in case the drive is returned and new entries are made and new links created that are 1 up.
Plus go into /dev and remove all the links as mentioned, and then reboot. 
If any of your apps still are having problems go in to the settings or preferences and adjust the default device as needed.

---

### Post by rMatey on 2008-07-13
> **unutbu said:**
> Let's just test if we can get things working before we worry about making the changes persistent.

Try

```
sudo ln -sf /dev/scd0 /dev/cdrom
```

This will make a link from /dev/cdrom to /dev/scd0.
Does this allow exaile, amarok and company to find your TDK CD drive?
...................................................................
  Success!!!!!!!!   Don't know what happened after all of that, but followed all of mc4mans next to last instructions.  Added the link from unutbus' last post (I added it again, was done before on linking).  Anyhow, everything working under Amarok like it should.
  And I learned a valuable lesson from mc4man. "Actually no need to back it up or really even create a new one. Just delete all the entries and reboot."  :)  Let the computer do the typing for you, instead of cut and paste.
  And thanks to unutbu, I also recall now that sometimes you have to reboot more than once for some changes to take hold.  I knew to reboot, but for some reason it took more than one...

 Thanks again!  :popcorn:

---

### Post by mc4man on 2008-07-13
Glad to hear
Remember if down the road you swap a drive double ck. (after a reboot) in 70....rules to see if the old drive is still there. Also if you happen to use sandisk thumb drives (micro cruzer) they'll get 2 entries in ...rules, so it's very easy for a new drive to end up with dev links of 4, 5 ect.

and sorry if I was seeming a little frustrated - it really is a simple process in the end

---

