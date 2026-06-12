---
title: "NFS doubles disk usage?"
date: 2010-07-22
forum: Networking &amp; Wireless
---

### Post by MartinHansell on 2010-07-22
A while back I set up NFS using [this guide]("https://help.ubuntu.com/community/SettingUpNFSHowTo"), and noticed that my disk usage increased dramatically.  I didn't bother about it at the time, but now it's causing me some bother!

Is it so that. if you install NFS and export using --bind, all the files are basically duplicated in the /export directory?

The instructions don't go as far as telling you how to undo this set-up, so I just deleted the /exports directory hoping that would do it.  Of course, I can no longer operate the intended shares, but the disk usage has remained the same. Yet when I check all the directories on the drive in question, I cannot find the rogue excess files anywhere!

Or maybe it's something totally unrelated?

Got any clues?
Thanks!
Martin

---

### Post by HHelsinger on 2010-08-01
I don't have a solution, but I have a related situation which may help identify the problem.   I dual boot windows/ubuntu.   The windows ntfs  partition has about 22 GB on it (Gparted says 21.43).   It is mounted at /media/windows.  Disk Usage Analyzer reports 21.3 GB of files in /media -- ALL 21.3 GB of which is /media/windows.  

Since all the windows files (stored on the Windows partition) are counted at part of /media, they are also counted as part of my ubuntu partition.  They have been counted twice.  As a result my 45 GB ubuntu partition reports 39 GB used, of which 22 GB are actually windows files. 

I believe this is because the windows partition is mounted in /media just as under NFS an exported /home/users directory is mounted in /export/users  (that comes from your link to NFS).  

Note that the man page for Mount says of the -bind option, that if:

>  fstab entry is:
                     /olddir /newdir none bind

              After  this  call the same contents is accessible in two places.

I guess it gets counted in two places also.

I imagine I could solve my problem by not mounting windows, but then how would I access those files?

---

### Post by MartinHansell on 2010-08-03
Thanks for your reply HHelsinger.  Yes I guess it's counted twice.  But I am trying to get rid of, and not sure how...  thanks again!

---

