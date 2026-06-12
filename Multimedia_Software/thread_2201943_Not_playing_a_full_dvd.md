---
title: "Not playing a full dvd"
date: 2014-01-26
forum: Multimedia Software
---

### Post by lcb503 on 2014-01-26
Hi,

 I need help getting the DVD to play fully (e.g. I can only play the first 1hour 30 of a two hour movie). I have two dvd's which end before the film has completely finished and show no further chapters (both with VLC and ubuntus default video). I have tried a second dvd player but this has the same problem (ihas122 and a samsung). All the restricted extra have been install and the first dvd player had its region set to europe (where the dvd were purchased from). Any help would be greatly appreciated. Thanks Quin

---

### Post by lcb503 on 2014-01-27
After testing and quite alot of faffing, I discovered that the dvd is only reading one of the two dvd layers (tried flipping over the disc and managed to read the second half of the film). I checked if the DVD drives are dual layer compatible and they are. Could anyone suggest a reason for this?

---

### Post by lcb503 on 2014-01-27
Herew is the lshw for the dvd drive:

 *-scsi:0
          physical id: 1
          logical name: scsi1
          capabilities: emulated
        *-cdrom
             description: DVD-RAM writer
             product: CDDVDW SH-224DB
             vendor: TSSTcorp
             physical id: 0.0.0
             bus info: scsi@1:0.0.0
             logical name: /dev/cdrom
             logical name: /dev/sr0
             logical name: /media/luke/GFBP44MF1
             version: SB01
             capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
             configuration: ansiversion=5 mount.fstype=udf mount.options=ro,nosuid,nodev,relatime,uid=1000,gid=1000,umask=77,iocharset=utf8 state=mounted status=ready
           *-medium
                physical id: 0
                logical name: /dev/cdrom
                logical name: /media/luke/GFBP44MF1
                configuration: mount.fstype=udf mount.options=ro,nosuid,nodev,relatime,uid=1000,gid=1000,umask=77,iocharset=utf8 state=mounted

---

