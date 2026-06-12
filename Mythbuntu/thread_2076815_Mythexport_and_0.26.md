---
title: "Mythexport and 0.26"
date: 2012-10-27
forum: Mythbuntu
---

### Post by dsfatwork on 2012-10-27
I had a totally working 12.04 / .25 system with mythexport functioning as it should.  With one small problem, on occasion something would null the config.xml file.  I have read that this is a known bug and was fixed it .26.  So I used the Mythbuntu control panel and set the updates to .26.  After the smoke cleared Mythbuntu still worked but mythexport no longer does.  The logs seem to indicate that it is not connecting to the database.  I've checked the config.xml file and the info there is correct, I tried uninstalling / re-installing mythexport but no luck.

******************************************************
Mythexport.log right after reboot

October 26 22:02:01 kie09760 /usr/bin/mythexport-daemon[1095]: Starting Processing:  1351314121

DBI connect('database=mythconverg:host=localhost;port=3306','mythtv',...) failed: Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2) at /usr/share/perl5/MythTV.pm line 371

October 26 22:02:03 kie09760 /usr/bin/mythexport-daemon[1095]: Can't connect to MythTV: Cannot connect to database: 

 at line 88 in /usr/bin/mythexport-daemon
avconv version 0.8.3-4:0.8.3-0ubuntu0.12.04.1, Copyright (c) 2000-2012 the Libav developers
  built on Jun 12 2012 16:52:09 with gcc 4.6.3
/var/lib/mythtv/banners/: Operation not permitted

October 26 22:03:09 kie09760 /usr/bin/mythexport-daemon[1095]: ERROR: No resulting file from ffmpeg, most likely your ffmpeg failed.  Enable debugging and test by hand. at line 459 in /usr/bin/mythexport-daemon
******************************************************

Any help, or a point in the right direction would be appreciated.

---

### Post by BicyclerBoy on 2012-10-28
It looks like your problem "ffmpeg" is the avconv imposter..

MythTV ships with its own real version of ffmpeg called mythffmpeg.
It tends to be a little outdated but still better than avconv.

You could first try to solve by reconfigure the transcoding cmds to use mythffmpeg or hack the perl script.

If all fails then you can build ffmpeg from source..I would suggest making a private build with no shared libraries (& a private name myffmpeg for ex.).
If you make (install) ffmpeg with shared libs you risk making a bigger mess of the *buntu avconv mess.
You still have to make the mythexport scrips use this private ffmpeg..

---

### Post by lionsnob on 2012-10-28
I'm having a similar issue.  I'm also seeing an error when trying to access my banners directory.  Here is the output with debugging on:

```
October 28 19:51:43 mythdish /usr/bin/mythexport-daemon[21271]: exportdir = /exported at line 353 in /usr/bin/mythexport-daemon
October 28 19:51:43 mythdish /usr/bin/mythexport-daemon[21271]: starttime = 20121028073000 at line 354 in /usr/bin/mythexport-daemon
October 28 19:51:43 mythdish /usr/bin/mythexport-daemon[21271]: chanid = 3289 at line 355 in /usr/bin/mythexport-daemon
October 28 19:51:43 mythdish /usr/bin/mythexport-daemon[21271]: config = PortableH264HighRes at line 356 in /usr/bin/mythexport-daemon
October 28 19:51:43 mythdish /usr/bin/mythexport-daemon[21271]: query = SELECT rec.title, rec.subtitle, rec.description, pg.syndicatedepisodenumber, pg.showtype, rec.programid, rec.basename, rec.starttime
    FROM recorded rec LEFT JOIN program pg ON pg.starttime = rec.starttime AND pg.chanid = rec.chanid
    WHERE rec.chanid=? AND rec.starttime=? at line 365 in /usr/bin/mythexport-daemon
October 28 19:51:43 mythdish /usr/bin/mythexport-daemon[21271]: Going into new mode
 at line 382 in /usr/bin/mythexport-daemon
October 28 19:51:43 mythdish /usr/bin/mythexport-daemon[21271]: query = SELECT callsign FROM channel WHERE chanid=? at line 390 in /usr/bin/mythexport-daemon
avconv version 0.8.3-4:0.8.3-0ubuntu0.12.04.1, Copyright (c) 2000-2012 the Libav developers
  built on Jun 12 2012 16:37:58 with gcc 4.6.3
/videos1/Banners/: Operation not permitted
October 28 19:51:43 mythdish /usr/bin/mythexport-daemon[21271]: ERROR: No resulting file from ffmpeg, most likely your ffmpeg failed.  Enable debugging and test by hand. at line 459 in /usr/bin/mythexport-daemon

```

Any ideas?

---

### Post by dsfatwork on 2012-10-28
Well not that I'd wish my problems on anyone else, still it's good to know that I'm not the only one.

I had thought that I was having a mysqld.sock issue because of the 'failed to connect' line in my mythexport.log.  But I now think that may just be the mythexport-daemon trying to attach before mysql has re-created the socket.

It must be able to talk to the database because I can go into the Mythexport web page 'File Maintenance' and delete files from my storage directory, have them show up in the 'Job Queue' page and then get cleared from the storage directory and mythconverg database.

I have no idea why the 'Banners/: Operation not permitted' is showing up or what it even has to do with mythexport.

This all worked right before I updated to 0.26, but I'm at a loss as to what got broken.

---

### Post by dsfatwork on 2012-11-01
Well I think I've figured this problem out. or at least I've gotten my install to start working again.  I noticed that a couple of my records were getting processed by Mythexport each day.  A 6am and 12Noon record, yet the others were not.  I remembered reading something about the database switching to UTC time in the 0.26 release.

Anyway, the User Job that Mythexport assigns starts with a %STARTTIME% command, I changed this to %STARTTIMEUTC% in mythtv-setup and low and behold it started running just like before.

If you wanted to fix it at the source the file is 
/usr/share/mythtv/mythexport/setupsave.cgi line 31

my $command = "mythexport_addjob starttime=%STARTTIME% chanid=%CHANID% config=$config deleteperiod=$deletePeriod podcastname=$podcastName";

I hope this does it, I'm marking it as solved

---

### Post by lionsnob on 2012-11-02
> **dsfatwork said:**
> Well I think I've figured this problem out. or at least I've gotten my install to start working again.  I noticed that a couple of my records were getting processed by Mythexport each day.  A 6am and 12Noon record, yet the others were not.  I remembered reading something about the database switching to UTC time in the 0.26 release.

Anyway, the User Job that Mythexport assigns starts with a %STARTTIME% command, I changed this to %STARTTIMEUTC% in mythtv-setup and low and behold it started running just like before.

If you wanted to fix it at the source the file is 
/usr/share/mythtv/mythexport/setupsave.cgi line 31

my $command = "mythexport_addjob starttime=%STARTTIME% chanid=%CHANID% config=$config deleteperiod=$deletePeriod podcastname=$podcastName";

I hope this does it, I'm marking it as solved

LOL.  I just spent an hour on this and came to the same conclusion.  Consider your solution verified!

---

### Post by rhpot1991 on 2012-11-06
Would someone mind opening a bug on this?  I'll get a fix pushed to our testing PPA then.

---

### Post by dsfatwork on 2012-11-06
I submitted (my first ever) a bug report on this issue.  Hope I did right.

---

