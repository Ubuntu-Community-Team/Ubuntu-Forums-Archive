---
title: "Tuner problems Mythbuntu 8.4 to 10.4 upgrade, also possible database corruptio"
date: 2010-10-21
forum: Mythbuntu
---

### Post by drifting on 2010-10-21
Hi All.

Well I bit the bullet a couple of weeks back and tried an upgrade from 8.4 to 10.4. The downloading and upgrading seemed to go well. 
However, I find that the storage groups were still working, yet the backend config had no entries? Worse still was the tuners, I have a Nova-T 500 and two Nova-S, both of which seemed to tune ok, but flatly refused to record or play live TV, and under MythStatus page it showed no tuners?
I have bought over a few niggles from previous, one being the stack of tuners that it decided to number higher with each config, the upgrade just added even more numbers, but still showed the four as expected.

I had to revert to a backup to get it all back where it was, so any help with an upgrade would really be welcome.

I would dearly love to blat this server and do a clean install, but I understand there is a database upgrade within the process? Is there such a thing as an upgrade script for the database only? 

Regards Paul.

---

### Post by ian dobson on 2010-10-21
Hi,

I don't know if this would help, but I've written a perl script that checks the mythtv database configuration. I actually wrote it after helping a friend to recover his system after a failed update/data corruption.

You can download the code from my web site.

Other than that have a look at the log file from the backend (/var/log/mythtv/mythtvbackend.log)

Regards
Ian Dobson

---

### Post by drifting on 2010-10-23
Thanks Ian

I have downloaded the file :-

paul@vs:~$ sudo ./CheckMythDB.pl
[--].No command line options defined trying mysql.txt
[--].Try ./CheckMythDB.pl -H for help
[--].Looking for Database information in /usr/local/share/mythtv/mysql.txt
[--].Looking for Database information in /usr/share/mythtv/mysql.txt
[--].Found configuration file /usr/share/mythtv/mysql.txt
[--].Looking for Database information in /etc/mythtv/mysql.txt
[--].Found configuration file /etc/mythtv/mysql.txt
[--].Looking for Database information in /usr/local/etc/mythtv/mysql.txt
[--].Looking for Database information in /home/paul/.mythtv/mysql.txt
[--].Found configuration file /home/paul/.mythtv/mysql.txt
[--].Looking for Database information in mysql.txt
[--] Using HostName 'server', DatabaseHost '10.0.0.1', SQLUserName 'mythtv', SQLPassword 'qujaisoa'
[--].Checking configuration for host 'server'
[OK].Found 2 video sources
[OK].Videosource 1 'Freeview' has a EPG source defined (eitonly)
[OK].Videosource 2 'FreeSat' has a EPG source defined (eitonly)
[OK].Videoinput 1 has 4 card inputs defined
[OK].Videoinput 2 has 4 card inputs defined
[--].Checking start channel for each cardinput
[--].Checking channel change script for each cardinput
[OK].All InputCards are linked to a videosource
[OK].Videosource 1 has 9 visible and 1 invisible channels defined
[OK].Videosource 2 has 38 visible and 211 invisible channels defined
[--].cardinput 17 type DVB is not local to host 'server'
[--].cardinput 18 type DVB is not local to host 'server'
[--].cardinput 19 type DVB is not local to host 'server'
[--].cardinput 20 type DVB is not local to host 'server'
[--].cardinput 21 type DVB is not local to host 'server'
[--].cardinput 22 type DVB is not local to host 'server'
[--].cardinput 23 type DVB is not local to host 'server'
[--].cardinput 24 type DVB is not local to host 'server'
[OK].All channels have a valid videosource
[OK].All dtv_multiplex channels have a valid videosource
[OK].All channel entries have a valid dtv_multiplex
[--].59 dtv_multiplex entries do not have a valid channel
[OK].Found 1 storage groups for 'server'
[OK].Storage group 'Default' exists in file system at (/media/store/)
[!!].Storage group 'LiveTV' is used in the recorded database but it's not defined
Took 29 SQL queries


See what I mean about the tuners? I wonder if that was the reason why my upgrade failed? And that none of the tuners would do anything other than tune, not a recording or live TV in sight!



Paul

---

### Post by ian dobson on 2010-10-24
Hi,

Don't panic, it could well be that my script doesn't know how to look for your tuners/the actual error is that mythtv thinks the tuners are on a different server.

I've just uploaded a new version of the script that will display the host name that the tuners are linked to [http://www.planet-ian.com/MythTV/CheckMythDB.txt](http://www.planet-ian.com/MythTV/CheckMythDB.txt).

Have you changed the name of you server after/during the upgrade? You did run the script on the server didn't you?

Also if you run the script with the -a option it'll do alot more tests.

Regards
Ian Dobson

---

### Post by drifting on 2010-10-25
With the new script.

Something weird is going on, according to the backend I do not even have any tuners listed? Also to make matters worse there is only one storage group listed, when in fact I have 3 and they are all working? I just get this horrible feeling that my database is nailed.

Paul.


paul@vs:~$ sudo ./CheckMythDB.pl
[--].No command line options defined trying mysql.txt
[--].Try ./CheckMythDB.pl -H for help
[--].Looking for Database information in /usr/local/share/mythtv/mysql.txt
[--].Looking for Database information in /usr/share/mythtv/mysql.txt
[--].Found configuration file /usr/share/mythtv/mysql.txt
[--].Looking for Database information in /etc/mythtv/mysql.txt
[--].Found configuration file /etc/mythtv/mysql.txt
[--].Looking for Database information in /usr/local/etc/mythtv/mysql.txt
[--].Looking for Database information in /home/paul/.mythtv/mysql.txt
[--].Found configuration file /home/paul/.mythtv/mysql.txt
[--].Looking for Database information in mysql.txt
[--] Using HostName 'server', DatabaseHost '10.0.0.1', SQLUserName 'mythtv', SQLPassword 'qujaisoa'
[!!].Checking configuration for host 'server' but running on host 'vs' 
[OK].Found 2 video sources
[OK].Videosource 1 'Freeview' has a EPG source defined (eitonly)
[OK].Videosource 2 'FreeSat' has a EPG source defined (eitonly)
[OK].Videoinput 1 has 4 card inputs defined
[OK].Videoinput 2 has 4 card inputs defined
[--].Checking start channel for each cardinput
[--].Checking channel change script for each cardinput
[OK].All InputCards are linked to a videosource
[OK].Videosource 1 has 9 visible and 1 invisible channels defined
[OK].Videosource 2 has 37 visible and 206 invisible channels defined
[--].cardinput 17 type DVB is not local to host 'server' it's configured on host 'vs' 
[--].cardinput 18 type DVB is not local to host 'server' it's configured on host 'vs' 
[--].cardinput 19 type DVB is not local to host 'server' it's configured on host 'vs' 
[--].cardinput 20 type DVB is not local to host 'server' it's configured on host 'vs' 
[--].cardinput 21 type DVB is not local to host 'server' it's configured on host 'vs' 
[--].cardinput 22 type DVB is not local to host 'server' it's configured on host 'vs' 
[--].cardinput 23 type DVB is not local to host 'server' it's configured on host 'vs' 
[--].cardinput 24 type DVB is not local to host 'server' it's configured on host 'vs' 
[OK].All channels have a valid videosource
[OK].All dtv_multiplex channels have a valid videosource
[OK].All channel entries have a valid dtv_multiplex
[--].59 dtv_multiplex entries do not have a valid channel
[OK].Found 1 storage groups for 'server'
[OK].Storage group 'Default' exists in file system at (/media/store/)
[!!].Storage group 'LiveTV' is used in the recorded database but it's not defined
Took 29 SQL queries
paul@vs:~$

---

### Post by ian dobson on 2010-10-25
Hi,

OK it looks as if mythtv thinks the backend server is called server, but your hostname (as read from the script) is vs. If you look in your backend log do you see anything about attempting to connect to the master backend server?

Sort out your name problem and things might get better.

Regards
Ian Dobson

---

### Post by drifting on 2010-10-25
Hi Ian

Thanks for your input. Really odd not sure where it was getting the name "server" as this has never been called that, but rather "vs"

The odd part is that Myth is actually working, and has been for at least 3 years, will however as you suggest check the logs out.

Paul

---

### Post by drifting on 2010-10-25
Well I have spent an entire day and most of the night with this. I have cleared out the numbering of the tuners, and set it to default, I also on suggestion have checked and optimized the database.

End result :- No TUNERS !!

No idea why, nothing in the backend logs, crazy thing is they all tune fine, and populate the db with channels. But the front ends say they are unavailable.

At the is stage I am seriously thinking of wiping the whole machine and doing a clean install. 3 years of progams down the drain.

8.4 running 0.21.0+fixes21768-0ubuntu0+mythbuntu1

 


paul@vs:~$ sudo ./CheckMythDB.pl 
[--].No command line options defined trying mysql.txt
[--].Try ./CheckMythDB.pl -H for help
[--].Looking for Database information in /usr/local/share/mythtv/mysql.txt
[--].Looking for Database information in /usr/share/mythtv/mysql.txt
[--].Found configuration file /usr/share/mythtv/mysql.txt
[--].Looking for Database information in /etc/mythtv/mysql.txt
[--].Found configuration file /etc/mythtv/mysql.txt
[--].Looking for Database information in /usr/local/etc/mythtv/mysql.txt
[--].Looking for Database information in /home/paul/.mythtv/mysql.txt
[--].Found configuration file /home/paul/.mythtv/mysql.txt
[--].Looking for Database information in mysql.txt
[--] Using HostName 'server', DatabaseHost '10.0.0.1', SQLUserName 'mythtv', SQLPassword 'qujaisoa'
[!!].Checking configuration for host 'server' but running on host 'vs' 
[OK].Found 2 video sources
[OK].Videosource 1 'freesat' has a EPG source defined (eitonly)
[OK].Videosource 2 'freeview' has a EPG source defined (eitonly)
[OK].Videoinput 1 has 4 card inputs defined
[OK].Videoinput 2 has 2 card inputs defined
[--].Checking start channel for each cardinput
[!!].Cardinput (5) Start channel (Please add)invalid
[!!].Cardinput (6) Start channel (Please add)invalid
[--].Checking channel change script for each cardinput
[OK].All InputCards are linked to a videosource
[OK].Videosource 1 has 11 visible and 0 invisible channels defined
[OK].Videosource 2 has 52 visible and 0 invisible channels defined
[!!].cardinput 1 does not appear to exist as a device
[!!].cardinput 2 does not appear to exist as a device
[!!].cardinput 3 does not appear to exist as a device
[!!].cardinput 4 does not appear to exist as a device
[!!].cardinput 5 does not appear to exist as a device
[!!].cardinput 6 does not appear to exist as a device
[!!].cardinput 7 does not appear to exist as a device
[!!].cardinput 8 does not appear to exist as a device
[OK].All channels have a valid videosource
[OK].All dtv_multiplex channels have a valid videosource
[OK].All channel entries have a valid dtv_multiplex
[--].86 dtv_multiplex entries do not have a valid channel
[OK].Found 5 storage groups for 'server'
[OK].Storage group 'Default' exists in file system at (/media/store/)
[OK].Storage group 'Default' exists in file system at (/media/data/mythtv/)
[OK].Storage group 'Default' exists in file system at (/media/music/)
[OK].Storage group 'Default' exists in file system at (/media/video/recordings/)
[OK].Storage group 'DB Backups' exists in file system at (/media/video/dbb/)
[!!].Storage group 'LiveTV' is used in the recorded database but it's not defined


Need sleep, if anyone can help that would be really great.

Paul

---

### Post by rhpot1991 on 2010-10-26
Did you ever bother redoing the first step in mythtv-setup?  That is where the hostname will come from, which appears to be at least one of your issues here.

---

### Post by drifting on 2010-10-27
Resolved.

My problem was due to the host name being wrong in my home folder mysql.txt, running the setup made no difference, if it was not for ian's app I would have been running round like an idiot trying to fidn this.

I would like to thank everyone who has helped both here and on the IRC chat.

Regards Paul

---

### Post by ian dobson on 2010-10-27
Hi,

Glad your problem's solved. This should have been a bit tip:-

[!!].Checking configuration for host 'server' but running on host 'vs' 

Maybe I should put in a warning that if the hostname and the name from the mysql.txt file aren't the same, but I though this message is enough.

Regards
Ian Dobson

---

