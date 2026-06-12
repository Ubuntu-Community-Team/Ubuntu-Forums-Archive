---
title: "Mythbackend overloading CPU and causing stutter"
date: 2010-06-15
forum: Mythbuntu
---

### Post by ErWenn on 2010-06-15
I have a combined backend/frontend machine running Mythbuntu release 10.04 with two 3 GHz Pentium 4 processors, and 1 GB RAM. Previously I was running version 9.10 and I'd noticed that whenever the backend was recording two different programs simultaneously and I tried to watch a third (previously recorded) program, the CPUs would get so overloaded that the video and audio would start to stutter, rendering things mostly unwatchable. Since upgrading (very messily*) to 10.04, the problem has gotten worse so that often I can't watch a recording even if it's only recording one other program, and sometimes I can't even watch the program as it's being recorded. Looking at the system monitor, I can see that the both CPUs are being nearly maxed out (each at 96-100%) just about anytime anything is being recorded, with the majority (100-115% (it took me a moment to realize that it was measuring out of 200% because of the two processors)) being used by mythbackend.

So I have a couple of questions:

1) Is there any reason why this would have gotten worse after upgrading to 10.04? And is there anything I can do to lessen the problem?

2) Is recording 2 things and watching a third asking too much of my machine?

*The database was corrupted as was the backup of the database, so I had to revert to the last reliable backup I had, from November 2009. I don't know if this has anything to do with anything.

---

### Post by ian dobson on 2010-06-16
Hi,

Could it be that commflagging in really hitting your CPU. Note that the commflag job starts just after the recording starts (+2-5minutes) and scans through the recording looking for commercial breaks. This puts the I/O system under load as is has to handle writing to the file and reading at the same time causing the disk to search like mad.

my quad core can handle recording 6 programs at the same time (2HD and 4 SD) as well as watching a 7th program on a remote frontend. The most important thing about my backend server is that it has 8Gb ram and a 6Tb RAID5 array (read/write at about 250-300mb sec). The cpu load from the backend process is almost always less than 5%.

Also is your mysql database on the same drive as your recordings? This will cause the drive to thrash as the recording and the seek table are being written at the same time.

Maybe try adding another Gb ram or limiting the system to only one commflag job at a time.

Regards
Ian Dobson

---

### Post by ErWenn on 2010-06-16
Thanks for your suggestions, Ian.

The commercial flagger is not running while the backend is recording anything. I've got it set to only run one job at a time and not to start commflag while recording. (Also, I can see on the system monitor that the flagger isn't running.)  For the record, the jumpiness problem starts immediately after recording begins.

I'm pretty sure it's not a memory problem as the system monitor shows that only half of my existing RAM is being used.

I'm not sure exactly where the mysql database is stored (I knew at some point, but now I can't remember where it is). How would I go about figuring that out? This could be related, but that wouldn't explain the high CPU usage rates.

I watched the CPU rates more closely while I was recording something  and the percentage used by mythbackend seems to oscillate every 5-10 seconds or so from about 65% up to 90-110%. That seems to match the timing on the playback stutters, so I'm feeling very strongly about the connection between the excessive CPU usage and the jumpiness.

Does anyone else have any suggestions or theories on what's causing the problem?

---

### Post by Senkoboy on 2010-06-16
Download a program called Top.  It displays a listing of the most CPU-intensive tasks. Maybe it will show you some more information.

[http://en.wikipedia.org/wiki/Top_%28Unix%29]("http://en.wikipedia.org/wiki/Top_%28Unix%29")

---

### Post by tgm4883 on 2010-06-16
> **Senkoboy said:**
> Download a program called Top.  It displays a listing of the most CPU-intensive tasks. Maybe it will show you some more information.

[http://en.wikipedia.org/wiki/Top_%28Unix%29]("http://en.wikipedia.org/wiki/Top_%28Unix%29")

couple things. 

[LIST=1]
[*]Top is installed by default.  
[*]The OP already stated it was mythbackend using the CPU
[/LIST]

What do the backend logs say during this time?

---

### Post by ErWenn on 2010-06-16
> **tgm4883 said:**
> 
What do the backend logs say during this time?

I only barely know what I'm doing, so I'm not sure what's relevant here, so I've included a few pages worth of log here. The only thing that looks... uh... strange to me is the "strange error flushing buffer ..." messages at around 22:57.

```
2010-06-16 22:32:03.078 Finished recording South Park "Go God Go XII": channel 1062
2010-06-16 22:32:03.270 ProgramInfo(): Updated pathname '':'' -> '1062_20100616220000.nuv'
2010-06-16 22:32:03.347 ProgramInfo(): Updated pathname '':'' -> '1062_20100616220000.nuv'
2010-06-16 22:32:18.549 mythbackend version: branches/release-0-23-fixes [24158] www.mythtv.org
2010-06-16 22:32:18.607 Using runtime prefix = /usr
2010-06-16 22:32:18.619 Using configuration directory = /home/mythtv/.mythtv
2010-06-16 22:32:18.725 Empty LocalHostName.
2010-06-16 22:32:18.743 Using localhost value of Devo
2010-06-16 22:32:19.729 New DB connection, total: 1
2010-06-16 22:32:20.247 Connected to database 'mythconverg' at host: localhost
2010-06-16 22:32:20.265 Closing DB connection named 'DBManager0'
2010-06-16 22:32:20.302 Connected to database 'mythconverg' at host: localhost
2010-06-16 22:32:20.425 Current MythTV Schema Version (DBSchemaVer): 1254
2010-06-16 22:32:20.476 ProgramInfo(): Updated pathname '':'' -> '1062_20100616220000.nuv'
2010-06-16 22:32:29.144 Preview: Grabbed preview '/var/lib/mythtv/recordings/1062_20100616220000.nuv' 720x480@184s
2010-06-16 22:32:33.111 ~MythContext waiting for threads to exit.
2010-06-16 22:33:05.080 Scheduled 978 items in 63.9 = 0.02 match + 63.86 place
2010-06-16 22:42:50.701 ProgramInfo(): Updated pathname '':'' -> '1044_20100616205800.nuv'
2010-06-16 22:42:50.972 MainServer::ANN Playback
2010-06-16 22:42:50.987 adding: Devo as a client (events: 0)
2010-06-16 22:42:53.450 RecBase(2:/dev/video0): GetKeyframePositions(6284,9223372036854775807,#4) out of 6126
2010-06-16 22:44:18.964 ProgramInfo(): Updated pathname '':'' -> '1044_20100616205800.nuv'
2010-06-16 22:44:19.014 ProgramInfo(): Updated pathname '':'' -> '1044_20100616205800.nuv'
2010-06-16 22:44:20.179 ProgramInfo(): Updated pathname '':'' -> '1044_20100616205800.nuv'
2010-06-16 22:45:55.207 AutoExpire: CalcParams(): Max required Free Space: 2.0 GB w/freq: 15 min
2010-06-16 22:46:19.108 ProgramInfo(): Updated pathname '':'' -> '1062_20100616085800.nuv'
2010-06-16 22:47:26.638 ProgramInfo(): Updated pathname '':'' -> '1062_20100616085800.nuv'
2010-06-16 22:47:28.911 ProgramInfo(): Updated pathname '':'' -> '1062_20100616085800.nuv'
2010-06-16 22:47:29.120 ProgramInfo(): Updated pathname '':'' -> '1062_20100616085800.nuv'
2010-06-16 22:47:29.231 ProgramInfo(): Updated pathname '':'' -> '1062_20100616085800.nuv'
2010-06-16 22:47:32.188 ProgramInfo(): Updated pathname '':'' -> '1062_20100616085800.nuv'
2010-06-16 22:47:36.825 Reschedule requested for id 0.
2010-06-16 22:47:54.224 Scheduled 978 items in 17.3 = 0.01 match + 17.29 place
2010-06-16 22:56:00.139 Reschedule requested for id 0.
2010-06-16 22:56:14.105 Scheduled 978 items in 13.9 = 0.00 match + 13.85 place
2010-06-16 22:56:29.320 TVRec(3): ASK_RECORDING 3 29 0 0
2010-06-16 22:57:01.519 ProgramInfo(): Updated pathname '':'' -> '1028_20100616225700.nuv'
2010-06-16 22:57:01.616 TVRec(3): Changing from None to RecordingOnly
2010-06-16 22:57:01.643 TVRec(3): HW Tuner: 3->3
2010-06-16 22:57:02.285 TVRec(3): rec->GetFileName(): '/var/lib/mythtv/recordings/1028_20100616225700.nuv'
strange error flushing buffer ...
strange error flushing buffer ...
strange error flushing buffer ...
strange error flushing buffer ...
strange error flushing buffer ...
2010-06-16 22:57:02.587 AutoExpire: CalcParams(): Max required Free Space: 3.0 GB w/freq: 15 min
2010-06-16 22:57:02.666 Started recording: Top Chef "What's Your Constituency?": channel 1028 on cardid 3, sourceid 1
2010-06-16 23:00:55.793 AutoExpire: CalcParams(): Max required Free Space: 3.0 GB w/freq: 15 min
2010-06-16 23:02:00.876 TVRec(2): Changing from RecordingOnly to None
2010-06-16 23:02:00.884 ProgramInfo(): Updated pathname '':'' -> '1044_20100616205800.nuv'
2010-06-16 23:02:00.909 Finished recording MythBusters "25 Best Busted Myths": channel 1044
2010-06-16 23:02:00.926 Reschedule requested for id 0.
2010-06-16 23:02:01.014 ProgramInfo(): Updated pathname '':'' -> '1044_20100616205800.nuv'
2010-06-16 23:02:01.058 ProgramInfo(1044_20100616205800.nuv), Error: Unknown type, recording width was 0
2010-06-16 23:02:01.701 ProgramInfo(): Updated pathname '':'' -> '1044_20100616205800.nuv'
2010-06-16 23:02:01.705 Finished recording MythBusters "25 Best Busted Myths": channel 1044
2010-06-16 23:02:01.774 ProgramInfo(): Updated pathname '':'' -> '1044_20100616205800.nuv'
2010-06-16 23:02:05.577 mythbackend version: branches/release-0-23-fixes [24158] www.mythtv.org
2010-06-16 23:02:05.586 Using runtime prefix = /usr
2010-06-16 23:02:05.613 Using configuration directory = /home/mythtv/.mythtv
2010-06-16 23:02:05.620 Empty LocalHostName.
2010-06-16 23:02:05.631 Using localhost value of Devo
2010-06-16 23:02:05.922 New DB connection, total: 1
2010-06-16 23:02:06.043 Connected to database 'mythconverg' at host: localhost
2010-06-16 23:02:06.044 Closing DB connection named 'DBManager0'
2010-06-16 23:02:06.060 Connected to database 'mythconverg' at host: localhost
2010-06-16 23:02:06.125 Current MythTV Schema Version (DBSchemaVer): 1254
2010-06-16 23:02:06.149 ProgramInfo(): Updated pathname '':'' -> '1044_20100616205800.nuv'
2010-06-16 23:02:10.029 Preview: Grabbed preview '/var/lib/mythtv/recordings/1044_20100616205800.nuv' 720x480@184s
2010-06-16 23:02:10.802 ~MythContext waiting for threads to exit.
2010-06-16 23:02:17.152 Scheduled 976 items in 16.1 = 0.01 match + 16.07 place

```

---

### Post by ian dobson on 2010-06-17
Hi,

This looks really strange. Can you answer afew questions:-

1) What tuner are you using
2) Whats the load on the system when no recording is active (uptime from the terminal after waiting afew minutes without a recording active)
3) Whats the load on the system when a recording is active (uptime from the terminal after waiting afew minutes with a recording active)
4) If your using DVB IS EIT enabled (EPG over the wire)
5) The only thing I see is that the scheduler is taking a really long time (Scheduled 976 items in 16.1) and do you really have over 900 programs that you want to record? On my box I see "Scheduled 127 items in 0.5 = 0.12 match + 0.33 place" as my TV provider brings the same program several times within afew days.
6) Why are your recordings .nuv files (thats only used for older tuners that don't support mpeg hardware encoding).

Regards
Ian Dobson

---

### Post by ErWenn on 2010-06-19
> **ian dobson said:**
> Hi,

This looks really strange. Can you answer afew questions:-

1) What tuner are you using

I have two Pinnacle PCTV HD 800i cards.

> 2) Whats the load on the system when no recording is active (uptime from the terminal after waiting afew minutes without a recording active)

Shortly after sitting around for an hour or so not doing anything, uptime says:[INDENT] load average: 0.12, 0.16, 0.16
[/INDENT]A few minutes later, it says:[INDENT] load average: 0.27, 0.22, 0.18
[/INDENT]And a few minutes after that:
[INDENT]load average: 0.17, 0.15, 0.16
[/INDENT]

When it's playing something back, uptime says:

[INDENT]load average: 2.54, 1.84, 1.14

[/INDENT]A few minutes later:
[INDENT]load average: 1.66, 1.92, 1.53
[/INDENT]
And one more time:
[INDENT]load average: 1.84, 1.71, 1.51
[/INDENT]

> 3) Whats the load on the system when a recording is active (uptime from the terminal after waiting afew minutes with a recording active)

While recording one show and watching nothing:
[INDENT]load average: 1.06, 1.16, 1.35
[/INDENT]
A few minutes later:
[INDENT]load average: 1.19, 1.19, 1.28

[/INDENT]And one more time:
[INDENT]load average: 1.51, 1.31, 1.26
[/INDENT]
> 4) If your using DVB IS EIT enabled (EPG over the wire)

I don't actually know what this means. How would I go about figuring that out?


> 5) The only thing I see is that the scheduler is taking a really long time (Scheduled 976 items in 16.1) and do you really have over 900 programs that you want to record? On my box I see "Scheduled 127 items in 0.5 = 0.12 match + 0.33 place" as my TV provider brings the same program several times within afew days.

I'm not actually recording 900 programs. I did some double-checking and it looks like it's counting all the showings of all the episodes of programs for which there's a rule, even showings that won't be recorded because that episode is being recorded at a different time or because it's a rerun or whatnot. I did some cleaning to get rid of some rules that aren't likely to record anything for a long time, but there's still a good 600 or so programs that it's "scheduling".

> 6) Why are your recordings .nuv files (thats only used for older tuners that don't support mpeg hardware encoding).

I have absolutely no idea. I don't recall changing any settings like that. In fact, I don't even know how to make such a change.

---

### Post by ian dobson on 2010-06-20
Hi,

Doing abit of reading up on the Pinnacle PCTV HD 800i, it looks as if it's a dual tuner (digital and analog). Which part are you using?

Can you go to myth-setup and check if you have the card defined as a DVB card or not for the digital part of the card. Have a look here:- [http://www.mythtv.org/wiki/Pinnacle_PCTV_HD_Card_(800i](http://www.mythtv.org/wiki/Pinnacle_PCTV_HD_Card_(800i))

I imagine the high load on your system is being caused by the video being transcoded from mpeg to nuv (if your recordings are actualy being transcoded, but it looks so from the log file you included).

Regards
Ian Dobson

---

### Post by ErWenn on 2010-06-27
> **ian dobson said:**
> Hi,

Doing abit of reading up on the Pinnacle PCTV HD 800i, it looks as if it's a dual tuner (digital and analog). Which part are you using? 

Can you go to myth-setup and check if you have the card defined as a DVB  card or not for the digital part of the card. Have a look here:- [http://www.mythtv.org/wiki/Pinnacle_PCTV_HD_Card_(800i]("http://www.mythtv.org/wiki/Pinnacle_PCTV_HD_Card_%28800i"))


I'm using the analog part of the card. When I set up the digital part of the card (as a DVB card), the analog part of the card stops working properly (I get about half a second of video and audio whenever I start watching or recording with the analog part card and then it goes to a dark static with white noise). So I currently only have the analog parts of the cards set up. I can live with that, but not being able to watch and record at the same time is a serious annoyance.

> 
I imagine the high load on your system is being caused by the video being transcoded from mpeg to nuv (if your recordings are actualy being transcoded, but it looks so from the log file you included).


I don't think there's a formal transcoding process going on. The transcode process isn't running when I get the problems, and I have it set not to run any transcode or commercial flag jobs until after the recording has finished. But I guess maybe it's transcoding as part of the main backend process or something. If that's the case, do you have any idea how to make it stop?

Thanks for all your help.

---

### Post by ErWenn on 2010-06-27
Did a little reading, and it looks like .nuv is the standard MythTV format unless you're recording directly from a digital card. Since I'm using an analog card (or at least the analog part of the card), this seems perfectly normal.

I still haven't figured out the "strange error flushing buffer..." messages. Anyone have any ideas?

---

### Post by tgm4883 on 2010-06-27
> **ErWenn said:**
> Did a little reading, and it looks like .nuv is the standard MythTV format unless you're recording directly from a digital card. Since I'm using an analog card (or at least the analog part of the card), this seems perfectly normal.

I still haven't figured out the "strange error flushing buffer..." messages. Anyone have any ideas?

Nuv is for software encoder cards, which I urge against. Digital or Analog cards with hardware encoders are much better

---

### Post by ErWenn on 2010-06-27
> **tgm4883 said:**
> Nuv is for software encoder cards, which I urge against. Digital or Analog cards with hardware encoders are much better

I'd love to go with a hardware encoder, but I don't know if my card supports it for analog recording, and if it does, I don't know how to set it up properly.

Update: I was able to get a slight improvement by changing the playback profile to "Slim" from "CPU++". Now it can go for a few minutes without skipping much at all, but eventually it seems to start stuttering again (although not quite as frequently as before).

---

### Post by tgm4883 on 2010-06-27
> **ErWenn said:**
> I'd love to go with a hardware encoder, but I don't know if my card supports it for analog recording, and if it does, I don't know how to set it up properly.

Update: I was able to get a slight improvement by changing the playback profile to "Slim" from "CPU++". Now it can go for a few minutes without skipping much at all, but eventually it seems to start stuttering again (although not quite as frequently as before).

AFAICT, your card is not a hardware encoder

---

### Post by ian dobson on 2010-06-28
Hi ErWenn,

Where abouts are you? I have a PVR150 and a PVR500 (PAL) they are analog cards with a hardware encode on board, gathering dust (gone over to DVB-C about 12months ago).

If you can make use of them we can come to a deal.

Regards
Ian Dobson

---

### Post by ErWenn on 2010-06-28
> **ian dobson said:**
> Hi ErWenn,

Where abouts are you? I have a PVR150 and a PVR500 (PAL) they are analog cards with a hardware encode on board, gathering dust (gone over to DVB-C about 12months ago).

If you can make use of them we can come to a deal.

Regards
Ian Dobson

I'm in Bloomington, Indiana. A deal is a possibility, although at the moment, Comcast is making grumblings about switching to entirely digital, in which case I *should* be able to switch to the DVB parts of the cards and get all the channels (and it won't matter that I can't use the analog parts of the cards). Also, I'm leaving town for 3 weeks on Thursday. So I think I'll hold out a bit longer before trying to change out the hardware.

Thanks for the offer, though. If I get back and I can't fix the problem and you still have them, I'll drop you a line.

Thanks for your help,
Erik

---

### Post by ian dobson on 2010-06-28
Hi,

There's no point in a deal, your analog is NTSC(USA) and the cards I have a PAL (Europe).

Regards
Ian Dobson

---

### Post by tgm4883 on 2010-06-28
> **ian dobson said:**
> Hi,

There's no point in a deal, your analog is NTSC(USA) and the cards I have a PAL (Europe).

Regards
Ian Dobson

What a coincidence. I too have a PVR500 and PVR150 gathering dust in a box. Mine though are NTSC(USA)

---

### Post by Johnius on 2010-12-10
Your analog problem, if it is the same as mine, is that the DVB is turning on.  The DVB is set to actively scan for EIT data by default.  If you open MythTVBackend -> Capture Cards -> DVB card -> Record options and then untick the "Actively Scan for EIT Data" box, it should work.  I messed around with a LOT of settings today and managed to get rid of the "strange error flushing buffer" message (I think by trying MPEG, MPEG-2 settings [which naturally don't work, but I think it fixed my buffer]).  Best of luck.

---

