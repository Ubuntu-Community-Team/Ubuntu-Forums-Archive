---
title: "K9Copy Woes."
date: 2008-09-25
forum: Multimedia Software
---

### Post by palu1 on 2008-09-25
Hi.. Odd one... Yes I too am a newbie to Ubuntu and hooked...  :-)

I am having problems with K9Copy... It randomly crashes.. when I launch it from terminal I get the error msg below.  
To me it appears I do not have the correct access to the tmp directory to write.  But when I try to change access I cant...  
How do I fix this one.
Thanks in advance for all your help.
PJ

paul@paul-laptop:~$ sudo k9copy
[sudo] password for paul:xxxxxxxxxxxxxxxxxxx
Error: "/tmp/kde-paulOe2Pt5" is owned by uid 1000 instead of uid 0.
Error: "/tmp/ksocket-paulS8pjS9" is owned by uid 1000 instead of uid 0.
Error: "/tmp/ksocket-paulS8pjS9" is owned by uid 1000 instead of uid 0.
Error: "/tmp/kde-paulOe2Pt5" is owned by uid 1000 instead of uid 0.
kbuildsycoca running...
Error: "/var/tmp/kdecache-paulPCmzm2" is owned by uid 1000 instead of uid 0.
Error: "/tmp/kde-paulOe2Pt5" is owned by uid 1000 instead of uid 0.
Error: "/var/tmp/kdecache-paulPCmzm2" is owned by uid 1000 instead of uid 0.
Error: "/var/tmp/kdecache-paulPCmzm2" is owned by uid 1000 instead of uid 0.
Error: "/tmp/kde-paulOe2Pt5" is owned by uid 1000 instead of uid 0.

---

### Post by firefly2442 on 2008-09-26
Try running it as just your user and not through sudo.

---

### Post by palu1 on 2008-09-26
I did... Thanks for the offer... 
When I do that, k9Copy just mysteriously closes.. No error or anything...

---

### Post by indytim on 2008-09-26
Somewhere in the K9Copy setup is provisions for the destination directory.  A couple of recommendations:

1.  Make sure that you have write access to the directory (folder).
2.  Make sure you're not size-constrained on the partition where the folder is located.
3.  Don't put any dvd iso's in FAT32 partitions (~4G maximum).

Hope one of these basics covers your problems.

IndyTim

---

### Post by carfinder01 on 2008-11-05
Im am also having the same problems yet i have used K9copy in the past successfully. I have enough space on the folder. What the program actually does is it starts backing up the media but like 20% through it just closes with no errors or prompts.
Any suggestions

---

### Post by carfinder01 on 2008-11-05
Im am also having the same problems yet i have used K9copy in the past successfully. I have enough space on the folder. What the program actually does is it starts backing up the media but like 20% through it just closes with no errors or prompts.
Any suggestions

---

