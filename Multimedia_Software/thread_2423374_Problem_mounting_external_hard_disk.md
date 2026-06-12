---
title: "Problem mounting external hard disk"
date: 2019-07-22
forum: Multimedia Software
---

### Post by ashotti2 on 2019-07-22
Hi all,

I have a FREECOM hard disk that I used without problems for a year more or less. One day it unfortunately disconnected from the laptop while it was copying some files. since then when I plug it I get the following:

> Error mounting /dev/sdc1 at /media/ ... : Command-line `mount -t "ntfs" -o "uhelper=udisks2,nodev,nosuid,uid=1001,gid=1001" "/dev/sdc1" "/media/...."' exited with non-zero exit status 13: $MFTMirr does not match $MFT (record 0).
Failed to mount '/dev/sdc1': Input/output error
NTFS is either inconsistent, or there is a hardware fault, or it's a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows twice. The usage of the /f parameter is very
important! If the device is a SoftRAID/FakeRAID then first activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for more details.

A couple of years ago I had a similar problem (with another hard disk) and I followed the instructions on what to do on Windows, and I lost my data. I hope there is another way without using windows and without loosing my data.

Thanks in advance for the help!

---

### Post by TheFu on 2019-07-22
Know idea how anything changed from the actions in the description.

```
gid=100 1
```
is wrong.
```
gid=1001
```
is probably what you need. Spaces are bad there.

Best to post using code tags and copy/paste directly from the terminal output. Quote tags isn't useful. Code tags are.

If you want to solve this forever, we need lots of background, like which Ubuntu release, how you mount the storage. Whether it is external or internal, how it is connected.  That information will help someone else provide the best possible guidance.

BTW, if you don't need NTFS for some really good reason, the easiest answer is to backup all the files somewhere else, then format make the disk have a GPT partition table, add a new partition, format it with EXT4, then connect it up.  Access will have native performance and native permissions, unlike what happens when using NTFS.

---

### Post by Autodave on 2019-07-22
You can also try bothering one of your Windows friends and run the HD on their machine and use Window's check disk function.

---

