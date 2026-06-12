---
title: "Can't mount DVD rom"
date: 2009-05-22
forum: Mythbuntu
---

### Post by don_engtech on 2009-05-22
On new install of 9.04 DVDrom mounted OK as cdrom0 (i think) and was playing audio cds.  After putting my SATA raid card back in I can't mount DVDrom.  could the raid card be causing a problem...

```
:/dev$ ls -l | grep dvd1
lrwxrwxrwx  1 root   root           3 2009-05-21 22:59 dvd1 -> sr0
:/dev$ ls -l | grep cdrom1
lrwxrwxrwx  1 root   root           3 2009-05-21 22:59 cdrom1 -> sr0

```
fstab:```
# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=971daa22-12ec-4844-85f8-2be08dc0d1f5 /               ext3    errors=remount-ro 0       1
# /var/lib was on /dev/sda6 during installation
UUID=00e1eb4c-6793-4b0b-8b63-d1f35a8e549c /var/lib        xfs     defaults        0       2
# swap was on /dev/sda5 during installation
UUID=9bc7d897-9e8a-4e2d-ad51-b283f51660ee none            swap    sw              0       0
/dev/sr0	/media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/sdb1	/media/Multimedia ext2	defaults 0	0
```

dmesg:
```

[    2.054582] scsi 1:0:0:0: CD-ROM            LITE-ON  DVD SOHD-167T    9S16 PQ: 0 ANSI: 5
[    2.056100] sr0: scsi3-mmc drive: 48x/48x cd/rw xa/form2 cdda tray
[    2.056104] Uniform CD-ROM driver Revision: 3.20
[    2.056228] sr 1:0:0:0: Attached scsi CD-ROM sr0
...............
[    2.597383] megaraid cmm: 2.20.2.7 (Release Date: Sun Jul 16 00:01:03 EST 2006)
[    2.599143] megaraid: 2.20.5.1 (Release Date: Thu Nov 16 15:32:35 EST 2006)
[    2.599186] megaraid: probe new device 0x1000:0x1960:0x1000:0x4523: bus 0:slot 11:func 0
[    2.599214] megaraid 0000:00:0b.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    2.620088] megaraid: fw version:[713N] bios version:[G119]
[    2.662991] scsi2 : LSI Logic MegaRAID driver

```

mount:```
:/dev$ sudo mount -t iso9660 /dev/sr0 /media/cdrom
mount: block device /dev/sr0 is write-protected, mounting read-only
mount: wrong fs type, bad option, bad superblock on /dev/sr0,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
```
dmesg | tail : ```
[74439.343441] end_request: I/O error, dev sr0, sector 64
[74439.343467] isofs_fill_super: bread failed, dev=sr0, iso_blknum=16, block=16
[74505.567898] end_request: I/O error, dev sr0, sector 64
[74505.567924] isofs_fill_super: bread failed, dev=sr0, iso_blknum=16, block=16
[77351.478849] end_request: I/O error, dev sr0, sector 64
[77351.478876] isofs_fill_super: bread failed, dev=sr0, iso_blknum=16, block=16
[77365.640978] end_request: I/O error, dev sr0, sector 64
[77365.641001] isofs_fill_super: bread failed, dev=sr0, iso_blknum=16, block=16
```

Any thoughts would be appreciated,
Don

---

