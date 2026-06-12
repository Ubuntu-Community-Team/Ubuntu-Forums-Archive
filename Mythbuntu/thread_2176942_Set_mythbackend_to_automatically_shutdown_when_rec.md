---
title: "Set mythbackend to automatically shutdown when recording is over"
date: 2013-09-26
forum: Mythbuntu
---

### Post by LastStarDust on 2013-09-26
Hello,
After a lot of pain I managed to setup acpi wake up for mythtv. I set the computer to boot at a certain time, autologin and start recording. I tested it and it does work.
Now, I'd like to make it automatically shutdown when recording is over, but I don't know how to achieve this.
I followed the guide at [http://www.mythtv.org/wiki/ACPI_Wakeup](http://www.mythtv.org/wiki/ACPI_Wakeup) with some arrangements (used rtcwake shell program). The checklogin.sh script is the very same, indeed.

Some info
No auto start mythfrontend at startup
ACPI Wake from state S5 (soft off)
Autologin at startup
Ubuntu 12.04 x86_64
MythTV 0.25

Thanks

---

### Post by harold95 on 2013-09-27
how about using the "AT" command? i'm pretty sure you can format the command to do a shut down at a specified time.
i'm sorry i can't give you the exact string, but look at the man page and you should have an idea of how to do it.

---

### Post by LastStarDust on 2013-09-27
> **harold95 said:**
> how about using the "AT" command? i'm pretty sure you can format the command to do a shut down at a specified time.
i'm sorry i can't give you the exact string, but look at the man page and you should have an idea of how to do it.

Thanks I'll give it a try. Do you know how I can get recording ending time from mythtv?

---

### Post by LastStarDust on 2013-09-29
I tried to shutdown through the post processing job that can be set for each recording.
I enabled job execution in backend-setup, but they seem not to be called.
I also tried to execute a very simple script as a job, but nothing happened.
This is job_1:
```
~/Desktop/job_1.sh %STARTTIME% %ENDTIME%
```
This is job_1.sh:
```
#!/bin/bash
touch /home/neo/Desktop/test
echo -e "STARTTIME =\t $1\n" >> ~/Desktop/test
echo -e "ENDTIME =\t $2\n" >> ~/Desktop/test
exit 0
```

---

### Post by khPWXxF on 2013-10-28
Will mythwelcome do what you want?  It works fine with Mythbuntu 12.04/Mythtv 0.25
I'm assuming you have a combined frontend/backend system.
See [http://www.mythtv.org/wiki/Mythwelcome](http://www.mythtv.org/wiki/Mythwelcome)
Phil

---

