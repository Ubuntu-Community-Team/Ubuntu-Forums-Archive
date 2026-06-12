---
title: "No guide data available in MythTV - Karmic"
date: 2009-11-28
forum: Multimedia Software
---

### Post by fimbar on 2009-11-28
Hi,

I've recently done a fresh install of Karmic and MythTV but I can't get any TV Guide Data pulled in. I'm using the EIT listings grabber, am based in the UK and am using a DVB-T card. Specifically a TDA10046H card.

Everything was working fine under both Intrepid and Jaunty but not so under Karmic. I've even wiped the OS drive and gone back and re-installed Jaunty just to see if I missed any steps and the guide data gets pulled in without issue. Using the exact same procedure for Karmic and I get no guide data.

Has anyone else seen this issue and/or know how to solve it?

I pulled in the channels using the channels.conf route if that makes any difference. I've also tried deleting all the channels, cards etc from within MythTV and re-setting everything up again but still no joy.

Oh, another thing......under Intrepid I could run the MythTV Backend Setup from the gnome menus but under Jaunty and Karmic I need to run it as sudo from a Terminal because it can't open my tuner card without sudo access. Could this be related (although under Jaunty the Guide Data came through fine?)

Many thanks guys.

---

### Post by hirnwurscht on 2009-11-28
Hello,

stop mythbackend
```
sudo /etc/init.d/mythtv-backend stop
```

Then run mythtvbackend with verbose output (eit)
```
sudo -u username mythbackend --verbose eit
```

replace username with the user that runs mythbackend (probably mythtv).

Wait a couple of minutes to see something or not.
Post the output.

---

### Post by fimbar on 2009-11-28
Hi and thanks for the reply.

That command has been running for hours and there was so much output it exceeded the Putty window buffer! I've killed it and re-ran it and pasted the top half of the output for you. Hopefully that's the interesting bit. If not let me know and I'll post some more.

I'm re-running it and am piping the output to a file so will get the whole thing as and when it finishes.

```
2009-11-28 19:55:16.941 mythbackend version: branches/release-0-22-fixes [22594] www.mythtv.org
2009-11-28 19:55:16.941 Using runtime prefix = /usr
2009-11-28 19:55:16.941 Using configuration directory = /home/ian/.mythtv
2009-11-28 19:55:16.942 Empty LocalHostName.
2009-11-28 19:55:16.942 Using localhost value of MediaServer
2009-11-28 19:55:16.944 New DB connection, total: 1
2009-11-28 19:55:16.946 Connected to database 'mythconverg' at host: localhost
2009-11-28 19:55:16.946 Closing DB connection named 'DBManager0'
2009-11-28 19:55:16.947 Connected to database 'mythconverg' at host: localhost
2009-11-28 19:55:16.948 Current MythTV Schema Version (DBSchemaVer): 1244
2009-11-28 19:55:16.948 MythBackend: Starting up as the master server.
2009-11-28 19:55:16.949 New DB connection, total: 2
2009-11-28 19:55:16.949 Connected to database 'mythconverg' at host: localhost
2009-11-28 19:55:18.215 New DB connection, total: 3
2009-11-28 19:55:18.215 Connected to database 'mythconverg' at host: localhost
2009-11-28 19:55:18.222 EITHelper: localtime offset 0:00:00
2009-11-28 19:55:20.475 New DB scheduler connection
2009-11-28 19:55:20.476 Connected to database 'mythconverg' at host: localhost
2009-11-28 19:55:20.485 Enabling Upnpmedia rebuild thread.
2009-11-28 19:55:22.035 Main::Registering HttpStatus Extension
2009-11-28 19:55:22.035 Enabled verbose msgs:  important general eit
2009-11-28 19:55:22.036 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2009-11-28 19:55:23.480 Reschedule requested for id -1.
2009-11-28 19:55:23.544 Scheduled 0 items in 0.1 = 0.00 match + 0.06 place
2009-11-28 19:55:23.545 Seem to be woken up by USER
2009-11-28 19:55:30.486 UPnpMedia: BuildMediaMap - no VideoStartupDir set,  skipping scan.
2009-11-28 19:56:18.495 EITScanner (1): StartActiveScan called with 6 multiplexes
2009-11-28 19:56:21.453 EITScanner (1): Now looking for EIT data on multiplex of channel 30
2009-11-28 19:56:21.453 EITCache: Pruning all entries that ended before UTC 2009-11-27T20:01:25
2009-11-28 19:56:21.453 EITCache: Deleting old cache entries from the database
2009-11-28 19:56:21.915 EITScanner (1): Started passive scan.
2009-11-28 19:56:40.545 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2009-11-28 20:01:29.495 EITScanner (1): Now looking for EIT data on multiplex of channel 9
2009-11-28 20:01:29.495 EITCache: Pruning all entries that ended before UTC 2009-11-27T20:06:33
2009-11-28 20:01:29.495 EITCache: Deleting old cache entries from the database
2009-11-28 20:01:30.027 EITScanner (1): Started passive scan.
2009-11-28 20:06:37.433 EITScanner (1): Now looking for EIT data on multiplex of channel 82
2009-11-28 20:06:37.433 EITCache: Pruning all entries that ended before UTC 2009-11-27T20:11:41
2009-11-28 20:06:37.433 EITCache: Deleting old cache entries from the database
2009-11-28 20:06:37.904 EITScanner (1): Started passive scan.


```

---

### Post by hirnwurscht on 2009-11-28
"That Command" is your mythtv-backend ...
I should have said "a couple of minutes UNTIL you see something related to EIT", sorry.


But it seems that it gets the EIT data OK.

Are you really sure that you activated EIT in mythtv-setup (Video-Sources / source / only EIT)?

Since you also got permission issues, post the output of 
```
ls -lh /dev/dvb*
```

I just remembered what i read somewhere on the mythtv user list, iirc mythtv has NO problems when you do the channel-scan in mythtv-setup.

Eventualy a rescan in mythtv-setup does the trick?

---

### Post by fimbar on 2009-11-28
> **hirnwurscht said:**
> "That Command" is your mythtv-backend ...
I should have said "a couple of minutes UNTIL you see something related to EIT", sorry.

That's no problem. I just wondered whether something was wrong since it wasn't simply taking a couple of minutes. ;)

> **hirnwurscht said:**
>  Are you really sure that you activated EIT in mythtv-setup (Video-Sources / source / only EIT)?

Positive. Absolutely 100%

> **hirnwurscht said:**
>  Since you also got permission issues, post the output of 
```
ls -lh /dev/dvb*
```I just remembered what i read somewhere on the mythtv user list, iirc mythtv has NO problems when you do the channel-scan in mythtv-setup.

Here you go.

ian@MediaServer:~$ ls -lh /dev/dvb*
total 0
drwxr-xr-x 2 root root 120 2009-11-28 15:01 adapter0

I've tried doing a chmod on it and, for that session, running the MythTV Backend Setup from the gnome menu works fine. However, after every reboot the permissions on that folder get reset to what they were previously.

> **hirnwurscht said:**
> Eventualy a rescan in mythtv-setup does the trick?

The rescan in MythTV never finds anything if I just "scan for channels". I have to pull in the channels.conf file to get MythTV to find any channels. However, once I've done that I can "scan all existing transports" and it also finds all the channels.

---

### Post by hirnwurscht on 2009-11-29
This will help you get the permission issue fixed:
[Device Filenames and Udev]("http://www.mythtv.org/wiki/Device_Filenames_and_udev")

Another thing you can try is to check (i.e. in mythweb) if you enabled epg data for the channels you want.

Let me get this straight, even if you watch a channel for some minutes it doesn't fill in the epg-data?

---

### Post by fimbar on 2009-11-29
> **hirnwurscht said:**
> This will help you get the permission issue fixed:
[Device Filenames and Udev]("http://www.mythtv.org/wiki/Device_Filenames_and_udev")

Thanks for the link, I'll work through it and report back.

> **hirnwurscht said:**
> Another thing you can try is to check (i.e. in mythweb) if you enabled epg data for the channels you want.

Yeah, they're all checked.

> **hirnwurscht said:**
> Let me get this straight, even if you watch a channel for some minutes it doesn't fill in the epg-data?

Correct.

---

### Post by fimbar on 2009-11-29
I'm not sure if it's helpful but here is the output from when I run mythfilldatabase

```

ian@MediaServer:~$ mythfilldatabase
2009-11-29 11:10:52.565 Using runtime prefix = /usr
2009-11-29 11:10:52.565 Using configuration directory = /home/ian/.mythtv
2009-11-29 11:10:52.566 Empty LocalHostName.
2009-11-29 11:10:52.566 Using localhost value of MediaServer
2009-11-29 11:10:52.568 New DB connection, total: 1
2009-11-29 11:10:52.570 Connected to database 'mythconverg' at host: localhost
2009-11-29 11:10:52.570 Closing DB connection named 'DBManager0'
2009-11-29 11:10:52.570 Connected to database 'mythconverg' at host: localhost
2009-11-29 11:10:52.572 Current MythTV Schema Version (DBSchemaVer): 1244
2009-11-29 11:10:52.573 New DB connection, total: 2
2009-11-29 11:10:52.573 Connected to database 'mythconverg' at host: localhost
**2009-11-29 11:10:52.573 Source 1 configured to use only the broadcasted guide data. Skipping.**
2009-11-29 11:10:52.574 Data fetching complete.
2009-11-29 11:10:52.574 Adjusting program database end times.
2009-11-29 11:10:52.574     0 replacements made
2009-11-29 11:10:52.574 Marking generic episodes.
2009-11-29 11:10:52.574     Found 0
2009-11-29 11:10:52.574 Fudging non-unique programids with multiple parts.
2009-11-29 11:10:52.574     Found -1
2009-11-29 11:10:52.574 Marking repeats.
2009-11-29 11:10:52.575     Found 0
2009-11-29 11:10:52.575 Unmarking new episode rebroadcast repeats.
2009-11-29 11:10:52.575     Found 0
2009-11-29 11:10:52.575 Marking episode first showings.
2009-11-29 11:10:52.575     Found 0
2009-11-29 11:10:52.575 Marking episode last showings.
2009-11-29 11:10:52.575     Found 0
2009-11-29 11:10:52.576
===============================================================
| Attempting to contact the master backend for rescheduling.  |
| If the master is not running, rescheduling will happen when |
| the master backend is restarted.                            |
===============================================================
2009-11-29 11:10:52.577 MythContext: Connecting to backend server: 192.168.1.64:6543 (try 1 of 1)
2009-11-29 11:10:52.577 Using protocol version 50
2009-11-29 11:10:52.734 Received a remote 'Clear Cache' request
2009-11-29 11:10:52.734 mythfilldatabase run complete.
2009-11-29 11:10:52.734 DataDirect: Deleting temporary files

```Is this line a clue?

[B]2009-11-29 11:10:52.573 Source 1 configured to use only the broadcasted guide data. Skipping.

[/B]Under Jaunty and Karmic I'm fairly sure the **Found **lines in the log above were populated with data and not just 0

EDIT: Sorry typo, I meant Jaunty and **Intrepid** not Karmic

---

### Post by hirnwurscht on 2009-11-29
> 2009-11-29 11:10:52.573 Source 1 configured to use only the broadcasted guide data. Skipping.
Seems ok to me...

[_Here_]("http://mythtv.org/wiki/EIT"), someone writes that Importing channels.conf doesn't provide enough information for MythTV to use EIT. Especially with DVB-T in UK and DVB-C in the Netherlands.

Maybe EIT with channels imported from channels.conf stopped working at some point in mythtv development.

Since this pretty much fits your problem, you should compare the mythtv-versions used. since karmic is using 0.22 as default and jaunty and intrepid do use 0.21...

Maybe a rescan with an import that went kinda wrong isn't enough?

---

### Post by fimbar on 2009-11-29
> **hirnwurscht said:**
> Seems ok to me...

[_Here_]("http://mythtv.org/wiki/EIT"), someone writes that Importing channels.conf doesn't provide enough information for MythTV to use EIT. Especially with DVB-T in UK and DVB-C in the Netherlands.

Maybe EIT with channels imported from channels.conf stopped working at some point in mythtv development.

Since this pretty much fits your problem, you should compare the mythtv-versions used. since karmic is using 0.22 as default and jaunty and intrepid do use 0.21...

Maybe a rescan with an import that went kinda wrong isn't enough?

Hmm, not very promising is it :sad:

Perhaps I need to replace my existing tuner for one that is a bit more "MythTV-friendly". 

Oh well. Thanks very much indeed for your help hirnwurscht. ;)

---

### Post by hirnwurscht on 2009-11-29
You're welcome.

FYI thats how i search for my DVB-T channels:

in mythtv-setup go to video-sources, select channel scan and do a full scan with the frequency table set to germany... 

Don't give up! :)

---

### Post by fimbar on 2009-11-29
> **hirnwurscht said:**
> You're welcome.

FYI thats how i search for my DVB-T channels:

in mythtv-setup go to video-sources, select channel scan and do a full scan with the frequency table set to germany... 

Don't give up! :)

When I try scanning the way you do all I get is screen loads of "Timed out, no channels" and it doesn't populate Myth with any channels. Using the channels.conf is the only way I can get any channels in there :)

---

### Post by hirnwurscht on 2009-11-29
I think if you don't delete the imported channels before doing the full scan, they're just updated (or not).

The mythtv wiki points to a mug (mythtv user group) in the UK, maybe someone there can help.

If you don't find a solution, you could try to update Jaunty (with working mythtv) to Karmic...

Btw, since the fresh install of Jaunty works and the fresh install of Karmic doesn't... You restore from the same database backup, no?
Maybe your database is damaged, run optimize_mythdb.pl ( in /usr/share/doc/mythtv-backend/contrib/maintenance/ ).

Good Luck!

---

### Post by fimbar on 2009-11-29
> **hirnwurscht said:**
> If you don't find a solution, you could try to update Jaunty (with working mythtv) to Karmic...


One of the many things I tried was to update Jaunty to Karmic and the channel guide was still intact in Karmic. However, when I deleted the card and settings etc. from MythTV and re-set them back up again it didn't repopulate the guide.

I'll head over to that User group you mentioned and see if anyone is hitting the same issues.

Thanks again for all your help.

---

### Post by hirnwurscht on 2009-11-29
When deleting makes it happen, the way you config the card may be wrong. You ticked the "Use for EIT-Scan" in the Card-Setup, didn't you?. Also, IIRC the EIT-scan option and the "use on demand" option contradict each other.

---

### Post by fimbar on 2009-11-29
> **hirnwurscht said:**
> You ticked the "Use for EIT-Scan" in the Card-Setup, didn't you?. Also, IIRC the EIT-scan option and the "use on demand" option contradict each other.

Yeah, I've pretty much tried every option possible. I'm gonna take your advice tho and not give up. ;)

---

### Post by poli5681 on 2009-12-03
Hello,

Same Problem for me. I updated from Intrepid to Karmic and everything worked (of course without rescanning). EIT data was updated, just as usual.

I had to rescan, because my cable provider changed some transponders...

First i tried with the w_scan and import channels.conf way:
No EIT data - everything else works

I thought it might have to do with missing data in the channels.conf, so i dropped everything and entered the transponders manually  - no EIT...

I played around with the settings for the DVB cards (especially the timeout settings) and nothing seems to help.

I got the EIT Scan to work 1 time, but only as long as i entered a single transponder, so i guess it might have to do with channel-changing - as soon as i entered a second one and scanned for channels - I got no data for both transponders.

My logs seem to be pretty much the same as for you, fimbar - no errors from the EITScanner.

Hope we find a solution.

Thanks!

Edit: Never mind; I already found a solution for this. You have to do a full scan of a frequency instead of adding channels or transponders
manually. I have no idea why this makes any difference, but since i did a full scan everything works.

---

### Post by ross.ackland on 2010-01-07
> **poli5681 said:**
> 

Same Problem for me. I updated from Intrepid to Karmic and everything worked (of course without rescanning). EIT data was updated, just as usual.

I had to rescan, because my cable provider changed some transponders...

First i tried with the w_scan and import channels.conf way:
No EIT data - everything else works

I thought it might have to do with missing data in the channels.conf, so i dropped everything and entered the transponders manually  - no EIT...


I had the same problem as well, making sure EIT Guide data options where checked etc. (I'm running same Karmic/Mythtv versions as fimbar). Everything was working fine until I recently decided to rescan existing transports, then I lost all guide data. I created a new channels.conf file using the scan utility and imported, but still no guide data. The only way I can get guide data back is to use the Full Scan (Tuned) option where I manually enter the  station frequency and parameters. Then it works!!

---

