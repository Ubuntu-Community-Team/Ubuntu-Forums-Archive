---
title: "mount.ntfs-3g cpu load high"
date: 2012-01-16
forum: Multimedia Software
---

### Post by thomasw81 on 2012-01-16
Hi guys,

Since the last software update about 5 days ago on my netbook 10.04.3 LTS I am having trouble with high CPU loads on mount.ntfs-3g. Continuously at least 50%. I noticed because Rythmbox and other programs that access the external hard disk (NTFS filesystem) got sluggish. 

Has anyone had this problem or found a solution?

Thanks!

---

### Post by Wug on 2012-03-08
I am also experiencing an issue very like this one.  I'm in the process of disaster recovery, imaging a 500GB hard drive to another drive with ddrescue.  The only drive we have with enough space was an external, and I had to move 200GB of backups to my laptop to make enough space.  Drive is a USB2.0 1TB NTFS-formatted external.

Originally, process went smoothly (10+MB/s), but the write speed to the drive has slowed down dramatically since the imaging began (it's down to only about 100KB/s).  top shows that mount.ntfs is using 100% of one CPU core.  I have experienced this issue before but never this badly.  I'm using a liveCD and the only process using the destination drive is ddrescue.  The source drive is formatted as ntfs, but this does not matter because it's not mounted and is being accessed directly.

Other possibly relevant info:
-Image file was preallocated to the full required size of ~500GB
-Drive is mostly full, but this should not matter much as the image was preallocated
-Writing is currently taking place at about 100KB/s about 40GB from the END of the file
-iostat is showing no unexpected input or output, just the anomolously low transfer rates between the two drives
-the destination file is NOT deeper than 8 nested directories

edit --
sorry to bump a month old post, but I've googled around and found a bunch of threads all with the same problem, but with no answers.  There were a few things about cron jobs for rsnapshot or rsync, neither of which are or have ever run in this environment.  I checked lsof but nothing was out of place, just a few bashes with opened directories and ddrescue.

---

### Post by Wug on 2012-03-08
I believe the issue to be related to the size of the file Im trying to deal with.  It seems less like a bug and more like a design issue or some other flaw in program logic.  Really, this more or less makes ntfs filesystems useless for any sort of real work using linux, which is unfortunate.

Oh people of the future who find this thread and have the same issue, you might be out of luck.  Looks like this issue has been around a while and it doesnt look like its going anywhere anytime soon.

---

### Post by jarondl on 2012-05-22
Have you found a solution since this post?
This bug will cost me two work days.

---

### Post by slycker on 2012-08-13
High CPU usage on a linux system writing to an NTFS volume can come from a number of sources, as described on tuxera (the maintainer of ntfs-3g). They make an optimized, comercialized version of an ntfs driver, but this isn't open-source, nor is it easily available. If you're committed to NTFS, you're stuck with this less stream-lined ntfs-3g driver.

[http://www.tuxera.com/community/ntfs-3g-faq/#highcpu](http://www.tuxera.com/community/ntfs-3g-faq/#highcpu)

Assuming you are using a recent version of ubuntu, with a recent version of ntfs-3g, then options are programs frequently reading/writing big chunks of data to the drive, application frequently accessing the drive (such as rsync), the drive being connected via a slow usb connection (possibly the usb port speed slowed down by a slow device/hub being attached), VMWare using temp files on the ntfs drive, or the drive being excessively fragmented (lots of debate around this issue, many people saying the drive shouldn't get too fragmented for linux unless you are also booting an installation of windows off of that drive). Read the above link for more information about these and more.

My solution was to go to my fstab and modify the mount line to include big_writes in the options (ie: defaults,big_writes ....). This caused it to write big chunks, rather than smaller chunks.

Disabling samba access to the drive and shutting down python scripts accessing the drive didn't have any impact for me.

---

