---
title: "Unable to mount/read VCD"
date: 2008-01-02
forum: Multimedia &amp; Video
---

### Post by manoj_paul_joseph on 2008-01-02
Hi,

I am on 7.10, Gutsy Gibbon. I am unable to read some Video CDs. I have not, however, seen this problem with DVDs and data CDs.

I am able to play the same VCD from Windows.

I see the following messages when automount fails. 

[FONT="Courier New"][ 5530.136000] end_request: I/O error, dev sr0, sector 20160
[ 5530.136000] Buffer I/O error on device sr0, logical block 2520
[ 5530.228000] end_request: I/O error, dev sr0, sector 20160
[ 5530.228000] Buffer I/O error on device sr0, logical block 2520
[ 5530.316000] end_request: I/O error, dev sr0, sector 20176
[ 5530.316000] Buffer I/O error on device sr0, logical block 2522
[ 5530.408000] end_request: I/O error, dev sr0, sector 20176
[ 5530.408000] Buffer I/O error on device sr0, logical block 2522
[ 5530.504000] end_request: I/O error, dev sr0, sector 20184
[ 5530.504000] Buffer I/O error on device sr0, logical block 2523
[ 5530.504000] Buffer I/O error on device sr0, logical block 2524
[ 5530.596000] end_request: I/O error, dev sr0, sector 20184
[ 5530.596000] Buffer I/O error on device sr0, logical block 2523
[ 5530.688000] end_request: I/O error, dev sr0, sector 20176
[ 5530.688000] Buffer I/O error on device sr0, logical block 2522
[ 5530.784000] end_request: I/O error, dev sr0, sector 20176
[ 5530.784000] Buffer I/O error on device sr0, logical block 2522
[ 5530.880000] end_request: I/O error, dev sr0, sector 20184
[ 5530.880000] Buffer I/O error on device sr0, logical block 2523
[ 5530.968000] end_request: I/O error, dev sr0, sector 20176
[ 5531.064000] end_request: I/O error, dev sr0, sector 20176
[ 5531.156000] end_request: I/O error, dev sr0, sector 20176
[ 5531.248000] end_request: I/O error, dev sr0, sector 20176
[ 5531.344000] end_request: I/O error, dev sr0, sector 20176
[ 5531.440000] end_request: I/O error, dev sr0, sector 20304
[ 5531.536000] end_request: I/O error, dev sr0, sector 20240
[ 5531.632000] end_request: I/O error, dev sr0, sector 20240
[ 5531.724000] end_request: I/O error, dev sr0, sector 20240
[ 5531.824000] end_request: I/O error, dev sr0, sector 20176
[ 5531.916000] end_request: I/O error, dev sr0, sector 20176
[ 5532.008000] end_request: I/O error, dev sr0, sector 20176
[ 5532.104000] end_request: I/O error, dev sr0, sector 20176
[ 5532.196000] end_request: I/O error, dev sr0, sector 20176
[ 5532.284000] end_request: I/O error, dev sr0, sector 20192
[ 5532.372000] end_request: I/O error, dev sr0, sector 20176
[ 5532.464000] end_request: I/O error, dev sr0, sector 20176
[ 5532.560000] end_request: I/O error, dev sr0, sector 20176
[ 5532.652000] end_request: I/O error, dev sr0, sector 20176
[ 5532.744000] end_request: I/O error, dev sr0, sector 20176
[ 5532.840000] end_request: I/O error, dev sr0, sector 20176
[ 5532.936000] end_request: I/O error, dev sr0, sector 20184
[ 5533.100000] end_request: I/O error, dev sr0, sector 0
[ 5533.196000] end_request: I/O error, dev sr0, sector 0
[ 5533.288000] end_request: I/O error, dev sr0, sector 0
[ 5533.380000] end_request: I/O error, dev sr0, sector 0
[ 5533.476000] end_request: I/O error, dev sr0, sector 0
[ 5533.568000] end_request: I/O error, dev sr0, sector 0
[ 5533.660000] end_request: I/O error, dev sr0, sector 0
[ 5533.756000] end_request: I/O error, dev sr0, sector 0
[ 5533.848000] end_request: I/O error, dev sr0, sector 0
[ 5533.944000] end_request: I/O error, dev sr0, sector 0
[ 5534.036000] end_request: I/O error, dev sr0, sector 0
[ 5534.128000] end_request: I/O error, dev sr0, sector 0
[ 5534.224000] end_request: I/O error, dev sr0, sector 0
[ 5534.316000] end_request: I/O error, dev sr0, sector 0
[ 5534.408000] end_request: I/O error, dev sr0, sector 0
[ 5534.504000] end_request: I/O error, dev sr0, sector 0
[ 5534.596000] end_request: I/O error, dev sr0, sector 0
[ 5534.692000] end_request: I/O error, dev sr0, sector 0
[ 5534.784000] end_request: I/O error, dev sr0, sector 0
[ 5534.876000] end_request: I/O error, dev sr0, sector 0
[ 5534.972000] end_request: I/O error, dev sr0, sector 0
[ 5535.064000] end_request: I/O error, dev sr0, sector 0
[ 5535.156000] end_request: I/O error, dev sr0, sector 0
[ 5535.156000] printk: 44 messages suppressed.
[ 5535.156000] Buffer I/O error on device sr0, logical block 0
[ 5535.252000] end_request: I/O error, dev sr0, sector 0
[ 5535.344000] end_request: I/O error, dev sr0, sector 0
[ 5535.436000] end_request: I/O error, dev sr0, sector 0
[ 5535.532000] end_request: I/O error, dev sr0, sector 0
[ 5535.636000] end_request: I/O error, dev sr0, sector 0
[ 5535.732000] end_request: I/O error, dev sr0, sector 0
[ 5536.020000] UDF-fs: No VRS found
[ 5538.300000] end_request: I/O error, dev sr0, sector 0
[ 5538.396000] end_request: I/O error, dev sr0, sector 4
[ 5538.488000] end_request: I/O error, dev sr0, sector 0
[ 5538.584000] end_request: I/O error, dev sr0, sector 1024
[ 5538.676000] end_request: I/O error, dev sr0, sector 1024
[ 5538.804000] end_request: I/O error, dev sr0, sector 0
[ 5538.900000] end_request: I/O error, dev sr0, sector 1024
[ 5538.992000] end_request: I/O error, dev sr0, sector 1028
[ 5539.132000] end_request: I/O error, dev sr0, sector 0
[ 5539.228000] end_request: I/O error, dev sr0, sector 1024
[ 5539.320000] end_request: I/O error, dev sr0, sector 1028
[ 5539.456000] end_request: I/O error, dev sr0, sector 0
[ 5539.552000] end_request: I/O error, dev sr0, sector 1024
[ 5539.648000] end_request: I/O error, dev sr0, sector 1028
[/FONT]

Does anyone have any idea what this issue might be? Is this a known bug?

Regards,
Manoj

---

### Post by jendalsepit on 2008-01-03
hmm ...
when u're booting, enter to command shell (Alt+F2)
type with : ```
**gksu nautilus**
```
edit fstab's file (/etc/fstab), and then comment out the file **sr0** (depend on your problems ...)
reboot ...

:)

---

### Post by manoj_paul_joseph on 2008-01-04
> **jendalsepit said:**
> 
edit fstab's file (/etc/fstab), and then comment out the file **sr0** (depend on your problems ...)
reboot ...


Interestingly there is no sr0 in /etc/fstab. There is however a "/dev/scd0       /media/cdrom0" which I commented out and rebooted. Gnome still tries to automount and fails with the same messages in /var/log/messages.

I tried to manually mount the device and succeded. I was able to browse the directories. But reading the files failed.

```
 $ sudo mount -t iso9660 /dev/scd0       /media/cdrom0
[sudo] password for manoj:
mount: block device /dev/scd0 is write-protected, mounting read-only
$ ls /media/cdrom0/
cdda  cdi  ext  karaoke  mpegav  segment  vcd
$ ls /media/cdrom0/mpegav/avseq0
avseq01.dat  avseq02.dat  
$ ls /media/cdrom0/mpegav/avseq01.dat 
/media/cdrom0/mpegav/avseq01.dat
$ cp /media/cdrom0/mpegav/avseq01.dat  .
cp: reading `/media/cdrom0/mpegav/avseq01.dat': Input/output error
$
```

So the CD is readable but the files are not!

Any clues?

---

### Post by svins on 2008-03-20
I have the same problem. I can mount VCD with mount /dev/0 /media/cdrom -t iso9660, i can browse, but can not read/copy files. But VLC can play the VCD, without mounting it!

---

### Post by Dynamo_Joe on 2008-03-20
I have been trying to resolve this issue for quite some time now. 

When I installed Dapper, VCD playback was not an issue - put in the disk and the default movie player played it. 

I have since upgraded to Feisty (after a motherboard swap - Dapper didn't recognise the onboard NIC - no internet) and still have not managed to get VCDs to play. 

I have searched the forums and applied some of the solutions (including installing gxine) but still no joy. 

I still have the Dapper installation on a separate HDD - when I get the time, plug it back in and see what it has installed and maybe get some clue from it ... don't hold out for me to though! :) 

If somebody comes up with a solution in the mean time, it will be highly appreciated. 

If I do find a solution, I'll post it back in the forums.

---

