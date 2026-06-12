---
title: "Problem mounting 2nd and 3rd Harddrive in my HTPC"
date: 2011-04-16
forum: Mythbuntu
---

### Post by bryan.sailer on 2011-04-16
I recently installed Mythbuntu 10.10 and the install went fine but I have two 500G Hard drives that have videos and Pictures that I amt trying to mount to the directory where MythTV can find them. I have edited the /etc/fstab file read as below:
 
/dev/sdb /var/lib/mythtv/pictures ext4 defaults 0 0
/dev/sdc /var/lib/mythtv/videos ext4 defaults 0 0
 
When I restarted the HTPC there was an error mounting both devices to the mount point. The two hard drives were mounted in my desktop with no problems. What might the problem be? How do I go about fixing this issue?
 
MythBuntu 10.10

---

### Post by ian dobson on 2011-04-16
Hi,

Are you sure your device is /dev/sdb and not /dev/sdb1, what does fdisk -l /dev/sdb show?

Regards
Ian Dobson

---

### Post by ilcapo09 on 2011-04-16
Did you check the permissions? I recently installed Mythbuntu 10.10 and I couldn't record anything to my second drive because mythtv didn't have permission to write to it

---

### Post by bryan.sailer on 2011-04-17
Yes, after looking up the drive names I was miss labeling them. Once I changed from sdb to sdb1 everything mounted correctly. 

Now I can see the Pictures in my gallary but On the other hard drive where my videos are I do not see them on mythtv. I will check the permissions and see if that is the problem. Thank you for the suggestion.

---

### Post by jb5 on 2011-04-19
In Myth, when on the video page have you tried pressing M, and then selecting scan for changes, to bring your videos up?

---

