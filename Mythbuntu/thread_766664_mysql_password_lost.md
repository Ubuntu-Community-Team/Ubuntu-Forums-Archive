---
title: "mysql password lost"
date: 2008-04-25
forum: Mythbuntu
---

### Post by Verlager on 2008-04-25
Previously I experimented with Zenwalk, a Slackware distro, installing and setting up mythbuntu. Now I understand ubuntu variants are better supported here. Good!  

I am using Linux Mint 4.0 and a Plextor ConvertX PX-402U. I have installed the wis-go7007-linux-0.9.8-patched.tar.bz2 driver and the command: 
[COLOR="DarkGreen"]gorecord -input 0 -duration 20 test-video.avi[/COLOR] records fine.

But I get this error message when I run: [COLOR="DarkGreen"]**sudo dpkg-reconfigure mythtv-database**
[/COLOR]
rmack@teasel:~$ **sudo dpkg-reconfigure mythtv-database**
Failed to connect to database: Can't connect to MySQL server on 'teasel' (111) at -e line 5, <> line 1.
Failed to create database (incorrect admin username/password?)
It's also possible that mysql-server wasn't running.  After install
is completed, you will need to make sure mysql-server is running
and that you supplied correct information. Try:
sudo dpkg-reconfigure mythtv-database
rmack@teasel:~$

Also, I changed the name from 'localhost' to 'teasel' to be more accurate.

---

### Post by volkswagner on 2008-04-25
Mysql default install has blank password for root user.  If you already set a password and forgot it, you will need to reset it.  I cant post links, but google can help here.  In my experience localhost works best on the machine hosting mysql.  All other machines shall point to it's ip.  Can you log into mysql via terminal?  
mysql -u root 
or
mysql -u root -p

if you changed the password for Mythtv user you will need to tell mysql via mysqladmin

---

### Post by oscarsfriend on 2008-04-25
Your mysql username and password (for mythtv) can probably be found in /etc/mythtv/mysql.txt (or at least they are under a usual ubuntu install + mythtv from repos).  Also, if that is not your problem, are you sure mysql-server was running in the first place? (Try pgrep -lf mysql.)  Also, make sure your /etc/hosts includes a line like: 127.0.0.1 localhost teasel.

---

### Post by Verlager on 2008-04-25
I found the password for MySQL.

```
rmack@teasel:~$ sudo mythtv-setup
[sudo] password for rmack:
Stopping MythTV server: mythbackend No /usr/bin/mythbackend found running; none killed.
.
Restarting MythTV server: mythbackend No /usr/bin/mythbackend found running; none killed.
.
.
rmack@teasel:~$ sudo mythtv-setup
Stopping MythTV server: mythbackend No /usr/bin/mythbackend found running; none killed.
.
Restarting MythTV server: mythbackend No /usr/bin/mythbackend found running; none killed.
.
.
rmack@teasel:~$ 

```

When I run mythTV front end, it runs the mySQL configuration tool and throws an error. Do I have to use such a modern interface? Isn't there one which uses a mouse, the way the other X-windows applications do? Not complaining, but the interface just gets in the way.

---

### Post by Verlager on 2008-05-04
I think I'm going to set this project on hold for a few weeks. For now I can capture and record video output manually from my DVR with a shell script I wrote, 'record.sh'. Avoids the overhead of MythTV, and CPU usage is low. But I want to set up a dedicated mythbox soon!

_Comments on the script and suggestions are welcome._

usage: (use no input filename suffix) ***record.sh {filename} {time_in_minutes}***
Example: **record.sh output 10** # records 10 min. of streaming video to 'output.avi' 
Example: **record.sh "The Bounty" 132** # records 132 min. of streaming video to 'The Bounty.avi' 

```

#!/bin/bash
bitrate=1750;
mode=ntsc
#format=mpeg2-dvd
format=mpeg2
duration=`expr $2 \* 60`
input=0

gorecord -input $input -duration $duration -bitrate $bitrate -mode $mode -format $format $1.avi
```

---

### Post by jnorth on 2008-05-07
> **Verlager said:**
> I think I'm going to set this project on hold for a few weeks. For now I can capture and record video output manually from my DVR with a shell script I wrote, 'record.sh'. Avoids the overhead of MythTV, and CPU usage is low. But I want to set up a dedicated mythbox soon!

_Comments on the script and suggestions are welcome._

usage: (use no input filename suffix) ***record.sh {filename} {time_in_minutes}***
Example: **record.sh output 10** # records 10 min. of streaming video to 'output.avi' 
Example: **record.sh "The Bounty" 132** # records 132 min. of streaming video to 'The Bounty.avi' 

```

#!/bin/bash
bitrate=1750;
mode=ntsc
#format=mpeg2-dvd
format=mpeg2
duration=`expr $2 \* 60`
input=0

gorecord -input $input -duration $duration -bitrate $bitrate -mode $mode -format $format $1.avi
```

Script looks good to me, what I';d like to know is how you got the convertx working!  I've checked out your other post with the links to the nikosapi page and the other thread in this forum, but for the life of me I can't get past the "Driver loaded but no GO7007 devices found. Is the device connected properly?" message when trying to use gorecord, much less get it set up in mythtv.
I'm running on an apple mac mini, which shouldn't matter as it's intel based.  Sheesh!

Any advice on how you got this far?

Thanks!

---

