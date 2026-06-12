---
title: "Frontend Tuner Problems"
date: 2010-09-11
forum: Mythbuntu
---

### Post by tincansandtwine on 2010-09-11
Running MythTV .23 on Ubuntu 10.04, Zotac ION F-E mobo, Hauppauge 2250 tuner.

The message I am getting is "MythTV is using all inputs, but there are no active recordings?".  After restarting the backend, everything works fine, but this it has to be restarted after every reboot.  The general consensus seems to be that this error is caused by the backend starting before the tuners are initialized.  I resolved this issue by following the post [here]("http://ubuntuforums.org/showthread.php?t=1345079"), but the error persists.  The log I get after changing the mythtv-backend.conf file is

```
: Mythtv-backend Upstart; MySQL is not ready. Waiting 1 second...
: Mythtv-backend Upstart; MySQL is now ready
: Mythtv-backend Upstart; MySQL is now ready
: Mythtv-backend Upstart; MySQL is now ready
: Mythtv-backend Upstart; MySQL is now ready
: Mythtv-backend Upstart; tuners found in database: /dev/dvb/adapter0/frontend0
/dev/dvb/adapter1/frontend0
: Mythtv-backend Upstart; tuner device /dev/dvb/adapter0/frontend0 is now ready
: Mythtv-backend Upstart; tuner device /dev/dvb/adapter1/frontend0 is now ready
: Mythtv-backend Upstart: tuner devices are now registered. Starting mythbackend
```

I have confirmed that the backend does start after the script runs, so now I am at a loss for what is giving me the error.  Any ideas?  Thanks in advance.


Edit: So I took a look at the mythbackend.log and I get this

```
2010-09-11 09:21:25.451 New DB connection, total: 2
2010-09-11 09:21:25.488 Connected to database 'mythconverg' at host: localhost
2010-09-11 09:21:25.549 DVBChan(1:/dev/dvb/adapter0/frontend0) Warning: Opening DVB frontend device failed.
			eno: No such file or directory (2)
2010-09-11 09:21:25.575 DVBChan(1:/dev/dvb/adapter0/frontend0) Error: Failed to open DVB frontend device due to fatal error or too many attempts.
2010-09-11 09:21:25.591 DVBChan(2:/dev/dvb/adapter1/frontend0) Warning: Opening DVB frontend device failed.
			eno: No such file or directory (2)
2010-09-11 09:21:25.597 DVBChan(2:/dev/dvb/adapter1/frontend0) Error: Failed to open DVB frontend device due to fatal error or too many attempts.
2010-09-11 09:21:25.608 MythBackend, Error: No valid capture cards are defined in the database.
			Perhaps you should re-read the installation instructions?
2010-09-11 09:21:25.649 New DB connection, total: 3
```

So it looks like even though the new script makes sure the tuners are loaded, the backend still isn't finding them.


Edit 2: Delayed backend start by 10 seconds, now I get Permission Denied as the reason for failing to open DVB device 0, still says "No such file or directory" for DVB adapter 1.  Going to try re-adding the device to mythbackend.

---

### Post by ian dobson on 2010-09-11
Hi,

What rights do your dvb devices have? ls /dev/dvb/ -o

I've written a small script that checks the configuration of the MythTV database. Maybe it'll help you find the problem. A download is available from my site.

Regards
Ian Dobson

---

### Post by tincansandtwine on 2010-09-11
> **ian dobson said:**
> Hi,

What rights do your dvb devices have? ls /dev/dvb/ -o

I've written a small script that checks the configuration of the MythTV database. Maybe it'll help you find the problem. A download is available from my site.

Regards
Ian Dobson

Output from ls /dev/dvb/ -o

```
total 0
drwxr-xr-x 2 root 120 2010-09-11 09:49 adapter0
drwxr-xr-x 2 root 120 2010-09-11 09:49 adapter1

```

Does this mean mythbackend doesn't have rights to the tuners?  I don't know if that makes sense, since restarting the backend fixes the problem.  I'll download the the script from your site now...

Edit: Output from CheckMythDB.pl:

```
[--].No command line options defined trying mysql.txt
[--].Try ./CheckMythDB.pl -H for help
[--].Looking for Database information in /usr/local/share/mythtv/mysql.txt
[--].Looking for Database information in /usr/share/mythtv/mysql.txt
[--].Looking for Database information in /etc/mythtv/mysql.txt
[--].Found configuration file /etc/mythtv/mysql.txt
[--].Looking for Database information in /usr/local/etc/mythtv/mysql.txt
[--].Looking for Database information in /home/htpc/.mythtv/mysql.txt
[--].Found configuration file /home/htpc/.mythtv/mysql.txt
[--].Looking for Database information in mysql.txt
[--] Using HostName 'htpc-desktop', DatabaseHost 'localhost', SQLUserName 'mythtv', SQLPassword 'uE8tRnb3'
[--].Checking configuration for host 'htpc-desktop'
[OK].Found 1 video sources
[OK].Videosource 1 'Schedules Direct' has a EPG source defined (schedulesdirect1)
[OK].Videoinput 1 has 3 card inputs defined
[--].Checking start channel for each cardinput
[--].Checking channel change script for each cardinput
[OK].All InputCards are linked to a videosource
[OK].Videosource 1 has 41 visible and 0 invisible channels defined
[OK].cardinput 1 type DVB exists as device in /dev, file permissions are 0660 (rw- rw- ---) owner (root) group (video)
[OK].cardinput 2 type DVB exists as device in /dev, file permissions are 0660 (rw- rw- ---) owner (root) group (video)
[OK].cardinput 3 type DVB exists as device in /dev, file permissions are 0660 (rw- rw- ---) owner (root) group (video)
[OK].All channels have a valid videosource
[OK].All dtv_multiplex channels have a valid videosource
[OK].All channel entries have a valid dtv_multiplex
[OK].All dtv_multiplex entries have a valid channel
[OK].Found 9 storage groups for 'htpc-desktop'
[OK].Storage group 'Default' exists in file system at (/var/lib/mythtv/recordings/)
[OK].Storage group 'Videos' exists in file system at (/var/lib/mythtv/videos/)
[OK].Storage group 'Fanart' exists in file system at (/var/lib/mythtv/fanart/)
[OK].Storage group 'Trailers' exists in file system at (/var/lib/mythtv/trailers/)
[OK].Storage group 'Coverart' exists in file system at (/var/lib/mythtv/coverart/)
[OK].Storage group 'Screenshots' exists in file system at (/var/lib/mythtv/screenshots/)
[OK].Storage group 'Banners' exists in file system at (/var/lib/mythtv/banners/)
[OK].Storage group 'DB Backups' exists in file system at (/var/lib/mythtv/db_backups/)
[OK].Storage group 'LiveTV' exists in file system at (/var/lib/mythtv/livetv/)
Can't use string ("0") as an ARRAY ref while "strict refs" in use at ./CheckMythDB.pl line 391.

```

---

### Post by ian dobson on 2010-09-11
Hi,

Looking at the output of my script:-
```
[OK].cardinput 1 type DVB exists as device in /dev, file permissions are 0660 (rw- rw- ---) owner (root) group (video)
[OK].cardinput 2 type DVB exists as device in /dev, file permissions are 0660 (rw- rw- ---) owner (root) group (video)
[OK].cardinput 3 type DVB exists as device in /dev, file permissions are 0660 (rw- rw- ---) owner (root) group (video)
```

Your tuners have the correct permissions (group video rw) and mythtv usually is in the group video.

Also you seem to have found a small bug in the script (Can't use string ("0") as an ARRAY ref while "strict refs") but I don't think thats a reasone why your tuners don't work.

I'll have a look at my code to see what could cause such an error.

EDIT: OK the error is caused my not having a recordings defined, I'll make a patch sometime for it. The script is trying to scan an array of the programs recorded but as the array is empty perl is blowing a fit.

EDIT2: OK script fixed, it's just a one liner. New version uploaded to my web page.

Regards
Ian Dobson

---

### Post by tincansandtwine on 2010-09-11
Possible noob question: why is it saying I have three tuners when I only have two (the two tuners of the 2250 card)?

---

### Post by ian dobson on 2010-09-11
Hi,

Do you have multirec (recording several programs from the same multiplex) enabled for one of your tuners? I imagine you have multirec enabled on one of your tuners.

On my backend I have 2 DVB tuners and have multirec enabled (2 recordings per tuner) and see 4 tuners in my script.

Regards
Ian Dobson

---

### Post by tincansandtwine on 2010-09-11
> **ian dobson said:**
> Hi,

Do you have multirec (recording several programs from the same multiplex) enabled for one of your tuners? I imagine you have multirec enabled on one of your tuners.

On my backend I have 2 DVB tuners and have multirec enabled (2 recordings per tuner) and see 4 tuners in my script.

Regards
Ian Dobson

I believe I do have that enabled.  Is that a problem?  I don't think the tuner can handle two recordings per tuner.  I noticed that and left it, figuring I could change it if it became a problem.

---

### Post by ian dobson on 2010-09-11
Hi,

No it's not a problem, using multirec allows mythtv to record several programs from the same multiplex at the same time.

Can you try deleting all your tuners and recresting them. Maybe mythtv-setup screwed up the configuration. Can you also try a channel scan after recreating your tuners.

Regards
Ian Dobson

---

### Post by tincansandtwine on 2010-09-12
Just realized that I was running 23.0.  Updated to 23.1, and the issue was completely resolved, i.e., the mythbackend.conf didn't even need to be modified, it just worked in its original form.  Myth always finds the backend, and the tuners are always available.  Now all I need is VDPAU to work right without stuttering like mad.

---

