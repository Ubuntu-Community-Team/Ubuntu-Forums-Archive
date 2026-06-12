---
title: "Script for video creation"
date: 2010-08-13
forum: Multimedia Software
---

### Post by rbishop on 2010-08-13
I have a script that I have set to run at the end of the day to pull a bunch of jpeg's into a short time lapse video.  The problem I am having is that when it runs at it's appropriate time it only creates a file of about 200K or so.  However if I run the script in the middle of the day from a command prompt it creates a file of about 12MB or so.....I am running this on an Ubuntu 10.04 server.  Here is the current script I have in place.....any help would be greatly appreciated.


```

#! /bin/bash

TD=$(date '+%m-%d')
cd /home/cam1/

ls > cam1.txt

mencoder mf://@/home/cam1/cam1.txt -nosound -mf w=320:h=240:fps=5:type=jpg -ovc xvid -xvidencopts bitrate=1600:vhq=2:bvhq=1:chroma_opt:quant_type=mpeg -o /home/user/$TD-cam1.avi

pause 100


```Thank you in advance for any and all help you can give me.

---

### Post by DaithiF on 2010-08-13
Hi, 
are you running this under cron?

put 
MAILTO=""
at the top of your cron file.

see [http://ubuntuforums.org/showthread.php?p=9625890](http://ubuntuforums.org/showthread.php?p=9625890)

---

### Post by rbishop on 2010-08-13
Yes I am running this under Cron.

---

### Post by DaithiF on 2010-08-13
> **rbishop said:**
> Yes I am running this under Cron.
and ... does my suggestion work?

---

### Post by rbishop on 2010-08-13
Sadly no it does not.  Any further thoughts?

---

### Post by DaithiF on 2010-08-14
can you post your crontab
thanks

---

### Post by rbishop on 2010-08-15
0 23 * * * /home/cam1/cam1             #Camera 1 Backup

---

### Post by DaithiF on 2010-08-15
can you add
```
 &> cam1.log
```
to the end of the mencoder line in your script to capture any stdout or stderr output

---

### Post by rbishop on 2010-08-15
I have added that to the end of my mencoder line and it now seems to spit out the correct size file.  I have set it up to run at it's normal time tonight.  I will let you know what I find out.  Thanks for your help on this one DaithiF

---

### Post by rbishop on 2010-08-16
Wow simply adding the output to a file actually worked.  Thanks for all the help.

---

