---
title: "iPod settings on Xubuntu"
date: 2007-12-25
forum: Multimedia &amp; Video
---

### Post by graabein on 2007-12-25
Hi I have installed Xubuntu 7.10 on a previous install of Xubuntu and I have a couple questions:


**1) Two iPod icons appear on desktop when I plug it in on USB.**

Here is the **dmesg** output:

```
[ 1686.452570] USB Mass Storage support registered.
[ 1691.449268] usb-storage: device scan complete
[ 1691.453286] scsi 4:0:0:0: Direct-Access     Apple    iPod             1.62 PQ: 0 ANSI: 0
[ 1691.483201] sd 4:0:0:0: [sdb] 117210239 512-byte hardware sectors (60012 MB)
[ 1691.489186] sd 4:0:0:0: [sdb] Write Protect is off
[ 1691.489212] sd 4:0:0:0: [sdb] Mode Sense: 64 00 00 08
[ 1691.489225] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[ 1691.497178] sd 4:0:0:0: [sdb] 117210239 512-byte hardware sectors (60012 MB)
[ 1691.503176] sd 4:0:0:0: [sdb] Write Protect is off
[ 1691.503199] sd 4:0:0:0: [sdb] Mode Sense: 64 00 00 08
[ 1691.503210] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[ 1691.503228]  sdb: sdb1 sdb2
[ 1691.552033]  sdb: p2 exceeds device capacity
[ 1691.552335] sd 4:0:0:0: [sdb] Attached SCSI removable disk
[ 1691.552520] sd 4:0:0:0: Attached scsi generic sg2 type 0
[ 1693.417441] attempt to access beyond end of device
[ 1693.417473] sdb: rw=0, want=117210240, limit=117210239
[ 1693.417489] Buffer I/O error on device sdb2, logical block 117129914
[ 1693.477592] attempt to access beyond end of device
[ 1693.477625] sdb: rw=0, want=117210240, limit=117210239
[ 1693.477640] Buffer I/O error on device sdb2, logical block 117129914
[ 1693.478866] attempt to access beyond end of device
[ 1693.478887] sdb: rw=0, want=117210240, limit=117210239
[ 1693.478901] Buffer I/O error on device sdb2, logical block 117129914
[ 1693.480291] attempt to access beyond end of device
[ 1693.480313] sdb: rw=0, want=117210240, limit=117210239
[ 1693.480327] Buffer I/O error on device sdb2, logical block 117129914
[ 1693.481689] attempt to access beyond end of device
[ 1693.481710] sdb: rw=0, want=117210240, limit=117210239
[ 1693.481724] Buffer I/O error on device sdb2, logical block 117129914
[ 1693.482849] attempt to access beyond end of device
[ 1693.482870] sdb: rw=0, want=117210240, limit=117210239
[ 1693.482883] Buffer I/O error on device sdb2, logical block 117129914
[ 1693.484005] attempt to access beyond end of device
[ 1693.484025] sdb: rw=0, want=117210240, limit=117210239
[ 1693.484039] Buffer I/O error on device sdb2, logical block 117129914
[ 1693.573590] attempt to access beyond end of device
[ 1693.573622] sdb: rw=0, want=117210240, limit=117210239
[ 1693.573637] Buffer I/O error on device sdb2, logical block 117129914
[ 1693.575116] attempt to access beyond end of device
[ 1693.575139] sdb: rw=0, want=117210240, limit=117210239
[ 1693.575153] Buffer I/O error on device sdb2, logical block 117129914
[ 1694.603421] attempt to access beyond end of device
[ 1694.603499] sdb: rw=0, want=117210240, limit=117210239
[ 1694.603515] Buffer I/O error on device sdb2, logical block 117129914
[ 1694.625136] attempt to access beyond end of device
[ 1694.625168] sdb: rw=0, want=117210240, limit=117210239
[ 1694.627050] attempt to access beyond end of device
[ 1694.627073] sdb: rw=0, want=117210240, limit=117210239
[ 1694.637683] attempt to access beyond end of device
[ 1694.637715] sdb: rw=0, want=117210240, limit=117210239
[ 1694.639243] attempt to access beyond end of device
[ 1694.639266] sdb: rw=0, want=117210240, limit=117210239
[ 1694.640898] attempt to access beyond end of device
[ 1694.640921] sdb: rw=0, want=117210240, limit=117210239
[ 1694.642439] attempt to access beyond end of device
[ 1694.642461] sdb: rw=0, want=117210240, limit=117210239
[ 1694.790184] attempt to access beyond end of device
[ 1694.790217] sdb: rw=0, want=117210240, limit=117210239
[ 1694.790941] attempt to access beyond end of device
[ 1694.790961] sdb: rw=0, want=117210240, limit=117210239
```

and my **/etc/fstab**:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=80c96146-e2a3-4418-b634-7c2bbe682b91 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda3
UUID=c53ab2e0-1462-491d-8acc-5b7e7bbc4f1d /home           ext3    defaults        0       2
# /dev/sda5
UUID=3df849e9-1942-4dae-b506-0bf144685c9d none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
```

I don't know where to start looking for duplicates?


**2) Can't seem to get gtkpod to sync files.**

Maybe user rights are not correct? Here is **ls -l /media**:

```
total 8
lrwxrwxrwx 1 root     root    6 2007-12-23 17:43 cdrom -> cdrom0
drwxr-xr-x 2 root     root 4096 2007-12-23 17:43 cdrom0
drwx------ 8 graabein root 4096 1970-01-01 01:00 GRAAPOD
```


Help please! :)

---

