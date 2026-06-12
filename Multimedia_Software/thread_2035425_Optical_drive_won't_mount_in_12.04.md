---
title: "Optical drive won't mount in 12.04"
date: 2012-07-30
forum: Multimedia Software
---

### Post by daKoolaid on 2012-07-30
I hate to start another of these threads, but nothing I've found in the others has helped. 

This is a Sony Vaio laptop with 12.04 & Unity and discs will not mount at all, even if I add /dev/sr0 to fstab. The install was done with usb drive so I've only just noticed the dvd issue when trying to play movies. Here are some outputs.
```
sudo lshw -C disk
......................
  *-cdrom
       description: DVD-RAM writer
       product: DVD RW AD-7700H
       vendor: Optiarc
       physical id: 1
       bus info: scsi@1:0.0.0
       logical name: /dev/cdrom
       logical name: /dev/cdrw
       logical name: /dev/dvd
       logical name: /dev/dvdrw
       logical name: /dev/sr0
       version: 1.V0
       capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
       configuration: ansiversion=5 status=nodisc

```

```
ls -l  /dev/cdrom /dev/cdrw /dev/dvd /dev/dvdrw /dev/scd0 /dev/sr0
ls: cannot access /dev/scd0: No such file or directory
lrwxrwxrwx  1 root root      3 Jul 30 14:01 /dev/cdrom -> sr0
lrwxrwxrwx  1 root root      3 Jul 30 14:01 /dev/cdrw -> sr0
lrwxrwxrwx  1 root root      3 Jul 30 14:01 /dev/dvd -> sr0
lrwxrwxrwx  1 root root      3 Jul 30 14:01 /dev/dvdrw -> sr0
brw-rw----+ 1 root cdrom 11, 0 Jul 30 14:01 /dev/sr0

```

```
wodim --devices
wodim: Overview of accessible drives (1 found) :
-------------------------------------------------------------------------
 0  dev='/dev/sg1'    rwrw-- : 'Optiarc' 'DVD RW AD-7700H'
-------------------------------------------------------------------------

```

From all that, I don't understand why wodim shows /dev/sg1 and everything else sr0, but regardless, I'm unable to mount any optical media through terminal too. I get the response, 'no medium found'. 

Any help would be spectacular, thank you in advance.

---

### Post by bozinsek on 2013-01-15
I'm encountering the same issue in 12.10... Dell Studio 1735..Optiarc 7640s.

I can eject through the terminal

```
 *-cdrom
       description: DVD-RAM writer
       product: DVD+-RW AD-7640S
       vendor: Optiarc
       physical id: 0.0.0
       bus info: scsi@1:0.0.0
       logical name: /dev/cdrom
       logical name: /dev/cdrw
       logical name: /dev/dvd
       logical name: /dev/dvdrw
       logical name: /dev/sr0
       version: HD14
       capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
       configuration: ansiversion=5 status=nodisc

```


```
boz@boz-Studio-1735:~$ wodim --devices
wodim: Overview of accessible drives (1 found) :
-------------------------------------------------------------------------
 0  dev='/dev/sg1'	rwrw-- : 'Optiarc' 'DVD+-RW AD-7640S'
-------------------------------------------------------------------------

```

Bootable Cd/DVD will boot at post and bios diagnostics picks up the device and passes all tests. I'm baffled!

---

