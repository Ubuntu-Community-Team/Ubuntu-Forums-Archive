---
title: "Standby/resume from standby"
date: 2008-10-01
forum: Mythbuntu
---

### Post by alexeix on 2008-10-01
Hi,

I'd like to make my Mythbuntu PC go into standby, so I don't have to leave it switched on all the time, and for it to resume to make scheduled recordings.

I have a Shuttle SN95G5v2 and it allows the PC to 'suspend', however, I can't find a Power option in the Mythbuntu menu, so I have to exit Mythbuntu in order to put my PC into suspend mode - meaning that it doesn't start up again automatically.

Is Mythbuntu able to do this and can anyone advise what I need to do?
Thanks!

---

### Post by SiHa on 2008-10-01
Try this thread.
[http://ubuntuforums.org/showthread.php?t=702310](http://ubuntuforums.org/showthread.php?t=702310)
And the guide mentioned in the first post:
[https://help.ubuntu.com/community/MythTV/Install/WhatNext/ACPIWake](https://help.ubuntu.com/community/MythTV/Install/WhatNext/ACPIWake)

---

### Post by alexeix on 2008-10-01
Thanks for the quick response.

I thought it would be more straightforward, but it looks like it's a job for the weekend...

---

### Post by SiHa on 2008-10-01
Yes, the whole Hibernate / Auto Wake think is a bit thorny from what I've seen. I've been putting it off until I've got the rest of the system sorted.
I cleared the last hurdle tonight, so It looks like I'm going to have to delve in soon as well...
Watch this space!

---

### Post by eddypolak on 2008-10-02
As an Ubuntu novice I can recommend the tutorial at
 [https://help.ubuntu.com/community/MythTV/Install/WhatNext/ACPIWake](https://help.ubuntu.com/community/MythTV/Install/WhatNext/ACPIWake)

This recipe works even if like me you have little idea what some of it actually means! So don't be put off if it looks daunting. It is hard to spot any mistakes you might make so be really careful, using cut-and-paste where possible.

Having said it works, I do have one sleep/wake issue with my combined frontend/backend system. Having set a recording and quit the frontend the system will sleep after the backend times out. When it wakes the system goes as far as the logon dialog -which is fine for the recording as the Myth backend is running at that point. The problem now is that the backend timout will not work. Paradoxically you have to logon and then it will.

Now I could swear that when I first got the system running this logon dialog did not appear and you went directly from power-on to the desktop. Maybe I'm kidding myself though...I have tried fiddling around with options relating to logon and sessions but nothing so far has helped. Ideas anyone?

---

### Post by SiHa on 2008-10-02
Isn't autologon an option in MCC? Perhaps it got unchecked by mistake.

---

### Post by eddypolak on 2008-10-03
Ah, thanks for getting me on the right track! I thought that option was just to autostart the frontend. As a running a frontend stops the machine going to sleep via Mythbuntu inactivity timeout I had unchecked it. Now that I have restored auto logon I soon found how to stop the frontend autostarting by deleting the MythTV Frontend file found in /home/'my_username'/.config/autostart.

---

### Post by alexeix on 2008-10-05
> **eddypolak said:**
> As an Ubuntu novice I can recommend the tutorial at
 [https://help.ubuntu.com/community/MythTV/Install/WhatNext/ACPIWake](https://help.ubuntu.com/community/MythTV/Install/WhatNext/ACPIWake)

This recipe works even if like me you have little idea what some of it actually means! So don't be put off if it looks daunting. It is hard to spot any mistakes you might make so be really careful, using cut-and-paste where possible.


Thanks for the link.

At step 1.1, my system returned /proc/acpi/alarm, so does this mean I can skip to step 1.5?

---

### Post by alexeix on 2008-10-23
I've carried on with the changes from [https://help.ubuntu.com/community/MythTV/Install/WhatNext/ACPIWake](https://help.ubuntu.com/community/MythTV/Install/WhatNext/ACPIWake) and everything was looking good up to the 'Another Test' section.

However, when I typed...

sudo mythbackend &

the  text below was displayed (unexpectedly).  I use a dual tuner card and it works fine, so does anyone know why this problem occurred?

Furthermore, I'm not sure if my system clock is UTC.  I'm in the UK and we are currently on BST, which is GMT+1.  The BIOS clock says (e.g.)
21:25, whereas it is actually 22:25.
I only have Mythbuntu on this PC.

Any advice?  I get the feeling I'm nearly there...!
Thanks.

alex@alex-mythbuntu:~$ sudo mythbackend &
[1] 7151
alex@alex-mythbuntu:~$ 2008-10-23 22:03:40.084 Using runtime prefix = /usr
2008-10-23 22:03:40.085 Empty LocalHostName.
2008-10-23 22:03:40.085 Using localhost value of alex-mythbuntu
2008-10-23 22:03:40.094 New DB connection, total: 1
2008-10-23 22:03:40.099 Connected to database 'mythconverg' at host: localhost
2008-10-23 22:03:40.100 Closing DB connection named 'DBManager0'
2008-10-23 22:03:40.101 Connected to database 'mythconverg' at host: localhost
2008-10-23 22:03:40.102 New DB connection, total: 2
2008-10-23 22:03:40.102 Connected to database 'mythconverg' at host: localhost
2008-10-23 22:03:40.104 Current Schema Version: 1214
Starting up as the master server.
2008-10-23 22:03:40.123 DVBChan(1:0) Error: Opening DVB frontend device failed.
			eno: Device or resource busy (16)
2008-10-23 22:03:40.124 DVBChan(2:0) Error: Opening DVB frontend device failed.
			eno: Device or resource busy (16)
2008-10-23 22:03:40.125 DVBChan(3:1) Error: Opening DVB frontend device failed.
			eno: Device or resource busy (16)
2008-10-23 22:03:40.126 DVBChan(4:1) Error: Opening DVB frontend device failed.
			eno: Device or resource busy (16)
ERROR: no valid capture cards are defined in the database.
Perhaps you should read the installation instructions?
QServerSocket: failed to bind or listen to the socket
2008-10-23 22:03:40.134 MediaServer::HttpServer Create Error
2008-10-23 22:03:40.134 mythbackend version: 0.21.20080304-1 [www.mythtv.org](www.mythtv.org)
2008-10-23 22:03:40.134 Enabled verbose msgs:  important general
2008-10-23 22:03:40.135 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
QServerSocket: failed to bind or listen to the socket
2008-10-23 22:03:40.137 Failed to bind port 6543. Exiting.

---

### Post by alexeix on 2008-10-25
Just wondering if anybody has any ideas on this?

Need to get my power on/off working by the end of the weekend.
Thanks.

---

### Post by SiHa on 2008-10-25
I've only just started to play with this, but if it helps - my RTC also seems to be set to GMT. when I do this:```
$ sudo sh -c 'echo "+00-00-00 00:05:00" > /proc/acpi/alarm'
```

then```
$ cat /proc/acpi/alarm
```

The time displayed is 5 minutes later than an hour ago, if you see what I mean.

However, the system will still wake up at the correct time.
I'll be insterested to see what happens after tonight (The clocks go back 1hr to GMT for those not in the UK!)

---

### Post by alexeix on 2008-11-08
Okay, if I set...

Server Halt=Server Halt Command: sudo shutdown -h -P now

...then the system shuts down, but only if the MythTV front-end is not running.

Is that how it's supposed to work?  I want to be able to use the computer to browse the web, email, etc., as well as PVR functions. 

Is there a way to do this?

---

### Post by spoky99 on 2008-11-09
> **SiHa said:**
> I've only just started to play with this, but if it helps - my RTC also seems to be set to GMT. when I do this:```
$ sudo sh -c 'echo "+00-00-00 00:05:00" > /proc/acpi/alarm'
```

then```
$ cat /proc/acpi/alarm
```

The time displayed is 5 minutes later than an hour ago, if you see what I mean.

However, the system will still wake up at the correct time.
I'll be insterested to see what happens after tonight (The clocks go back 1hr to GMT for those not in the UK!)

Is a strange thing..
the time written into the bios clock is the "Universal Time Coordinated" the kernel of your machine wen come up change the UTC into your time (correct it to the GMT), and if you "cat" the time into your bios yo see the time correct. Using echo etc etc you sum 5 minutes at your time in the moment that you execute the command.
The strange thing is not that your clock is 5 minutes after, but that you see the UTC and not your real time.
Question... but if you shutdown the computer it come up itself after 5 minutes?

---

### Post by SiHa on 2008-11-09
> **spoky99 said:**
> 
Question... but if you shutdown the computer it come up itself after 5 minutes?

It certainly does.

I've not had a chance to play since then, so that's as far I as I got.

---

### Post by alexeix on 2008-11-12
> **alexeix said:**
> Okay, if I set...
Server Halt=Server Halt Command: sudo shutdown -h -P now
...then the system shuts down, but only if the MythTV front-end is not running.
Is that how it's supposed to work?  I want to be able to use the computer to browse the web, email, etc., as well as PVR functions. 
Is there a way to do this?

I still haven't figured this out.  Success seems to be a bit hit and miss, for example, I set MythTV to record something before leaving this morning and then exited the MythTV Frontend, leaving the PC to go into standby on its own a few minutes later.

However, when I got home tonight, the PC hadn't started up to record.

Any suggestions what might be going wrong?

---

