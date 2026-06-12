---
title: "2x1Tb disc partition question"
date: 2010-06-17
forum: Mythbuntu
---

### Post by blkbx on 2010-06-17
I want to do a new install of mythbuntu 10.04 using two one terabyte drive. I know that this is alot of space but I want to put my iso movies onto one of the disks. I also record alot of television so in the end I think that I'll be adding more space in the future.
So now to my question. I want to give the folders that hold Mythtv as much space as I can but am not sure the best way to do this. Do I for example give one Tb to /var/lib/mythtv where the recorded content is stored am I right, then install / root onto the first one Tb drive and leave it at that. Or a small /root directory and large /home and /var/lib/mythtv.
thanks

---

### Post by tgm4883 on 2010-06-17
> **blkbx said:**
> I want to do a new install of mythbuntu 10.04 using two one terabyte drive. I know that this is alot of space but I want to put my iso movies onto one of the disks. I also record alot of television so in the end I think that I'll be adding more space in the future.
So now to my question. I want to give the folders that hold Mythtv as much space as I can but am not sure the best way to do this. Do I for example give one Tb to /var/lib/mythtv where the recorded content is stored am I right, then install / root onto the first one Tb drive and leave it at that. Or a small /root directory and large /home and /var/lib/mythtv.
thanks

Personally, I would go small root, mount the rest of drive 1 to /var/lib/mythtv/recordings and the other drive to /var/lib/mythtv. I wouldn't mount /home to a separate partition if this is just a media center

---

### Post by psusi on 2010-06-17
If they are two basically identical disks, raid them.  Don't have to worry about breaking up the storage into different areas, and you get twice the throughput with raid0.

---

### Post by ian dobson on 2010-06-17
Hi,

I'd probably RAID1 (mirror) a small 20Gb boot and root partition then just split the rest into 2 mount points and tell mythtv to use storage groups for both mount points. MythTV will then dump it's recordings one or the other mount point based on the free space/IO load on the drive.

Thats was I'm doing on my main backend. I have a mirrored boot/root partition of about 20Gb and the rest in in a RAID5 array.

Getting Ubuntu to boot from a mirrored disk is a royal pain in the butt but when it works you have protection against a disk falour.

Regards
Ian Dobson

---

### Post by blkbx on 2010-06-21
Thanks for the replies. Never thought of using raid though not sure how identical the drives are other than their size. I think I'll go with splitting drive0 with a root partition and /var/lib/myth/recording and drive 1 with /var/lib/myth/recording. See how that works out for me unless someone has a better partition type.
thanks

---

