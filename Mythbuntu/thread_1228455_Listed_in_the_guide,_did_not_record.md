---
title: "Listed in the guide, did not record"
date: 2009-07-31
forum: Mythbuntu
---

### Post by mathog on 2009-07-31
Last night a channel (52_2) set to record didn't.  I have seen this happen before when the schedule was screwed up and missing the schedule for that channel, but in this case there was the show nicely highlighted like any other show being recorded.  Our first hint that all was not well came when my wife tried to view the recording 20 minutes after it started, and it gave a message like "can not open file" or "could not find file".  

Today I tuned in that channel with "Watch TV" and it came right up.

Here are the backend logs.  

```
2009-07-30 20:55:42.418 HDHRChan(1011f855/1): device found at address 192.168.0.103
2009-07-30 20:56:50.080 Reschedule requested for id -1.
2009-07-30 20:56:50.488 Scheduled 14 items in 0.4 = 0.32 match + 0.08 place
2009-07-30 20:58:17.148 AutoExpire: CalcParams(): Max required Free Space: 3.0 GB w/freq: 15 min
2009-07-30 20:59:00.621 Reschedule requested for id 0.
2009-07-30 20:59:00.959 Scheduled 14 items in 0.3 = 0.02 match + 0.32 place
2009-07-30 20:59:29.056 TVRec(2): ASK_RECORDING 2 29 0 0
2009-07-30 21:00:01.793 Finished recording Bones "The Doctor in the Den": channel 1111
2009-07-30 21:00:02.265 AutoExpire: CalcParams(): Max required Free Space: 3.0 GB w/freq: 15 min
2009-07-30 21:00:03.870 Using runtime prefix = /usr
2009-07-30 21:00:03.919 Empty LocalHostName.
2009-07-30 21:00:03.948 Using localhost value of mediahog
2009-07-30 21:00:04.087 New DB connection, total: 1
2009-07-30 21:00:04.162 Connected to database 'mythconverg' at host: localhost
2009-07-30 21:00:04.176 Closing DB connection named 'DBManager0'
2009-07-30 21:00:04.178 Connected to database 'mythconverg' at host: localhost
2009-07-30 21:00:04.187 New DB connection, total: 2
2009-07-30 21:00:04.190 Connected to database 'mythconverg' at host: localhost
2009-07-30 21:00:04.199 Current Schema Version: 1214
2009-07-30 21:00:04.221 TVRec(1): RingBufferChanged()
2009-07-30 21:00:04.275 Finished recording Bones "The Doctor in the Den": channel 1111
2009-07-30 21:00:04.310 TVRec(2): Changing from None to RecordingOnly
2009-07-30 21:00:04.433 TVRec(2): HW Tuner: 2->2
2009-07-30 21:00:05.813 AutoExpire: CalcParams(): Max required Free Space: 3.0 GB w/freq: 8 min
2009-07-30 21:00:05.821 Started recording: Ni¤os Ricos Pobres Padres: channel 1522 on cardid 2, sourceid 1
2009-07-30 21:00:06.114 Could not find channel 52_2 in TVCT
2009-07-30 21:00:06.117 
VCT Terra: channels(1) tsid(0x101) seclength(62)
Channel #0 name(KVEA-HD) 52-1 mod(ATSC 8-VSB) cTSID(0x101)
 pnum(3) ETM_loc(1) access_ctrl(0) hidden(0) hide_guide(1) service_type(2) source_id(1)
 descriptors length(17) count(1)
  Service Location Descriptor (0xa1) length(15)


2009-07-30 21:00:06.479 Could not find channel 52_2 in TVCT
2009-07-30 21:00:06.480 
VCT Terra: channels(1) tsid(0x101) seclength(62)
Channel #0 name(KVEA-HD) 52-1 mod(ATSC 8-VSB) cTSID(0x101)
 pnum(3) ETM_loc(1) access_ctrl(0) hidden(0) hide_guide(1) service_type(2) source_id(1)
 descriptors length(17) count(1)
  Service Location Descriptor (0xa1) length(15)


2009-07-30 21:00:06.835 Could not find channel 52_2 in TVCT
2009-07-30 21:00:06.954 
VCT Terra: channels(1) tsid(0x101) seclength(62)
Channel #0 name(KVEA-HD) 52-1 mod(ATSC 8-VSB) cTSID(0x101)
 pnum(3) ETM_loc(1) access_ctrl(0) hidden(0) hide_guide(1) service_type(2) source_id(1)
 descriptors length(17) count(1)
  Service Location Descriptor (0xa1) length(15)


2009-07-30 21:00:07.078 AFD: Opened codec 0x9a328d0, id(MPEG2VIDEO) type(Video)
2009-07-30 21:00:07.082 AFD: codec AC3 has 6 channels
2009-07-30 21:00:07.084 AFD: Opened codec 0x9a32ec0, id(AC3) type(Audio)
2009-07-30 21:00:07.085 AFD: codec AC3 has 2 channels
2009-07-30 21:00:07.086 AFD: Opened codec 0x9a334b0, id(AC3) type(Audio)
2009-07-30 21:00:07.196 Could not find channel 52_2 in TVCT
2009-07-30 21:00:07.198 
etc.
```

when one tries to watch the missing show (there is an entry for it under "watch recordings" a zillion of these show up in the backend log:

```
2009-07-31 19:40:11.071 ProgramInfo, Error: GetPlaybackURL: '1522_20090730210000.mpg' should be local, but it can not be found.


2009-07-31 19:40:11.102 ProgramInfo, Error: GetPlaybackURL: '1522_20090730210000.mpg' should be local, but it can not be found.
2009-07-31 19:40:11.138 ProgramInfo, Error: GetPlaybackURL: '1522_20090730210000.mpg' should be local, but it can not be found.
2009-07-31 19:40:11.169 ProgramInfo, Error: GetPlaybackURL: '1522_20090730210000.mpg' should be local, but it can not be found.
2009-07-31 19:40:11.202 ProgramInfo, Error: GetPlaybackURL: '1522_20090730210000.mpg' should be local, but it can not be found.
2009-07-31 19:40:11.234 ProgramInfo, Error: GetPlaybackURL: '1522_20090730210000.mpg' should be local, but it can not be found.

```

The file really is missing, which makes sense if the recording failed.

Any ideas what might have caused this?  We were watching a DVD part of the time it wasn't recording, but it's hard to see how that could make it not find a channel.

Thanks,

---

### Post by uncle hammy on 2009-08-01
The most obvious (not necessarily correct, mind you) answer to me is the tuner failed to get a signal lock before it timed out when it tried to tune into that channel do perform the recording.

Being able to tune it today, or even 5 minutes after the scheduled start time doesn't mean there was an issue (weather, station, etc) problem at the actual time the recording was to start.

---

### Post by mathog on 2009-08-04
> **uncle hammy said:**
> The most obvious (not necessarily correct, mind you) answer to me is the tuner failed to get a signal lock before it timed out when it tried to tune into that channel do perform the recording.

Being able to tune it today, or even 5 minutes after the scheduled start time doesn't mean there was an issue (weather, station, etc) problem at the actual time the recording was to start.

OK, that is officially not it.  It did it again on the same program at the same time.  I stopped the failed recording (could not find file) and tried to start it again, but nothing.  Then tuned to it.  No problem.  No way the transmitter just happened to come back to life in that 4 seconds.  It looks like there is some sort of database corruption.  I will try later to set it to record automatically on the same channel at some other time to see if it is the program or the channel.  My money is on the channel.

Who can translate the error messages above and suggest where in the database to look for the corrupted record?

Thanks.

---

### Post by mathog on 2009-08-05
In the MythTV mailing list Fred Squires wrote:

> try changing the Use Quick Tuning
setting in mythtvsetup on the Input Connections screen from
Live TV Only to Always. I had similar problems with one channel,
and this change fixed it for me.


This seems to have been the problem, since at least the first test recording on the problem channel worked.  When I get a chance I will try to break live tv by flipping this setting to Never, and if that does it, then file a bug report.

---

