---
title: "Won't record even though guide data and schedules exist"
date: 2007-12-03
forum: Mythbuntu
---

### Post by nimda79 on 2007-12-03
Either in the frontend or on mythweb I don't see any upcoming recordings. I have alot of things set to record but it doesn't. I even selected an item from the guide and it doesn't record. Please Help!
Running 7.10 of mythbuntu x64.

---

### Post by kevinatkins on 2007-12-03
Hmm, strange. Only thing I can suggest is to check your PC clock - is it correct?

---

### Post by ubnewbie2 on 2007-12-03
Are the programs that you have set to record, listed on the schedule page under mythweb?

---

### Post by nimda79 on 2007-12-03
Yes they are on the Recording Schedules but is blank in upcoming recordings. I already checked the time and date, and it's fine. Like a said I can't even record what's currently playing. It's like the backend just went haywire.

---

### Post by ubnewbie2 on 2007-12-03
What about disk space?  I've seen it fill up with logs, for example.

Does live tv still work (because that has to be able to record in order to be able to pause and rewind)?

---

### Post by nimda79 on 2007-12-03
Yes live tv w/ timeshifting still work, it has like 120GB of free space left on the drive.

---

### Post by ubnewbie2 on 2007-12-03
Try a repair on the database tables.

(a quick google should find instructions)

---

### Post by nimda79 on 2007-12-04
Well I ran "sudo mysqlcheck -r -e --all-databases" and still not working, what table in the database houses the upcoming recordings? I have Webmin installed and I can browse the database to see if there is anything in there.

---

### Post by ubnewbie2 on 2007-12-04
I'm sorry but I am fairly unfamiliar with the database structure myself.  However there is some explanation of the scheduler here

[http://www.mythtv.org/wiki/index.php/Scheduler](http://www.mythtv.org/wiki/index.php/Scheduler)

and the database schema here

[http://www.mythtv.org/wiki/index.php/Database_Schema](http://www.mythtv.org/wiki/index.php/Database_Schema)

---

### Post by uopjohnson on 2007-12-04
Are your listings connected to a tuner?  
You do this in step three of the mythtv-setup.  Each Tuner needs to be connected to a listing. 
This would allow live TV to work and not recording.  When you watch live TV does the EPG show up with the correct name of the show you are watching? In mythweb do you see each sheduled recording with a number next to it?  Or with a letter.  The letters are error codes, numbers are tuners.

---

### Post by uopjohnson on 2007-12-04
also.  Has this worked before now and just quit on you?  Or has it never worked?

---

### Post by nimda79 on 2007-12-04
> **uopjohnson said:**
> also.  Has this worked before now and just quit on you?  Or has it never worked?

This has been working and stopped working after the 30th of November. I'll check the rest in 45 min when I get off work

---

### Post by nimda79 on 2007-12-04
> **uopjohnson said:**
> Are your listings connected to a tuner?  
You do this in step three of the mythtv-setup.  Each Tuner needs to be connected to a listing. 
This would allow live TV to work and not recording.  When you watch live TV does the EPG show up with the correct name of the show you are watching? In mythweb do you see each sheduled recording with a number next to it?  Or with a letter.  The letters are error codes, numbers are tuners.

They are connected to a tuner
EPG does show up and is correct.
It does not show anything in upcoming which is where you would see the number or error code.

---

### Post by uopjohnson on 2007-12-05
OK.  Why don't you try tunning mythfilldatabase manually form the terminal.  This may give you some error indication when it is complete.  Are you logging events to the database?  There is a setting for that in setup->general I think.  You should also check the backend logs they are in /var/log/.  If you are logging all events you can see those in mythweb. 
Sorry to be so general, but I'm at work. 
Let me know what you discover.

---

### Post by ghuber on 2007-12-09
I had the same problem today.

I fixed it by first running

> sudo mysqlcheck -r -e --all-databases

I noted that it found a error and fixed it.

The recordings still were not back so I ran

> mythfilldatabase

When that completed all the upcoming recordings had returned and the box began to record shows again.

The combo of the two fixed it for me.

---

### Post by usererror on 2009-06-19
I have this same issue now.  I tried the steps from above and I get the following at the very end:

```

ICE Default IO error handler doing an exit(), pid = 5631, errno = 32
```

that's at the end of mythfilldatabase

the backend logs from the mythweb keeps saying that it started as slave?  I don't know how it did that, since this has always been the master backend.

but even mythfilldatabase says

```

2009-06-19 12:10:07.392 Connecting to backend server: 192.168.13.50:6543 (try 1 of 5)
```

which is its own IP!

EDIT: I think I found my problem. I ran mythtv-setup and under general the two IP addresses were different, the first one was localhost, the 2nd was its LAN IP.  I made them both the LAN IP.  Now the server shows as starting as a master backend in the backend logs listed in mythweb.

---

