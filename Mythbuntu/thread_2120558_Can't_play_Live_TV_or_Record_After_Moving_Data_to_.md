---
title: "Can't play Live TV or Record After Moving Data to network drive"
date: 2013-02-26
forum: Mythbuntu
---

### Post by grunge09 on 2013-02-26
Its fixed now.  Marked thread as solved.  Permissions issue on backend /mnt/mythtv and had to fix /etc/fstab.  See last post for exact fix. 

I copied all /var/lin/mythtv files & folders to a Samba Network share of /mnt/mythtv

Stopped backend and renamed local Mythtv folder.

Ran backend setup and changed all file paths I could find
 to network path.

Ran mythtfilldatabase

Ran frontend, setup and changed ell paths I could find. 

I can play recorded stuff no problem,  I can play music no problem.

BUT I can no longer play Live TV or record upcoming scheduled stuff or manually scheduled stuff

I checked mythtbackend log and found...

TVRec(22): HW Tuner: 22->22
2013-02-26 21:37:35.720 format_to_mode() does not recognize V4L1
2013-02-26 21:37:35.775 New DB connection, total: 4
2013-02-26 21:37:35.847 Connected to database 'mythconverg' at host: 192.168.0.100
2013-02-26 21:37:35.848 LoadFromScheduler(): Error, called from backend.
2013-02-26 21:37:35.923 AutoExpire: CalcParams(): Max required Free Space: 2.0 GB w/freq: 15 min
2013-02-26 21:37:36.955 TFW, Error: Opening file '/mnt/mythtv/livetv/1068_20130226213736.mpg'.
			eno: Permission denied (13)
2013-02-26 21:37:37.059 TVRec(22) Error: RingBuffer '/mnt/mythtv/livetv/1068_20130226213736.mpg' not open...
2013-02-26 21:37:37.179 TVRec(22) Error: CreateLiveTVRingBuffer(68) failed
2013-02-26 21:37:37.288 TVRec(22) Error: Failed to create RingBuffer 1
2013-02-26 21:37:38.524 TVRec(22): Changing from WatchingLiveTV to None
2013-02-26 21:37:38.971 Reschedule requested for id 0.
2013-02-26 21:37:41.003 Scheduled 758 items in 2.0 = 0.08 match + 1.93 place

I checked on the ubuntu 12.10 server

ls -ld /storage/mythtv

drwxrwxr-x 13 mythtv mythtv 4096 feb 26 19:22 /storage/mythtv

Please Help ASAP, thanks.

---

### Post by PhilWig on 2013-02-27
Any clues here?

[http://ubuntuforums.org/archive/index.php/t-946930.html](http://ubuntuforums.org/archive/index.php/t-946930.html)

> Stopped backend and renamed local Mythtv folder
Which folder is that?  Not /home/mythtv?

Phil

---

### Post by tgm4883 on 2013-02-27
> **grunge09 said:**
> I copied all /var/lin/mythtv files & folders to a Samba Network share of /mnt/mythtv

Stopped backend and renamed local Mythtv folder.

Ran backend setup and changed all file paths I could find
 to network path.

Ran mythtfilldatabase

Ran frontend, setup and changed ell paths I could find. 

I can play recorded stuff no problem,  I can play music no problem.

BUT I can no longer play Live TV or record upcoming scheduled stuff or manually scheduled stuff

I checked mythtbackend log and found...

TVRec(22): HW Tuner: 22->22
2013-02-26 21:37:35.720 format_to_mode() does not recognize V4L1
2013-02-26 21:37:35.775 New DB connection, total: 4
2013-02-26 21:37:35.847 Connected to database 'mythconverg' at host: 192.168.0.100
2013-02-26 21:37:35.848 LoadFromScheduler(): Error, called from backend.
2013-02-26 21:37:35.923 AutoExpire: CalcParams(): Max required Free Space: 2.0 GB w/freq: 15 min
2013-02-26 21:37:36.955 TFW, Error: Opening file '/mnt/mythtv/livetv/1068_20130226213736.mpg'.
			eno: Permission denied (13)
2013-02-26 21:37:37.059 TVRec(22) Error: RingBuffer '/mnt/mythtv/livetv/1068_20130226213736.mpg' not open...
2013-02-26 21:37:37.179 TVRec(22) Error: CreateLiveTVRingBuffer(68) failed
2013-02-26 21:37:37.288 TVRec(22) Error: Failed to create RingBuffer 1
2013-02-26 21:37:38.524 TVRec(22): Changing from WatchingLiveTV to None
2013-02-26 21:37:38.971 Reschedule requested for id 0.
2013-02-26 21:37:41.003 Scheduled 758 items in 2.0 = 0.08 match + 1.93 place

I checked on the ubuntu 12.10 server

ls -ld /storage/mythtv

drwxrwxr-x 13 mythtv mythtv 4096 feb 26 19:22 /storage/mythtv

Please Help ASAP, thanks.

It's a permissions issue, but you are checking the wrong server. Unless you set it up specifically, the UID of mythtv on both machines probably doesn't match. What is the permissions on /mnt/mythtv on the backend?

---

### Post by grunge09 on 2013-02-27
Yea that was it.  

Unmounted it was root:root user/group

I ran 

sudo chown -R mediabox:mythtv /mnt/mythtv

sudo umount /mnt/mythtv

sudo mount -a

unable to open live stream from frontend.  

ran 

ls -ld /mnt/mythtv
drwxrwxr-x 1 mediabox homelan 0 2011-08-02 08:10 /mnt/mythtv

thats when it struck me to check /etc/fstab

//192.168.0.99/mythtv /mnt/mythtv cifs credentials=/root/.smbcredentials,iocharset=utf8,uid=mediabox,gid=homelan,nounix,file_mode=0775,dir_mode=0775

I changed the gid=homelan to gid=mythtv then saved and exited gedit

ran  again....

sudo umount /mnt/mythtv

sudo mount -a

then one moretime ran...

ls -ld /mnt/mythtv
drwxrwxr-x 1 mediabox mythtv 0 2011-08-02 08:10 /mnt/mythtv

Re-ran frontend and Live TV works and recording works.  

I had to rsync a few recordings that were missing but its working now.

---

