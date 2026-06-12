---
title: "Storage directory issues"
date: 2009-11-14
forum: Mythbuntu
---

### Post by sawbuck on 2009-11-14
As usual, let me preface this with the statement I'm still finding my way around Mythtv and ubuntu....

I have Mythbuntu 9.10 installed taking up all space on my main (250 Gb)disk.  After some stumbling and reinstalls I got it up and working fine.  I recently added the Ubuntu desktop because I needed some extra features (printing, disk utilities.etc) and was having problems getting the right packages added (that seemed to work in the previous 9.04).  Mythtv LiveTV, scheduling and recording, transcoding, watching,etc seems to be running OK all from the single disk with Ubuntu desktop and its features added as long as I use the defaut storage director..  

I had a smaller (80Gb) disk in the system that previously had been set up with XP & mythtv 0.21/fedora that I thought I'd use for some testing.  I used the Pallimpset Disk utility to format the 2nd disk to a 77 Gb & 3Gb Ext4 partitions and mounted them.   A sample text store and retrieve showed I could that as well as delete with no problem so I assumed the system could see the mounted devices. .

My problem is that I created a new storage directory in the 77Gb partition (from Mythbackend setup) and tried to use it to store some sample recordings I wanted to experiment with.  (Being a total greenie, I've learned not to mess with the primary area I use a lot for normal viewing ). The first effort said: (from mythbackend log)

```
2009-11-13 16:30:02.167 TVRec(1): Changing from None to Watching RecordingOnly
2009-11-13 16:30:02.232 TVRec(1): HW Tuner: 1->1
2009-11-13 16:30:02.391 AutoExpire: CalcParams(): Max required Free Space: 3.0 GB w/freq: 15 min
2009-11-13 16:30:02.438 Started recording: Judge Judy: channel 1041 on cardid 1, sourceid 1
2009-11-13 16:30:02.489 scheduler: Started recording: Judge Judy: channel 1041 on cardid 1, sourceid 1
2009-11-13 16:30:03.579 Reschedule requested for id 0.
2009-11-13 16:30:03.721 Scheduled 9 items in 0.1 = 0.05 match + 0.09 place
2009-11-13 16:30:03.780 scheduler: Scheduled items: Scheduled 9 items in 0.1 = 0.05 match + 0.09 place
2009-11-13 16:30:05.138 TFW, Error: Opening file '/media/recordings2/mythtv2/myshows/1041_20091113163000.mpg'.
            eno: Permission denied (13)
2009-11-13 16:30:05.191 TVRec(1) Error: RingBuffer '/media/recordings2/mythtv2/myshows/1041_20091113163000.mpg' not open...
2009-11-13 16:30:05.252 TVRec(1): Changing from Watching RecordingOnly to None
2009-11-13 16:30:05.315 Finished recording Judge Judy: channel 1041
2009-11-13 16:30:05.377 scheduler: Finished recording: Judge Judy: channel 1041
2009-11-13 16:30:05.317 Reschedule requested for id 0.
```

The permission denied statement, I thought, was the culprit so I went into a shell window and changed the permission of "myshows"  using :
                 
                             chmod a+rw myshows

When I check permissions with "ls -l", I get the following:

```
drwxrwxrwx 2 frank frank 4096 2009-11-14 13:39 myshows
```

Which I thought would give mythtv permission to read, write, execute in the directory myshows.  However, another attempt yielded: (from mythbackend log):


```
2009-11-14 02:05:02.271 TVRec(1): Changing from None to Watching RecordingOnly
2009-11-14 02:05:02.352 TVRec(1): HW Tuner: 1->1
2009-11-14 02:05:02.453 New DB connection, total: 4
2009-11-14 02:05:02.501 Connected to database 'mythconverg' at host: Frank4
2009-11-14 02:05:02.568 AutoExpire: CalcParams(): Max required Free Space: 3.0 GB w/freq: 15 min
2009-11-14 02:05:02.643 Started recording: The Cosby Show "Day of the Locusts": channel 1051 on cardid 1, sourceid 1
2009-11-14 02:05:02.694 scheduler: Started recording: The Cosby Show "Day of the Locusts": channel 1051 on cardid 1, sourceid 1
2009-11-14 02:05:04.023 TFW, Error: Opening file '/media/recordings2/mythtv2/myshows/1051_20091114020500.mpg'.
            eno: Permission denied (13)
2009-11-14 02:05:04.080 TVRec(1) Error: RingBuffer '/media/recordings2/mythtv2/myshows/1051_20091114020500.mpg' not open...
2009-11-14 02:05:04.133 TVRec(1): Changing from Watching RecordingOnly to None
2009-11-14 02:05:04.196 Finished recording The Cosby Show "Day of the Locusts": channel 1051
2009-11-14 02:05:04.250 scheduler: Finished recording: The Cosby Show "Day of the Locusts": channel 1051
2009-11-14 02:05:04.198 Reschedule requested for id 0.
```


When I use my usual recording process it DOES record and  vies finel  A sample output of mythbackend log for a successful record (to default directory on the main disk) shows:

```
2009-11-14 07:30:02.905 TVRec(1): Changing from None to Watching RecordingOnly
2009-11-14 07:30:02.979 TVRec(1): HW Tuner: 1->1
2009-11-14 07:30:03.072 AutoExpire: CalcParams(): Max required Free Space: 3.0 GB w/freq: 15 min
2009-11-14 07:30:03.120 Started recording: Wild About Animals: channel 1251 on cardid 1, sourceid 1
2009-11-14 07:30:03.172 scheduler: Started recording: Wild About Animals: channel 1251 on cardid 1, sourceid 1
2009-11-14 07:43:16.337 AutoExpire: CalcParams(): Max required Free Space: 3.0 GB w/freq: 15 min
2009-11-14 07:54:03.231 MainServer::ANN Monitor
2009-11-14 07:54:03.304 adding: Frank4 as a client (events: 0)
2009-11-14 07:57:21.943 UPnpMedia: BuildMediaMap - no VideoStartupDir set,  skipping scan.
2009-11-14 07:58:16.493 AutoExpire: CalcParams(): Max required Free Space: 3.0 GB w/freq: 15 min
2009-11-14 08:00:00.552 TVRec(1): Changing from Watching RecordingOnly to None
2009-11-14 08:00:00.660 Finished recording Wild About Animals: channel 1251
2009-11-14 08:00:00.731 scheduler: Finished recording: Wild About Animals: channel 1251

```


What am I doing wrong?  Do I need to add something to the (secondary -  '/media/recordings2/mythtv2/myshows')  storage directory path in backend setup?

Appreciate any help...

---

### Post by klc5555 on 2009-11-14
Your storage directory needs to be owned by 'mythtv' and be in the 'mythtv' group. Looks like owner and group are now both 'frank'. Mythtv does not have permission to read/write from a 'frank' directory.

So:

sudo chown -R mythtv /media/recordings2/mythtv2/myshows

and:

sudo chgrp -R mythtv /media/recordings2/mythtv2/myshows

should do it.

---

### Post by sawbuck on 2009-11-14
klc5555,

Thanks for the tip.  I changed as you suggest and "ls -l" shows it now owned my mythtv.  I've got a sample recording scheduled to test it out.

Somehow I thought giving permission to all would include mythtv.  Guess I'll have to look into the ownership/permission section more thoroughly.

---

### Post by sawbuck on 2009-11-14
klc5555,

It didn't work.

Here's the ownership:

```
frank@Frank4:/media/recordings2/mythtv2$ ls -l
total 4
drwxrwxrwx 2 mythtv mythtv 4096 2009-11-14 13:39 myshows

```

Here's the error report from backend log:

```
2009-11-14 17:00:02.079 TVRec(1): Changing from None to Watching RecordingOnly
2009-11-14 17:00:02.136 TVRec(1): HW Tuner: 1->1
2009-11-14 17:00:02.244 AutoExpire: CalcParams(): Max required Free Space: 3.0 GB w/freq: 15 min
2009-11-14 17:00:02.293 Started recording: House "Son of Coma Guy": channel 1251 on cardid 1, sourceid 1
2009-11-14 17:00:02.345 scheduler: Started recording: House "Son of Coma Guy": channel 1251 on cardid 1, sourceid 1
2009-11-14 17:00:04.523 TFW, Error: Opening file '/media/recordings2/mythtv2/myshows/1251_20091114170000.mpg'.
            eno: Permission denied (13)
2009-11-14 17:00:04.569 TVRec(1) Error: RingBuffer '/media/recordings2/mythtv2/myshows/1251_20091114170000.mpg' not open...
2009-11-14 17:00:04.622 TVRec(1): Changing from Watching RecordingOnly to None
2009-11-14 17:00:04.685 Finished recording House "Son of Coma Guy": channel 1251
2009-11-14 17:00:04.731 scheduler: Finished recording: House "Son of Coma Guy": channel 1251
2009-11-14 17:00:04.688 Reschedule requested for id 0.
```

What now????

---

### Post by klc5555 on 2009-11-15
It's still a permissions/ownership/group tangle of some sort, if not in the 'myshows' directory itself, then somewhere upstream from the 'myshows' directory in the path down from /media/... to .../myshows, assuming the directories on this path all reside on the same physical drive. If this path goes through /home or is owned/grouped somewhere by root or any user other than mythtv, this will have to be straightened out.

It's to prevent problems like this from popping up that Mythbuntu by default sets up all recording/video directories under '/var/lib/mythtv/...'

---

### Post by sawbuck on 2009-11-15
> **klc5555 said:**
> It's still a permissions/ownership/group tangle of some sort, if not in the 'myshows' directory itself, then somewhere upstream from the 'myshows' directory in the path down from /media/... to .../myshows, assuming the directories on this path all reside on the same physical drive. If this path goes through /home or is owned/grouped somewhere by root or any user other than mythtv, this will have to be straightened out.

It's to prevent problems like this from popping up that Mythbuntu by default sets up all recording/video directories under '/var/lib/mythtv/...'

klc5555,

As it turns out it was the path issue.  I wondered about that since I had encountered that issue either with msdos or another OS somewhere in the past. I figured modern day linux might be more direct.  However, after chmod to the directories leading up to the path to give mythtv access it did finally record a snippet with no problem.  Thanks again for the help.

---

