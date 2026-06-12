---
title: "More Recording Help needed... &quot;Missing Files&quot;?"
date: 2011-05-14
forum: Mythbuntu
---

### Post by iiwii on 2011-05-14
I've been making custom schedules to record 5 recordings while I am at work. After a week of doing this is the actual recordings are not always there. A couple of days, all 5 recordings would record with no problems. Other days it would be 4 out of 5 or 3 out of 5.  When I go into the Media Library and see all my recorded events the missing ones are grayed out and trying to open them gives a "file missing for this recording" error.

Summary: It knows it was suppose to record something, but there is NO file in the recording directory.  It's not always the same "window" either.  One day, the second recording did not record. Another day it missed the third recording.  One day, the 1st and 5th did not record.

My Hauppauge HVR-1250 shows 2 recorders in setup.  Is there a way to simultaneously record the same recording from the same channel?  This way I would have a backup in case one failed. Or am I mistaken in how that works?

Thanks in advance!

---

### Post by bance on 2011-05-14
Check your logs.... or provide them so others can help!

---

### Post by ian dobson on 2011-05-15
Hi,

Yep, check your log files, it sounds like your tuner has a problem with locking onto a channel.

Also maybe try increasing the tuner timeout in mythtv-setup.

Regards
Ian Dobson

---

### Post by iiwii on 2011-05-15
> **bance said:**
> Check your logs.... or provide them so others can help!

Still new at this...  How do I check my logs? I ran through Setup and it looks like they haven't been logging anything.  I checked on Frontend, Backend, and Hardware logs.  Is there an existing log or do I need to wait for it to fail again?

---

### Post by ian dobson on 2011-05-15
Hi,

The logs for mythtv are in /var/log/mythtv a log rotation process copies the actual log file to log.1, log.1 to log2 etc once per day hand myth normally stores 7 days worth of logs.

Just look for error..

Regards
Ian Dobson

---

### Post by iiwii on 2011-05-15
Okay, I think I am getting closer.  I found a log for mythbackend and narrowed it down to the day I missed two recordings.  The entire day is about 17pages long.  I've narrowed it down to the 2 events that produced missing files... (These are not 0byte files. They don't exist at all.)

--------------------------------- EVENT 1 is as follows...


 [FONT=Courier New, monospace][SIZE=2]2011-05-10 05:08:30.640 Reschedule requested for id 0.[/SIZE][/FONT]
 [FONT=Courier New, monospace][SIZE=2]2011-05-10 05:08:30.817 Scheduled 45 items in 0.2 = 0.06 match + 0.12 place[/SIZE][/FONT]
 [FONT=Courier New, monospace][SIZE=2]2011-05-10 05:09:00.599 TVRec(2): ASK_RECORDING 2 29 0 0[/SIZE][/FONT]
 [FONT=Courier New, monospace][SIZE=2]2011-05-10 05:09:00.701 TVRec(1): ASK_RECORDING 1 29 0 0[/SIZE][/FONT]
 [FONT=Courier New, monospace][SIZE=2]2011-05-10 05:09:31.974 TVRec(1): Changing from None to RecordingOnly[/SIZE][/FONT]
 [FONT=Courier New, monospace][SIZE=2]2011-05-10 05:09:32.016 TVRec(1): HW Tuner: 1->1[/SIZE][/FONT]
 [FONT=Courier New, monospace][SIZE=2]2011-05-10 05:09:32.195 AutoExpire: CalcParams(): Max required Free Space: 3.0 GB w/freq: 14 min[/SIZE][/FONT]
 [FONT=Courier New, monospace][SIZE=2]2011-05-10 05:09:32.257 Started recording: "RECORD 1 (Manual Record)":"Tue May 10 05:10:00 2011": channel 11791 on cardid 1, sourceid 1[/SIZE][/FONT]
 [FONT=Courier New, monospace][SIZE=2]2011-05-10 05:17:00.000 AutoExpire: CalcParams(): Max required Free Space: 3.0 GB w/freq: 14 min[/SIZE][/FONT]
 [FONT=Courier New, monospace][SIZE=2]2011-05-10 05:17:01.799 MainServer::ANN Monitor[/SIZE][/FONT]
 [FONT=Courier New, monospace][SIZE=2]2011-05-10 05:17:01.874 adding: htpc as a client (events: 2)[/SIZE][/FONT]
 [FONT=Courier New, monospace][SIZE=2]2011-05-10 05:25:30.293 TVRec(1): Changing from RecordingOnly to None[/SIZE][/FONT]
 [FONT=Courier New, monospace][SIZE=2]2011-05-10 05:25:30.520 Updating status for "RECORD 1 (Manual Record)":"Tue May 10 05:10:00 2011" on cardid 1 (Tuning => Recorder Failed)[/SIZE][/FONT]
 [FONT=Courier New, monospace][SIZE=2]2011-05-10 05:25:30.600 Reschedule requested for id 0.[/SIZE][/FONT]
 [FONT=Courier New, monospace][SIZE=2]2011-05-10 05:25:30.907 Scheduled 44 items in 0.3 = 0.17 match + 0.14 place[/SIZE][/FONT]
 [FONT=Courier New, monospace][SIZE=2]2011-05-10 05:25:31.173 Preview Error: Encountered problems running '/usr/bin/mythpreviewgen --size 0x0 --chanid 11791 --starttime 20110510051000  > /dev/null'[/SIZE][/FONT]
 [FONT=Courier New, monospace][SIZE=2]2011-05-10 05:31:00.095 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min[/SIZE][/FONT]
 [FONT=Courier New, monospace][SIZE=2]2011-05-10 05:33:30.046 Reschedule requested for id 0.[/SIZE][/FONT]
 

---------------------------- EVENT 5 is as follows....


 [FONT=Courier New, monospace][SIZE=2]2011-05-10 10:58:02.517 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min[/SIZE][/FONT]
 [FONT=Courier New, monospace][SIZE=2]2011-05-10 10:58:30.781 Reschedule requested for id 0.[/SIZE][/FONT]
 [FONT=Courier New, monospace][SIZE=2]2011-05-10 10:58:30.943 Scheduled 41 items in 0.2 = 0.05 match + 0.11 place[/SIZE][/FONT]
 [FONT=Courier New, monospace][SIZE=2]2011-05-10 10:58:59.513 TVRec(2): ASK_RECORDING 2 29 0 0[/SIZE][/FONT]
 [FONT=Courier New, monospace][SIZE=2]2011-05-10 10:59:00.002 TVRec(1): ASK_RECORDING 1 29 0 0[/SIZE][/FONT]
 [FONT=Courier New, monospace][SIZE=2]2011-05-10 10:59:31.183 TVRec(1): Changing from None to RecordingOnly[/SIZE][/FONT]
 [FONT=Courier New, monospace][SIZE=2]2011-05-10 10:59:31.232 TVRec(1): HW Tuner: 1->1[/SIZE][/FONT]
 [FONT=Courier New, monospace][SIZE=2]2011-05-10 10:59:31.318 AutoExpire: CalcParams(): Max required Free Space: 3.0 GB w/freq: 14 min[/SIZE][/FONT]
 [FONT=Courier New, monospace][SIZE=2]2011-05-10 10:59:31.366 Started recording: "RECORD @11 (Manual Record)":"Tue May 10 11:00:00 2011": channel 11791 on cardid 1, sourceid 1[/SIZE][/FONT]
 [FONT=Courier New, monospace][SIZE=2]2011-05-10 11:13:02.619 AutoExpire: CalcParams(): Max required Free Space: 3.0 GB w/freq: 14 min[/SIZE][/FONT]
 [FONT=Courier New, monospace][SIZE=2]2011-05-10 11:17:02.018 MainServer::ANN Monitor[/SIZE][/FONT]
 [FONT=Courier New, monospace][SIZE=2]2011-05-10 11:17:02.081 adding: htpc as a client (events: 2)[/SIZE][/FONT]
 [FONT=Courier New, monospace][SIZE=2]2011-05-10 11:27:02.725 AutoExpire: CalcParams(): Max required Free Space: 3.0 GB w/freq: 14 min[/SIZE][/FONT]
 [FONT=Courier New, monospace][SIZE=2]2011-05-10 11:30:30.553 TVRec(1): Changing from RecordingOnly to None[/SIZE][/FONT]
 [FONT=Courier New, monospace][SIZE=2]2011-05-10 11:30:30.829 Updating status for "RECORD @11 (Manual Record)":"Tue May 10 11:00:00 2011" on cardid 1 (Tuning => Recorder Failed)[/SIZE][/FONT]
 [FONT=Courier New, monospace][SIZE=2]2011-05-10 11:30:30.873 Reschedule requested for id 0.[/SIZE][/FONT]
 [FONT=Courier New, monospace][SIZE=2]2011-05-10 11:30:31.010 Scheduled 40 items in 0.1 = 0.04 match + 0.10 place[/SIZE][/FONT]
 [FONT=Courier New, monospace][SIZE=2]2011-05-10 11:30:31.058 Preview Error: Encountered problems running '/usr/bin/mythpreviewgen --size 0x0 --chanid 11791 --starttime 20110510110000  > /dev/null'[/SIZE][/FONT]
 [FONT=Courier New, monospace][SIZE=2]2011-05-10 11:31:10.590 ProgramInfo(11791_20110510110000.mpg), Error: GetPlaybackURL: '11791_20110510110000.mpg' should be local, but it can not be found.[/SIZE][/FONT]
 [FONT=Courier New, monospace][SIZE=2]2011-05-10 11:31:10.658 ProgramInfo(11791_20110510110000.mpg), Error: GetPlaybackURL: '11791_20110510110000.mpg' should be local, but it can not be found.[/SIZE][/FONT]
 [FONT=Courier New, monospace][SIZE=2]2011-05-10 11:31:10.699 JobQueue: Commercial Detection Starting for "RECORD @11 (Manual Record)":"Tue May 10 11:00:00 2011" recorded from channel 11791 at 2011-05-10T11:00:00[/SIZE][/FONT]
 [FONT=Courier New, monospace][SIZE=2]2011-05-10 11:31:10.868 Using runtime prefix = /usr[/SIZE][/FONT]
 [FONT=Courier New, monospace][SIZE=2]2011-05-10 11:31:10.931 Using configuration directory = /home/mythtv/.mythtv[/SIZE][/FONT]
 [FONT=Courier New, monospace][SIZE=2]2011-05-10 11:31:10.973 Empty LocalHostName.[/SIZE][/FONT]
 [FONT=Courier New, monospace][SIZE=2]2011-05-10 11:31:11.014 Using localhost value of htpc[/SIZE][/FONT]
 [FONT=Courier New, monospace][SIZE=2]2011-05-10 11:31:11.063 New DB connection, total: 1[/SIZE][/FONT]
 [FONT=Courier New, monospace][SIZE=2]2011-05-10 11:31:11.109 Connected to database 'mythconverg' at host: localhost[/SIZE][/FONT]
 [FONT=Courier New, monospace][SIZE=2]2011-05-10 11:31:11.153 Closing DB connection named 'DBManager0'[/SIZE][/FONT]
 [FONT=Courier New, monospace][SIZE=2]2011-05-10 11:31:11.190 Connected to database 'mythconverg' at host: localhost[/SIZE][/FONT]
 [FONT=Courier New, monospace][SIZE=2]2011-05-10 11:31:11.233 Current locale EN_US[/SIZE][/FONT]
 [FONT=Courier New, monospace][SIZE=2]2011-05-10 11:31:11.273 Reading locale defaults from /usr/share/mythtv//locales/en_us.xml[/SIZE][/FONT]
 [FONT=Courier New, monospace][SIZE=2]2011-05-10 11:31:11.321 Loading en_us translation for module mythfrontend[/SIZE][/FONT]
 [FONT=Courier New, monospace][SIZE=2]2011-05-10 11:31:11.362 ProgramInfo(11791_20110510110000.mpg), Error: GetPlaybackURL: '11791_20110510110000.mpg' should be local, but it can not be found.[/SIZE][/FONT]
 [FONT=Courier New, monospace][SIZE=2]2011-05-10 11:31:11.483 MythSocket(9557128:8): Unable to lookup: [/SIZE][/FONT] 
 [FONT=Courier New, monospace][SIZE=2]2011-05-10 11:31:11.533 RemoteFile::openSocket(control socket), Error: [/SIZE][/FONT] 
 [FONT=Courier New, monospace][SIZE=2]			Could not connect to server :6543[/SIZE][/FONT]
 [FONT=Courier New, monospace][SIZE=2]2011-05-10 11:31:11.583 RingBuf(GetPlaybackURL/UNABLE/TO/FIND/LOCAL/FILE/ON/htpc/11791_20110510110000.mpg) Error: RingBuffer::RingBuffer(): Failed to open remote file (GetPlaybackURL/UNABLE/TO/FIND/LOCAL/FILE/ON/htpc/11791_20110510110000.mpg)[/SIZE][/FONT]
 [FONT=Courier New, monospace][SIZE=2]2011-05-10 11:31:11.640 ProgramInfo(11791_20110510110000.mpg), Error: GetPlaybackURL: '11791_20110510110000.mpg' should be local, but it can not be found.[/SIZE][/FONT]
 [FONT=Courier New, monospace][SIZE=2]2011-05-10 11:31:11.697 MythCoreContext: Connecting to backend server: 127.0.0.1:6543 (try 1 of 1)[/SIZE][/FONT]
 [FONT=Courier New, monospace][SIZE=2]2011-05-10 11:31:11.735 Using protocol version 63[/SIZE][/FONT]
 [FONT=Courier New, monospace][SIZE=2]2011-05-10 11:31:11.776 MainServer::ANN Monitor[/SIZE][/FONT]
 [FONT=Courier New, monospace][SIZE=2]2011-05-10 11:31:11.817 adding: htpc as a client (events: 0)[/SIZE][/FONT]
 [FONT=Courier New, monospace][SIZE=2]2011-05-10 11:31:11.859 MainServer::ANN Monitor[/SIZE][/FONT]
 [FONT=Courier New, monospace][SIZE=2]2011-05-10 11:31:11.901 adding: htpc as a client (events: 1)[/SIZE][/FONT]
 [FONT=Courier New, monospace][SIZE=2]2011-05-10 11:31:11.945 RingBuf(GetPlaybackURL/UNABLE/TO/FIND/LOCAL/FILE/ON/htpc/11791_20110510110000.mpg) Warning: Peek() requested 2048 bytes, but only returning -1[/SIZE][/FONT]
 [FONT=Courier New, monospace][SIZE=2]2011-05-10 11:31:11.946 RingBuf(GetPlaybackURL/UNABLE/TO/FIND/LOCAL/FILE/ON/htpc/11791_20110510110000.mpg) Error: Invalid file descriptor in 'safe_read()'[/SIZE][/FONT]
 [FONT=Courier New, monospace][SIZE=2]2011-05-10 11:31:11.993 Player(0), Warning: OpenFile() waiting on data[/SIZE][/FONT]
 [FONT=Courier New, monospace][SIZE=2]2011-05-10 11:31:12.143 RingBuf(GetPlaybackURL/UNABLE/TO/FIND/LOCAL/FILE/ON/htpc/11791_20110510110000.mpg) Warning: Peek() requested 2048 bytes, but only returning 0[/SIZE][/FONT]
 [FONT=Courier New, monospace][SIZE=2]2011-05-10 11:31:12.185 Player(0), Warning: OpenFile() waiting on data[/SIZE][/FONT]
 [FONT=Courier New, monospace][SIZE=2]2011-05-10 11:31:12.276 RingBuf(GetPlaybackURL/UNABLE/TO/FIND/LOCAL/FILE/ON/htpc/11791_20110510110000.mpg) Warning: Peek() requested 2048 bytes, but only returning 0[/SIZE][/FONT]
 [FONT=Courier New, monospace][SIZE=2]2011-05-10 11:31:12.318 Player(0), Warning: OpenFile() waiting on data[/SIZE][/FONT]
 [FONT=Courier New, monospace][SIZE=2]2011-05-10 11:31:12.410 RingBuf(GetPlaybackURL/UNABLE/TO/FIND/LOCAL/FILE/ON/htpc/11791_20110510110000.mpg) Warning: Peek() requested 2048 bytes, but only returning 0[/SIZE][/FONT]
 [FONT=Courier New, monospace][SIZE=2]2011-05-10 11:31:12.452 Player(0), Warning: OpenFile() waiting on data[/SIZE][/FONT]
 [FONT=Courier New, monospace][SIZE=2]2011-05-10 11:31:12.543 RingBuf(GetPlaybackURL/UNABLE/TO/FIND/LOCAL/FILE/ON/htpc/11791_20110510110000.mpg) Warning: Peek() requested 2048 bytes, but only returning 0[/SIZE][/FONT]
 [FONT=Courier New, monospace][SIZE=2]2011-05-10 11:31:12.585 Player(0), Warning: OpenFile() waiting on data[/SIZE][/FONT]
 [FONT=Courier New, monospace][SIZE=2]2011-05-10 11:31:12.677 RingBuf(GetPlaybackURL/UNABLE/TO/FIND/LOCAL/FILE/ON/htpc/11791_20110510110000.mpg) Warning: Peek() requested 2048 bytes, but only returning 0[/SIZE][/FONT]
 [FONT=Courier New, monospace][SIZE=2]2011-05-10 11:31:12.719 Player(0), Warning: OpenFile() waiting on data[/SIZE][/FONT]
 [FONT=Courier New, monospace][SIZE=2]2011-05-10 11:31:12.810 RingBuf(GetPlaybackURL/UNABLE/TO/FIND/LOCAL/FILE/ON/htpc/11791_20110510110000.mpg) Warning: Peek() requested 2048 bytes, but only returning 0[/SIZE][/FONT]
 [FONT=Courier New, monospace][SIZE=2]2011-05-10 11:31:12.852 Player(0), Warning: OpenFile() waiting on data[/SIZE][/FONT]
 [FONT=Courier New, monospace][SIZE=2]2011-05-10 11:31:12.944 RingBuf(GetPlaybackURL/UNABLE/TO/FIND/LOCAL/FILE/ON/htpc/11791_20110510110000.mpg) Warning: Peek() requested 2048 bytes, but only returning 0[/SIZE][/FONT]
 [FONT=Courier New, monospace][SIZE=2]2011-05-10 11:31:12.986 Player(0), Error: OpenFile(): Could not read first 2048 bytes of 'GetPlaybackURL/UNABLE/TO/FIND/LOCAL/FILE/ON/htpc/11791_20110510110000.mpg'[/SIZE][/FONT]
 [FONT=Courier New, monospace][SIZE=2]2011-05-10 11:31:14.036 ~MythContext waiting for threads to exit.[/SIZE][/FONT]
 [FONT=Courier New, monospace][SIZE=2]2011-05-10 11:31:14.189 ProgramInfo(11791_20110510110000.mpg), Error: GetPlaybackURL: '11791_20110510110000.mpg' should be local, but it can not be found.[/SIZE][/FONT]

---

### Post by iiwii on 2011-05-22
> **ian dobson said:**
> Hi,

Yep, check your log files, it sounds like your tuner has a problem with locking onto a channel.

Also maybe try increasing the tuner timeout in mythtv-setup.

Regards
Ian Dobson

Thanks for the suggestion.  I think that helped.  The first two days after I upped the wait time my recordings were perfect -- 5 a day for 2 days yielded a perfect 10! Day 3 the system must have locked up. I had the first recording but nothing else (not even the "file missing" error). I came home to find the system on a black screen and unresponsive. Day 4 it missed a recording going 4 out of 5.

 Of course, it would be the ONE channel I need that it cannot lock on to! Today, it has had trouble getting a lock when just watching TV.  Sometimes it takes several seconds to lock on and sometimes even after a full minute it never did.  All the other channels lock pretty quickly (1-3 seconds).

I noticed when the other channels lock they give a 2.6db s/n.  My one channel I need (ABC)  only gives a "partial lock" at 2.5db.  It seems to be working now, but how do I keep it working?  

Any suggestions would be appreciated.  I guess it could be the tuner card. Would a different card fix the problem? I'm using a [Hauppauge 1250]("http://www.newegg.com/Product/Product.aspx?Item=N82E16815116028").

* Update for Monday: 0 for 5 recordings... "Watch TV" locked in on 2.5db.  I'm completely baffled now.

---

### Post by iiwii on 2011-06-10
**Possibly Solved?**

Just a quick update...  I was browsing some threads on here about a week ago and found the suggestion about turning on quick tune.  I turned it to "always" and I have had 25+ consecutive successful recordings! I haven't missed a recording this week.  Maybe it was the solution all a long or it worked in concert with adjusting the tuner time out setting. Either way, I am finally pleased with my setup and Mythbuntu.

Any idea what quick tune does? I'd like to write this up in my "case study" of my Mythbuntu experience.

---

