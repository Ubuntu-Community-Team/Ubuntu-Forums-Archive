---
title: "CD playback  / burn skips"
date: 2009-11-06
forum: Multimedia Software
---

### Post by calcio1 on 2009-11-06
I am trying to extract audio from a CD.

Rhythmbox / Sound extractor / VLC etc skip and jerk, the audio is unlistenable. Some programmes just hang completely when I attempt to play CD

It is definitely not the disc.

I thought it might be the drive and bought a brand new one. Still same problem.

I think maybe it is something to do with DMA but don't know. 

I have only noticed problem since upgrading to Karmic but it may have existed before since this is the first time I have tried to extract CD on ubuntu.

Please help.

---

### Post by calcio1 on 2009-11-06
```
rhythmbox

** (rhythmbox:4870): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (rhythmbox:4870): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed
WARNING: Unhandled message: interface=org.freedesktop.DBus.Introspectable, path=/, member=Introspect
Sense key: 0x70 0x00 0x04 0x00 0x00 0x00 0x00 0x0a 0x00 0x00 0x00 0x00 0x08 0x03 0x00 0x00 0x00 0x00 0x00 
scsi_read error: sector=54 length=27 retry=0
                 Sense key: 4 ASC: 8 ASCQ: 3
                 Transport error: Target hardware fault
                 System error: Input/output error
scsi_read error: sector=81 length=27 retry=0
                 Sense key: 4 ASC: 8 ASCQ: 3
                 Transport error: Target hardware fault
                 System error: Input/output error
scsi_read error: sector=81 length=13 retry=1
                 Sense key: 4 ASC: 8 ASCQ: 3
                 Transport error: Target hardware fault
                 System error: Input/output error
scsi_read error: sector=81 length=6 retry=2
                 Sense key: 4 ASC: 8 ASCQ: 3
                 Transport error: Target hardware fault
                 System error: Input/output error
scsi_read error: sector=81 length=3 retry=3
                 Sense key: 4 ASC: 8 ASCQ: 3
                 Transport error: Target hardware fault
                 System error: Input/output error
scsi_read error: sector=81 length=1 retry=4
                 Sense key: 4 ASC: 8 ASCQ: 3
                 Transport error: Target hardware fault
                 System error: Input/output error
scsi_read error: sector=81 length=1 retry=5
                 Sense key: 4 ASC: 8 ASCQ: 3
                 Transport error: Target hardware fault
                 System error: Input/output error
scsi_read error: sector=81 length=1 retry=6
                 Sense key: 4 ASC: 8 ASCQ: 3
                 Transport error: Target hardware fault
                 System error: Input/output error
scsi_read error: sector=81 length=1 retry=7
                 Sense key: 4 ASC: 8 ASCQ: 3
                 Transport error: Target hardware fault
                 System error: Input/output error
scsi_read error: sector=81 length=1 retry=8
                 Sense key: 4 ASC: 8 ASCQ: 3
                 Transport error: Target hardware fault
                 System error: Input/output error
scsi_read error: sector=108 length=27 retry=0
                 Sense key: 4 ASC: 8 ASCQ: 3
                 Transport error: Target hardware fault
                 System error: Input/output error
scsi_read error: sector=108 length=13 retry=1
                 Sense key: 4 ASC: 8 ASCQ: 3
                 Transport error: Target hardware fault
                 System error: Input/output error
scsi_read error: sector=108 length=6 retry=2
                 Sense key: 4 ASC: 8 ASCQ: 3
                 Transport error: Target hardware fault
                 System error: Input/output error
scsi_read error: sector=108 length=3 retry=3
                 Sense key: 4 ASC: 8 ASCQ: 3
                 Transport error: Target hardware fault
                 System error: Input/output error
scsi_read error: sector=108 length=1 retry=4
                 Sense key: 4 ASC: 8 ASCQ: 3
                 Transport error: Target hardware fault
                 System error: Input/output error
scsi_read error: sector=108 length=1 retry=5
                 Sense key: 4 ASC: 8 ASCQ: 3
                 Transport error: Target hardware fault
                 System error: Input/output error
scsi_read error: sector=108 length=1 retry=6
                 Sense key: 4 ASC: 8 ASCQ: 3
                 Transport error: Target hardware fault
                 System error: Input/output error
scsi_read error: sector=108 length=1 retry=7
                 Sense key: 4 ASC: 8 ASCQ: 3
                 Transport error: Target hardware fault
                 System error: Input/output error
scsi_read error: sector=108 length=1 retry=8
                 Sense key: 4 ASC: 8 ASCQ: 3
                 Transport error: Target hardware fault
                 System error: Input/output error
scsi_read error: sector=135 length=15 retry=0
                 Sense key: 4 ASC: 8 ASCQ: 3
                 Transport error: Target hardware fault
                 System error: Input/output error
scsi_read error: sector=135 length=7 retry=1
                 Sense key: 4 ASC: 8 ASCQ: 3
                 Transport error: Target hardware fault
                 System error: Input/output error
scsi_read error: sector=135 length=3 retry=2
                 Sense key: 4 ASC: 8 ASCQ: 3
                 Transport error: Target hardware fault
                 System error: Input/output error
scsi_read error: sector=135 length=1 retry=3
                 Sense key: 4 ASC: 8 ASCQ: 3
                 Transport error: Target hardware fault
                 System error: Input/output error
scsi_read error: sector=135 length=1 retry=4
                 Sense key: 4 ASC: 8 ASCQ: 3
                 Transport error: Target hardware fault
                 System error: Input/output error
scsi_read error: sector=135 length=1 retry=5
                 Sense key: 4 ASC: 8 ASCQ: 3
                 Transport error: Target hardware fault
                 System error: Input/output error
scsi_read error: sector=135 length=1 retry=6
                 Sense key: 4 ASC: 8 ASCQ: 3
                 Transport error: Target hardware fault
                 System error: Input/output error
scsi_read error: sector=135 length=1 retry=7
                 Sense key: 4 ASC: 8 ASCQ: 3
                 Transport error: Target hardware fault
                 System error: Input/output error
scsi_read error: sector=135 length=1 retry=8
                 Sense key: 4 ASC: 8 ASCQ: 3
                 Transport error: Target hardware fault
                 System error: Input/output error


cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=06cd41a0-3b7a-4b35-8782-bd32de4cdce9 /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=4d718759-caac-4d2b-bc00-a0c92a1eb09e none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

#/dev/sdb2 /media/ipod vfat nosuid,noauto,nodev,rw,umask=077,gid=1000,uid=1000,user,defaults,noatime,iocharset=utf8 0 0



sudo lshw -C disk
  *-disk                  
       description: ATA Disk
       product: Maxtor 6L250R0
       vendor: Maxtor
       physical id: 0.1.0
       bus info: scsi@0:0.1.0
       logical name: /dev/sda
       version: BAJ4
       serial: L51FXQTG
       size: 233GiB (251GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=af63af63
  *-cdrom
       description: DVD-RAM writer
       product: iHAP322   9
       vendor: ATAPI
       physical id: 0.0.0
       bus info: scsi@1:0.0.0
       logical name: /dev/cdrom
       logical name: /dev/cdrw
       logical name: /dev/dvd
       logical name: /dev/dvdrw
       logical name: /dev/scd0
       logical name: /dev/sr0
       version: 6L19
       capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
       configuration: ansiversion=5 status=ready
     *-medium
          physical id: 0
          logical name: /dev/cdrom



hdparm -i /dev/sr0

/dev/sr0:
 HDIO_DRIVE_CMD(identify) failed: Bad address

 Model=ATAPI, FwRev=6L19, SerialNo=
 Config={ Fixed Removeable DTR<=5Mbs DTR>10Mbs nonMagnetic }
 RawCHS=0/0/0, TrkSize=0, SectSize=0, ECCbytes=0
 BuffType=unknown, BuffSize=0kB, MaxMultSect=0
 (maybe): CurCHS=0/0/0, CurSects=0, LBA=yes, LBAsects=0
 IORDY=yes, tPIO={min:240,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio3 pio4 
 DMA modes:  mdma0 mdma1 mdma2 
 UDMA modes: udma0 udma1 udma2 udma3 *udma4 
 AdvancedPM=no
 Drive conforms to: Unspecified:  ATA/ATAPI-4,5,6,7

 * signifies the current active mode




```

---

### Post by calcio1 on 2009-11-09
anybody?

---

