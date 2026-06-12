---
title: "vlc dvd mount point"
date: 2008-01-21
forum: Multimedia &amp; Video
---

### Post by yon2501 on 2008-01-21
where do you go in vlc to change the mount point for dvds because right now it thinks its at /dev/scd0 which dosent even exsist. i need it at /media/cdrom which i can do manually every time i put a disc in but its still a pain.

---

### Post by logos34 on 2008-01-21
it should be set for '/dev/<drive>' -- mine's /dev/hdc.

What's listed in /etc/fstab?

---

### Post by yon2501 on 2008-01-21
in /exe/fstab ive got 
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda6
UUID=903d91de-7fef-4e84-98c9-c8cf7cec8371 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=2AB4F2BCB4F28A19 /media/sda1     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda5
UUID=f8b8fecf-57c4-47d1-b25a-3f6ba52758e8 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0

```

---

### Post by logos34 on 2008-01-21
well, /dev/scd0 is listed right there.  Are dvds and cds otherwise mounting ok?

When you press play button (>) in VLC, the 'Open' dialog box pops up, and under 'Disc' tab you should be able to choose 'device name'...It should work with either /dev/scd0 or /dev/dvd (if there's a symlink of the latter in /dev).

---

### Post by yon2501 on 2008-01-21
yeah its listed there but it dosent actually exist if i look at the folder. and the only place dvd's and cds have been mounting is at /media/cdrom nothing else. i just need to know how to change the mount point vlc looks at. what i normally do now is pop in the disc then open vlc and go to file > open disc then it has /dev/scd as the place its looking at i simply change that to /media/cdrom but it only saves for the session that vlc is open.

---

### Post by logos34 on 2008-01-21
hmm...tell me, what does 

**sudo lshw -C disk **

show? (i.e. 'logical name' for optical drive?)

---

### Post by yon2501 on 2008-01-21
this is what i got 
```

  *-disk
       description: SCSI Disk
       product: Hitachi HTS72101
       vendor: ATA
       physical id: 0
       bus info: scsi@0:0.0.0
       logical name: /dev/sda
       version: MCZO
       serial: MPCZN7Y0GZG2UL
       size: 93GB
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5
  *-cdrom
       description: DVD writer
       product: DVD+-RW ND-6650A
       vendor: _NEC
       physical id: 1
       bus info: scsi@1:0.0.0
       logical name: /dev/cdrom
       logical name: /dev/dvd
       logical name: /dev/scd0
       logical name: /dev/sr0
       version: 102C
       serial: [_NEC    DVD+-RW ND-6650A102C05051200
       capabilities: removable audio cd-r cd-rw dvd dvd-r
       configuration: ansiversion=5 status=ready
     *-disc
          physical id: 0
          logical name: /dev/cdrom

```

---

### Post by logos34 on 2008-01-21
hmm, it lists four different logical names..

the cd/dvd mount point in fstab is /media/cdrom**0**

run

**gnome-volume-properties**

is it set to 'mount removable media when inserted' (the box should be ticked)

This will mount cds/dvds for you at /media/cdrom0.

Also, set the multimedia tab>video dvd discs>**check 'play video dvd doiscs when inserted'**
command: **vlc**

do that and then try inserting a dvd...Anything?  Or do you still have to adjust it manually each time?

---

