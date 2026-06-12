---
title: "Innodb as default database engine"
date: 2008-10-27
forum: Mythbuntu
---

### Post by Valen00 on 2008-10-27
I'm sick of repairing tables and rebuilding recordedseek tables.
myisam sucks in terms of sustaining a power fail event. Basically come the first blackout I loose some table or another and its really not intuitive for somebody who isn't really "into" the backend of things to fix.

(like say my dad who just wants to watch tv)

Anyway, this problem often manifests in the recordedseek table and shows up to the end user as the inability to skip and fast forward or rewind at greater than 5x will cause the player to die and drop back to the main menu.

Nothing apears in the mythfrontend or backend logs when this happens just to make life interesting.

the "fix" is to login to mysql then repair the table in question

mysql
use mythconverg;
repair table recordedseek;

stuff recorded from then on will fast forward and rewind properly

to fix the broken recordings

```
find /var/lib/mythtv/recordings -iname "*.mpg"  -atime -4 -print0 | xargs -0 -n1 mythcommflag --rebuild --file
```

should do the job. Its fairly quick, a few minutes per hour of recorded data, its IO bound on a P4 3ghz, probably best not to do it whilst watching a recording, but a DVD is fine.

To prevent all this hassle in the future I suggest that mythbuntu move to using the innodb engine as the default rather than the myisam that myth ships with, yes it does use 10mb more disk space, but its far more reliable. (and really who cares about 10mb of disk space)

to convert an existing myth instillation to innodb rather than myisam 

```

for t in $(mysql --batch --column-names=false -e "show tables" mythconverg |grep -v "exclude_this");
do
mysql -e "alter table $t type=InnoDB" mythconverg;
done

```

I run this on all the myth boxes I have out there currently and have no problems with it.

---

### Post by uopjohnson on 2008-10-27
You should post this in launchpad as a sugestion.  Or file it as a bug with mythtv.org.  I think there are some performance gains on large dataset with myisam especialy with frequent read/in-frequent write, but it may not justify sticking with the format.  
I don't think mythbuntu wants to make that kind of change that could lead to some very difficult-to-track-down bugs in the future, but give it a try in launchpad.

---

### Post by ian dobson on 2008-10-28
Hi,

I've been runnning MythTV for about 11months now, and I've never seen the problems your describing. If your system (OS/Hardware) is unstable you should look at fixing that rather than fighting the symptoms.

Regards
Ian Dobson

---

### Post by Valen00 on 2008-10-28
The system is stable, it has a 15 minute UPS on it as well, unfortunately there are blackouts longer than that and if its recording when that happens then theres a good chance of it dying.

I have had this problem 4 or 5 times with 3 years of mythtv in 3 installs.

The problem is myISAM isn't "safe", a power fail or the like and the table is corrupt. Thats the reason mysql was looked at as a toy database for a fair while, with the addition of innodb table type then you get an ACID compliant database with the sole change being type=innodb rather than type=myisam

As for database load mythtv is so light that sqlite would do the job handily (well except for the working over a network thing ;->). 
it has like 1 query per second tops?
when isam was created it was better in terms of large datasets but innodb has caught up now, and surpasses isam when there is any concurrency.

I was thinking that the conversion could perhaps be a tick box in the mythtv wizard, I doubt upstream would care much, but I'll try I spose.
They wont want to break compatibilty with people who config mysql to not start innodb I'd guess although it'd only matter on a new install.

---

### Post by laga on 2008-10-28
> 
As for database load mythtv is so light that sqlite would do the job handily (well except for the working over a network thing ;->).
it has like 1 query per second tops

The scheduler query uses lots of ressources and sqlite doesn't cut it there. The MythTV developers are planning to move to embedded MySQL eventually, but there's no ETA on it AFAIK.

---

### Post by mrand on 2008-10-28
> **Valen00 said:**
> The system is stable, it has a 15 minute UPS on it as well, unfortunately there are blackouts longer than that and if its recording when that happens then theres a good chance of it dying.Howdy,

While a more corrupt-resistant database would be nice, you'd still be playing with fire by not shutting down the computer when the UPS gets low.  There are many files potentially at risk when powering a computer off without shutdown - a corrupted database could be the least of your concerns.

The proper solution is to have the computer auto-shutdown based upon status from the UPS.  Yes, it costs money.  And just like a good power supply, it's worth it!

Have fun,

[INDENT]   Marc[/INDENT]

---

### Post by Valen00 on 2008-10-30
I have a UPS however its USB only and won't play nice with linux.

I had the exact same problem today on my main machine actually (different machine to the one that prompted the post), this time it looks like a hardware problem caused some kind of lockup.
Still responded to ping etc but not to any kind of other input, needed a reset to wake it up, first time thats happened, but today is a stinking hot day, I'll be looking into this.

I'm not saying that software should be made to fix hardware problems. However when people are doing "important" jobs they use the innodb table type for a reason. There is an ACID compliant engine sitting 4 keystrokes away, why not use it. My mail system (dbmail) is sitting on the same system and it came back up fine, it has 12GB worth of mail in it and it was in use at the time of the crash. Mythtv was reccording one show, corrupted the seektable yet again. (turns out I hadn't set it to innodb after the last re-install (again due to a corrupt database))

---

### Post by mrand on 2008-10-30
> **Valen00 said:**
> I have a UPS however its USB only and won't play nice with linux.
I'm curious - what brand is it that doesn't play nice?  I'd like to make sure I avoid it, because there are plenty of USB-based devices that do work with nut: [http://eu1.networkupstools.org/compat/]("http://eu1.networkupstools.org/compat/")

> Still responded to ping etc but not to any kind of other input, needed a reset to wake it up, first time thats happened, but today is a stinking hot day, I'll be looking into this.It's weird that it would respond to ping, but you couldn't telnet to it.  I know that using Alt-SysReq-[REISUB] to reboot wouldn't guarantee no corruption, but I'd think that it would help at least a little - or is that blocked too?

> I'm not saying that software should be made to fix hardware problems. However when people are doing "important" jobs they use the innodb table type for a reason. There is an ACID compliant engine sitting 4 keystrokes away, why not use it. My mail system (dbmail) is sitting on the same system and it came back up fine, it has 12GB worth of mail in it and it was in use at the time of the crash. Mythtv was reccording one show, corrupted the seektable yet again. (turns out I hadn't set it to innodb after the last re-install (again due to a corrupt database))Again, I understand and agree that (more) corruption resistant databases are desirable.  I don't know enough about them to intelligently debate the tradeoff's - the last database system I worked with was dbase III!

[INDENT]Marc[/INDENT]

---

### Post by Valen00 on 2008-10-30
Its some generic peice of trash that i got from jaycar, powertech I believe? It might be able to work but i gave up after an hour and a half of mucking with it. I accidentally plugged a heater into one (twice) and both times the fuse holder actually melted itself until the wire fell off rather than blow the fuse. I have replaced the fuse and the holder with a more suitably rated one now. 

On the plus side, we just had 2 mini blackouts (.5 of a second or so) and it kept everything happy while that happened, even kept myth playing a video, guess the LCD has some good caps in it ;-> reset my desktop though (but its not on a UPS).

I think it was something related to the disk that caused the lockup, anything that would cause disk access was rooted. Might even be a software/driver problem. Ping was ok cos it didn't make it that far up the kernel, ssh was a no go. I'll have a look at hdd temps etc, theres a 1TB raid 0 array in there at the moment with a 100gb raid 5 partition that keeps my server virtual machine as well as a 500gb physical disk for the system and more recordings.

I went to the box physically and whilst it put a video signal out it was just a blank screen (IE DPMS turned off and it tried to paint myth)

I don't really see a downside to innodb, its memory and disk requirements are pretty minimal, its enabled by default its pretty much just plain ready to use ;->

If your feeling adventurous take a copy of your database
(if you have a default mythbuntu install)
mysqldump -u root mythconverg > mythtvbackup.sql

then run the conversion script (took my system about 25 seconds to convert)

and your done.

to roll back (you will loose access to recordings etc done since the conversion)
mysql -u root 
drop database mythconverg;
create database mythconverg;
quit;
mysql -u root mythconverg < mythtvbackup.sql

---

