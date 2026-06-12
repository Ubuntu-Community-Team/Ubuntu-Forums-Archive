---
title: "Working on a few issues"
date: 2008-09-21
forum: Mythbuntu
---

### Post by Caps18 on 2008-09-21
I'm trying to organize myself here and list what I need to work on tonight/tomorrow.  If you have any advice or tips, I'll take them.

1. Get 1TB hard drive recognized and working
2. Setup MythVideo on new drive
3. Transfer all media files from Mythbuntu drive and external USB drives to the new one
4. Setup router (or buy replacement)
5. Setup (permanent) NFS networking between laptop and Mythbuntu box
6. Transfer media from laptop to MythVideo
7. Setup MythVideo (new posters, info, imdb?)
8. Setup pictures
9. Setup 5.1 digital audio along with analog stereo audio
10. Watch a movie

------------------------------------------------------------
1. Problem with hard drive:

I just installed a second SCSI drive in my Mythbuntu machine and thought I set it up correctly.  It was working and I wrote 2 GB (that I knew I could lose) to the drive.  I was copying those files off to an external drive and the computer locked up and had to have the plug pulled.  Now when I restarted it, I get the error:

> Cannot mount volume

Unable to mount the volume

Details

mount: wrong fs type, bad option, bad superblock on /dev/sdb1, missing codepage or helper program, or other error.  In some cases useful info is found in syslog -try    dmesg | tail or so

> Failed to mount "1T volume"

Failed to determine the mount point for /dev/sdb1

Is this some type of root permission issue since I am only a user logging in?  When I type sudo mount -t jfs /dev/sdb1 /mnt/sdb1 into the terminal I get the same error as above:

> mount: wrong fs type, bad option, bad superblock on /dev/sdb1, missing codepage or helper program, or other error.  
In some cases useful info is found in syslog -try
dmesg | tail or so

I'm not sure if I setup my /etc/fstab file correctly though.  I added this manually:

> 
#/dev/sdb1
UUID=     /mnt/sdb1    jfs     defaults    0    0

I'm not sure if I need to give it a UUID, or find it's UUID, or have it enter it automatically or something...

dmesg | tail doesn't have anything useful (ip6 router can't be found NFSD grace period, AGP stuff), and it can't find the syslog command.

Did I kill this drive or something?  What else can I try to get it working?  What advice do you have to set it up so this can't happen again and just works?  

Thanks!

---

### Post by DemonBob on 2008-09-21
To find the disk's UUID use this command.

```
blkid /dev/sdxx 
``` 

Where sdxx is the 1tb drive, you can find this out by issueing: ```
sudo fdisk -l
```

---

### Post by Caps18 on 2008-09-22
The computer finds it, and I added the UUID to the /etc/fstab file.  But I still get the same error message.

Should I format it again and start over?  Or is there something else I can try?

---

