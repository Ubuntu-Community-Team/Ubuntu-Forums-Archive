---
title: "Recordings no longer work"
date: 2007-10-25
forum: Mythbuntu
---

### Post by crmullins on 2007-10-25
I installed 7.10 mythbuntu beta three weeks ago. I had everything setup nicely and encountered no problems until around 8:37pm yesterday.

My recordings from 8:30pm-9:00pm and 8:30pm-10:00pm were cut short abruptly at 8:37pm and now all future scheduled recordings won't record.

Here's my mythbackend.log:
```

2007-10-23 20:00:02.983 TVRec(1): Changing from None to RecordingOnly
2007-10-23 20:00:02.988 TVRec(1): HW Tuner: 1->1
2007-10-23 20:00:03.231 MPEGRec(/dev/video0) Error: Error getting codec params using old IVTV ioctl
			eno: Bad address (14)
2007-10-23 20:00:03.255 Started recording: Cavemen "The Mascot": channel 1007 on cardid 1, sourceid 1
2007-10-23 20:00:03.261 scheduler: Started recording: Cavemen "The Mascot": channel 1007 on cardid 1, sourceid 1
2007-10-23 20:30:01.004 TVRec(1): Changing from RecordingOnly to None
2007-10-23 20:30:01.029 Finished recording Cavemen "The Mascot": channel 1007
2007-10-23 20:30:01.050 scheduler: Finished recording: Cavemen "The Mascot": channel 1007
2007-10-23 20:30:01.131 Finished recording Cavemen "The Mascot": channel 1007
0: start_time: 0.036 duration: 161.700
1: start_time: 0.026 duration: 161.676
stream: start_time: 0.289 duration: 1796.773 bitrate=7185 kb/s
2007-10-23 20:30:01.204 AFD: Opened codec 0xe5e8a0, id(MPEG2VIDEO) type(Video)
2007-10-23 20:30:01.209 AFD: Opened codec 0xc08c80, id(MP2) type(Audio)
2007-10-23 20:30:02.091 TVRec(1): Changing from None to RecordingOnly
2007-10-23 20:30:02.098 TVRec(1): HW Tuner: 1->1
2007-10-23 20:30:02.273 MPEGRec(/dev/video0) Error: Error getting codec params using old IVTV ioctl
			eno: Bad address (14)
2007-10-23 20:30:02.300 Started recording: Carpoolers "Down for the Count": channel 1007 on cardid 1, sourceid 1
2007-10-23 20:30:02.306 scheduler: Last message repeated 1 times: Finished recording: Cavemen "The Mascot": channel 1007
2007-10-23 20:30:02.310 scheduler: Started recording: Carpoolers "Down for the Count": channel 1007 on cardid 1, sourceid 1
2007-10-23 20:30:02.349 TVRec(2): Changing from None to RecordingOnly
2007-10-23 20:30:02.354 TVRec(2): HW Tuner: 2->2
2007-10-23 20:30:02.518 MPEGRec(/dev/video1) Error: Error getting codec params using old IVTV ioctl
			eno: Bad address (14)
2007-10-23 20:30:02.520 Started recording: The Biggest Loser: channel 1003 on cardid 2, sourceid 1
2007-10-23 20:30:02.550 scheduler: Started recording: The Biggest Loser: channel 1003 on cardid 2, sourceid 1
2007-10-23 20:30:03.620 Reschedule requested for id 0.
2007-10-23 20:30:04.125 Scheduled 69 items in 0.5 = 0.00 match + 0.50 place
2007-10-23 20:30:04.128 scheduler: Scheduled items: Scheduled 69 items in 0.5 = 0.00 match + 0.50 place
2007-10-23 20:30:51.495 JobQueue: Commercial Flagging Starting for Cavemen "The Mascot" recorded from channel 1007 at Tue Oct 23 20:00:00 2007
2007-10-23 20:30:51.501 commflag: Commercial Flagging Starting: Cavemen "The Mascot" recorded from channel 1007 at Tue Oct 23 20:00:00 2007
2007-10-23 20:30:52.518 Using runtime prefix = /usr
2007-10-23 20:30:52.661 New DB connection, total: 1
2007-10-23 20:30:52.685 Connected to database 'mythconverg' at host: localhost
2007-10-23 20:30:52.692 New DB connection, total: 2
2007-10-23 20:30:52.693 Connected to database 'mythconverg' at host: localhost
2007-10-23 20:30:52.711 Connecting to backend server: 127.0.0.1:6543 (try 1 of 5)
2007-10-23 20:30:52.713 Using protocol version 31
2007-10-23 20:30:52.714 MainServer::HandleAnnounce Monitor
2007-10-23 20:30:52.719 adding: mythserver as a client (events: 0)
2007-10-23 20:30:52.720 MainServer::HandleAnnounce Monitor
2007-10-23 20:30:52.721 adding: mythserver as a client (events: 1)
0: start_time: 0.036 duration: 161.700
1: start_time: 0.026 duration: 161.676
stream: start_time: 0.289 duration: 1796.773 bitrate=7185 kb/s
2007-10-23 20:30:52.768 AFD: Opened codec 0x73c730, id(MPEG2VIDEO) type(Video)
2007-10-23 20:30:52.785 AFD: Opened codec 0x73cbd0, id(MP2) type(Audio)
2007-10-23 20:36:52.065 Using runtime prefix = /usr
2007-10-23 20:36:52.685 New DB connection, total: 1
2007-10-23 20:36:52.772 Connected to database 'mythconverg' at host: localhost
2007-10-23 20:36:52.954 Current Schema Version: 1160
Starting up as the master server.
2007-10-23 20:36:53.129 mythbackend: MythBackend started as master server
2007-10-23 20:36:53.247 New DB connection, total: 2
2007-10-23 20:36:53.250 Connected to database 'mythconverg' at host: localhost
2007-10-23 20:36:53.298 EITHelper: localtime offset -7:00:00 
2007-10-23 20:36:53.305 New DB connection, total: 3
2007-10-23 20:36:53.311 Connected to database 'mythconverg' at host: localhost
2007-10-23 20:36:53.507 EITHelper: localtime offset -7:00:00 
2007-10-23 20:36:53.673 New DB scheduler connection
2007-10-23 20:36:53.683 Connected to database 'mythconverg' at host: localhost
2007-10-23 20:36:53.804 DB Error (UpdateAborted):
Query was:
UPDATE oldrecorded SET recstatus = -4   WHERE recstatus = -2
Driver error was [2/145]:
QMYSQL3: Unable to execute query
Database error was:
Table './mythconverg/oldrecorded' is marked as crashed and should be repaired

2007-10-23 20:36:53.946 QMulticastSocket: setsockopt - IP_ADD_MEMBERSHIP Error
2007-10-23 20:36:54.709 QMulticastSocket: setsockopt - IP_ADD_MEMBERSHIP Error
2007-10-23 20:36:56.098 Main::Registering HttpStatus Extension
2007-10-23 20:36:56.146 QMulticastSocket: setsockopt - IP_ADD_MEMBERSHIP Error
2007-10-23 20:36:56.151 mythbackend version: 0.20.20070821-1 www.mythtv.org
2007-10-23 20:36:56.370 Enabled verbose msgs:  important general
2007-10-23 20:36:56.422 AutoExpire: Found 2 recorders w/max rate of 144 MiB/min
2007-10-23 20:36:56.425 AutoExpire: Required Free Space: 3.1 GB w/freq: 10 min
2007-10-23 20:36:56.540 Reschedule requested for id -1.
2007-10-23 20:37:00.445 DB Error (AddNewRecords):
Query was:
SELECT DISTINCT channel.chanid, channel.sourceid, program.starttime, program.endtime, program.title, program.subtitle, program.description, channel.channum, channel.callsign, channel.name, oldrecorded.endtime IS NOT NULL AS oldrecduplicate, program.category, record.recpriority, record.dupin, recorded.endtime IS NOT NULL AS recduplicate, oldfind.findid IS NOT NULL AS findduplicate, record.type, record.recordid, program.starttime - INTERVAL record.startoffset minute AS recstartts, program.endtime + INTERVAL record.endoffset minute AS recendts, program.previouslyshown, record.recgroup, record.dupmethod, channel.commfree, capturecard.cardid, cardinput.cardinputid, UPPER(cardinput.shareable) = 'Y' AS shareable, program.seriesid, program.programid, program.category_type, program.airdate, program.stars, program.originalairdate, record.inactive, record.parentid, (CASE record.type   WHEN 6    THEN record.findid   WHEN 9    THEN to_days(date_sub(program.starttime, interval                 time_format(record.findtime, '%H:%i') hour_minute))   WHEN 10    THEN floor((to_days(date_sub(program.starttime, interval                time_format(record.findtime, '%H:%i') hour_minute)) -                record.findday)/7) * 7 + record.findday   WHEN 7    THEN record.findid   ELSE 0  END) , record.playgroup, oldrecstatus.recstatus, oldrecstatus.reactivate, channel.recpriority + cardinput.recpriority, record.prefinput, program.hdtv, program.closecaptioned, program.first, program.last, program.stereo FROM recordmatch  INNER JOIN record ON (recordmatch.recordid = record.recordid)  INNER JOIN program ON (recordmatch.chanid = program.chanid AND                         recordmatch.starttime = program.starttime AND                         recordmatch.manualid = program.manualid)  INNER JOIN channel ON (channel.chanid = program.chanid)  INNER JOIN cardinput ON (channel.sourceid = cardinput.sourceid)  INNER JOIN capturecard ON (capturecard.cardid = cardinput.cardid)  LEFT JOIN oldrecorded as oldrecstatus ON   ( oldrecstatus.station = channel.callsign AND     oldrecstatus.starttime = program.starttime AND     oldrecstatus.title = program.title )  LEFT JOIN oldrecorded ON   (     record.dupmethod > 1 AND     oldrecorded.duplicate <> 0 AND     program.title = oldrecorded.title      AND      (       (program.programid <> '' AND program.generic = 0        AND program.programid = oldrecorded.programid)       OR       (oldrecorded.findid <> 0 AND         oldrecorded.findid = (CASE record.type   WHEN 6    THEN record.findid   WHEN 9    THEN to_days(date_sub(program.starttime, interval                 time_format(record.findtime, '%H:%i') hour_minute))   WHEN 10    THEN floor((to_days(date_sub(program.starttime, interval                time_format(record.findtime, '%H:%i') hour_minute)) -                record.findday)/7) * 7 + record.findday   WHEN 7    THEN record.findid   ELSE 0  END) )       OR       (        program.generic = 0        AND        (program.programid = '' OR oldrecorded.programid = '')        AND        (((record.dupmethod & 0x02) = 0) OR (program.subtitle <> ''           AND program.subtitle = oldrecorded.subtitle))        AND        (((record.dupmethod & 0x04) = 0) OR (program.description <> ''           AND program.description = oldrecorded.description))       )      )   )  LEFT JOIN recorded ON   (     record.dupmethod > 1 AND     recorded.duplicate <> 0 AND     program.title = recorded.title AND     recorded.recgroup <> 'LiveTV'      AND      (       (program.programid <> '' AND program.generic = 0        AND program.programid = recorded.programid)       OR       (recorded.findid <> 0 AND         recorded.findid = (CASE record.type   WHEN 6    THEN record.findid   WHEN 9    THEN to_days(date_sub(program.starttime, interval                 time_format(record.findtime, '%H:%i') hour_minute))   WHEN 10    THEN floor((to_days(date_sub(program.starttime, interval                time_format(record.findtime, '%H:%i') hour_minute)) -                record.findday)/7) * 7 + record.findday   WHEN 7    THEN record.findid   ELSE 0  END) )       OR       (        program.generic = 0        AND        (program.programid = '' OR recorded.programid = '')        AND        (((record.dupmethod & 0x02) = 0) OR (program.subtitle <> ''           AND program.subtitle = recorded.subtitle))        AND        (((record.dupmethod & 0x04) = 0) OR (program.description <> ''           AND program.description = recorded.description))       )      )   )  LEFT JOIN oldfind ON   (oldfind.recordid = recordmatch.recordid AND    oldfind.findid = (CASE record.type   WHEN 6    THEN record.findid   WHEN 9    THEN to_days(date_sub(program.starttime, interval                 time_format(record.findtime, '%H:%i') hour_minute))   WHEN 10    THEN floor((to_days(date_sub(program.starttime, interval                time_format(record.findtime, '%H:%i') hour_minute)) -                record.findday)/7) * 7 + record.findday   WHEN 7    THEN record.findid   ELSE 0  END) )  ORDER BY record.recordid DESC
Driver error was [2/145]:
QMYSQL3: Unable to execute query
Database error was:
Table './mythconverg/oldrecorded' is marked as crashed and should be repaired

2007-10-23 20:37:00.457 Scheduled 0 items in 3.9 = 3.90 match + 0.02 place
2007-10-23 20:37:00.463 scheduler: Scheduled items: Scheduled 0 items in 3.9 = 3.90 match + 0.02 place
2007-10-23 20:37:00.469 Seem to be woken up by USER
2007-10-23 20:37:03.140 mythbackend: Running housekeeping thread
2007-10-23 20:37:03.979 JobQueue: Commercial Flagging Starting for Cavemen "The Mascot" recorded from channel 1007 at Tue Oct 23 20:00:00 2007
2007-10-23 20:37:04.010 commflag: Commercial Flagging Starting: Cavemen "The Mascot" recorded from channel 1007 at Tue Oct 23 20:00:00 2007
2007-10-23 20:37:04.254 Using runtime prefix = /usr
2007-10-23 20:37:04.438 New DB connection, total: 1
2007-10-23 20:37:04.475 Connected to database 'mythconverg' at host: localhost
2007-10-23 20:37:04.488 New DB connection, total: 2
2007-10-23 20:37:04.557 Connected to database 'mythconverg' at host: localhost
2007-10-23 20:37:06.762 Connecting to backend server: 127.0.0.1:6543 (try 1 of 5)
2007-10-23 20:37:06.936 Using protocol version 31
2007-10-23 20:37:07.210 MainServer::HandleAnnounce Monitor
2007-10-23 20:37:07.419 adding: mythserver as a client (events: 0)
2007-10-23 20:37:07.519 MainServer::HandleAnnounce Monitor
2007-10-23 20:37:07.599 adding: mythserver as a client (events: 1)
0: start_time: 0.036 duration: 161.700
1: start_time: 0.026 duration: 161.676
stream: start_time: 0.289 duration: 1796.773 bitrate=7185 kb/s
2007-10-23 20:37:09.299 AFD: Opened codec 0x73c8d0, id(MPEG2VIDEO) type(Video)
2007-10-23 20:37:09.975 AFD: Opened codec 0x73cd70, id(MP2) type(Audio)
[mpeg2video @ 0x2ab0db7ccfd0]warning: first frame is no keyframe
[mpeg2video @ 0x2ab0db7ccfd0]warning: first frame is no keyframe
[mpeg2video @ 0x2ab0db7ccfd0]warning: first frame is no keyframe
[mpeg2video @ 0x2ab0db7ccfd0]warning: first frame is no keyframe
[mpeg2video @ 0x2ab0db7ccfd0]warning: first frame is no keyframe
[mpeg2video @ 0x2ab0db7ccfd0]warning: first frame is no keyframe
[mpeg2video @ 0x2ab0db7ccfd0]warning: first frame is no keyframe
[mpeg2video @ 0x2ab0db7ccfd0]warning: first frame is no keyframe
[mpeg2video @ 0x2ab0db7ccfd0]warning: first frame is no keyframe
[mpeg2video @ 0x2ab0db7ccfd0]warning: first frame is no keyframe
[mpeg2video @ 0x2ab0db7ccfd0]warning: first frame is no keyframe
[mpeg2video @ 0x2ab0db7ccfd0]warning: first frame is no keyframe
[mpeg2video @ 0x2ab0db7ccfd0]warning: first frame is no keyframe
[mpeg2video @ 0x2ab0db7ccfd0]warning: first frame is no keyframe
[mpeg2video @ 0x2ab0db7ccfd0]warning: first frame is no keyframe
[mpeg2video @ 0x2ab0db7ccfd0]warning: first frame is no keyframe
[mpeg2video @ 0x2ab0db7ccfd0]warning: first frame is no keyframe
[mpeg2video @ 0x2ab0db7ccfd0]warning: first frame is no keyframe
[mpeg2video @ 0x2ab0db7ccfd0]warning: first frame is no keyframe
[mpeg2video @ 0x2ab0db7ccfd0]warning: first frame is no keyframe
[mpeg2video @ 0x2ab0db7ccfd0]warning: first frame is no keyframe
[mpeg2video @ 0x2ab0db7ccfd0]warning: first frame is no keyframe
[mpeg2video @ 0x2ab0db7ccfd0]warning: first frame is no keyframe
[mpeg2video @ 0x2ab0db7ccfd0]warning: first frame is no keyframe
[mpeg2video @ 0x2ab0db7ccfd0]warning: first frame is no keyframe
[mpeg2video @ 0x2ab0db7ccfd0]warning: first frame is no keyframe
[mpeg2video @ 0x2ab0db7ccfd0]warning: first frame is no keyframe
[mpeg2video @ 0x2ab0db7ccfd0]warning: first frame is no keyframe
[mpeg2video @ 0x2ab0db7ccfd0]warning: first frame is no keyframe
[mpeg2video @ 0x2ab0db7ccfd0]warning: first frame is no keyframe
[mpeg2video @ 0x2ab0db7ccfd0]warning: first frame is no keyframe
[mpeg2video @ 0x2ab0db7ccfd0]warning: first frame is no keyframe
[mpeg2video @ 0x2ab0db7ccfd0]warning: first frame is no keyframe
[mpeg2video @ 0x2ab0db7ccfd0]warning: first frame is no keyframe
[mpeg2video @ 0x2ab0db7ccfd0]warning: first frame is no keyframe
[mpeg2video @ 0x2ab0db7ccfd0]warning: first frame is no keyframe
[mpeg2video @ 0x2ab0db7ccfd0]warning: first frame is no keyframe
[mpeg2video @ 0x2ab0db7ccfd0]warning: first frame is no keyframe
[mpeg2video @ 0x2ab0db7ccfd0]warning: first frame is no keyframe
[mpeg2video @ 0x2ab0db7ccfd0]warning: first frame is no keyframe
[mpeg2video @ 0x2ab0db7ccfd0]warning: first frame is no keyframe
[mpeg2video @ 0x2ab0db7ccfd0]warning: first frame is no keyframe
[mpeg2video @ 0x2ab0db7ccfd0]warning: first frame is no keyframe
[mpeg2video @ 0x2ab0db7ccfd0]warning: first frame is no keyframe
[mpeg2video @ 0x2ab0db7ccfd0]warning: first frame is no keyframe
[mpeg2video @ 0x2ab0db7ccfd0]warning: first frame is no keyframe
[mpeg2video @ 0x2ab0db7ccfd0]warning: first frame is no keyframe
[mpeg2video @ 0x2ab0db7ccfd0]warning: first frame is no keyframe
[mpeg2video @ 0x2ab0db7ccfd0]warning: first frame is no keyframe
[mpeg2video @ 0x2ab0db7ccfd0]warning: first frame is no keyframe
[mpeg2video @ 0x2ab0db7ccfd0]warning: first frame is no keyframe
[mpeg2video @ 0x2ab0db7ccfd0]warning: first frame is no keyframe
[mpeg2video @ 0x2ab0db7ccfd0]warning: first frame is no keyframe
[mpeg2video @ 0x2ab0db7ccfd0]warning: first frame is no keyframe
[mpeg2video @ 0x2ab0db7ccfd0]warning: first frame is no keyframe
[mpeg2video @ 0x2ab0db7ccfd0]warning: first frame is no keyframe
[mpeg2video @ 0x2ab0db7ccfd0]warning: first frame is no keyframe
[mpeg2video @ 0x2ab0db7ccfd0]warning: first frame is no keyframe
[mpeg2video @ 0x2ab0db7ccfd0]warning: first frame is no keyframe
[mpeg2video @ 0x2ab0db7ccfd0]warning: first frame is no keyframe
[mpeg2video @ 0x2ab0db7ccfd0]warning: first frame is no keyframe
[mpeg2video @ 0x2ab0db7ccfd0]warning: first frame is no keyframe
[mpeg2video @ 0x2ab0db7ccfd0]warning: first frame is no keyframe
[mpeg2video @ 0x2ab0db7ccfd0]warning: first frame is no keyframe
[mpeg2video @ 0x2ab0db7ccfd0]warning: first frame is no keyframe
[mpeg2video @ 0x2ab0db7ccfd0]warning: first frame is no keyframe
[mpeg2video @ 0x2ab0db7ccfd0]warning: first frame is no keyframe
[mpeg2video @ 0x2ab0db7ccfd0]warning: first frame is no keyframe
[mpeg2video @ 0x2ab0db7ccfd0]warning: first frame is no keyframe
[mpeg2video @ 0x2ab0db7ccfd0]warning: first frame is no keyframe
[mpeg2video @ 0x2ab0db7ccfd0]warning: first frame is no keyframe
[mpeg2video @ 0x2ab0db7ccfd0]warning: first frame is no keyframe
[mpeg2video @ 0x2ab0db7ccfd0]warning: first frame is no keyframe
[mpeg2video @ 0x2ab0db7ccfd0]warning: first frame is no keyframe
[mpeg2video @ 0x2ab0db7ccfd0]warning: first frame is no keyframe
[mpeg2video @ 0x2ab0db7ccfd0]warning: first frame is no keyframe
[mpeg2video @ 0x2ab0db7ccfd0]warning: first frame is no keyframe
[mpeg2video @ 0x2ab0db7ccfd0]warning: first frame is no keyframe
[mpeg2video @ 0x2ab0db7ccfd0]warning: first frame is no keyframe
[mpeg2video @ 0x2ab0db7ccfd0]warning: first frame is no keyframe
[mpeg2video @ 0x2ab0db7ccfd0]warning: first frame is no keyframe
[mpeg2video @ 0x2ab0db7ccfd0]warning: first frame is no keyframe
[mpeg2video @ 0x2ab0db7ccfd0]warning: first frame is no keyframe
[mpeg2video @ 0x2ab0db7ccfd0]warning: first frame is no keyframe
[mpeg2video @ 0x2ab0db7ccfd0]warning: first frame is no keyframe
[mpeg2video @ 0x2ab0db7ccfd0]warning: first frame is no keyframe
[mpeg2video @ 0x2ab0db7ccfd0]warning: first frame is no keyframe
[mpeg2video @ 0x2ab0db7ccfd0]warning: first frame is no keyframe
[mpeg2video @ 0x2ab0db7ccfd0]warning: first frame is no keyframe
[mpeg2video @ 0x2ab0db7ccfd0]warning: first frame is no keyframe
[mpeg2video @ 0x2ab0db7ccfd0]warning: first frame is no keyframe
[mpeg2video @ 0x2ab0db7ccfd0]warning: first frame is no keyframe
[mpeg2video @ 0x2ab0db7ccfd0]warning: first frame is no keyframe
[mpeg2video @ 0x2ab0db7ccfd0]warning: first frame is no keyframe
[mpeg2video @ 0x2ab0db7ccfd0]warning: first frame is no keyframe
[mpeg2video @ 0x2ab0db7ccfd0]warning: first frame is no keyframe
[mpeg2video @ 0x2ab0db7ccfd0]warning: first frame is no keyframe
[mpeg2video @ 0x2ab0db7ccfd0]warning: first frame is no keyframe
[mpeg2video @ 0x2ab0db7ccfd0]warning: first frame is no keyframe
[mpeg2video @ 0x2ab0db7ccfd0]warning: first frame is no keyframe
[mpeg2video @ 0x2ab0db7ccfd0]warning: first frame is no keyframe
[mpeg2video @ 0x2ab0db7ccfd0]warning: first frame is no keyframe
[mpeg2video @ 0x2ab0db7ccfd0]warning: first frame is no keyframe
[mpeg2video @ 0x2ab0db7ccfd0]warning: first frame is no keyframe
[mpeg2video @ 0x2ab0db7ccfd0]warning: first frame is no keyframe
[mpeg2video @ 0x2ab0db7ccfd0]warning: first frame is no keyframe
[mpeg2video @ 0x2ab0db7ccfd0]warning: first frame is no keyframe
[mpeg2video @ 0x2ab0db7ccfd0]warning: first frame is no keyframe
[mpeg2video @ 0x2ab0db7ccfd0]warning: first frame is no keyframe
[mpeg2video @ 0x2ab0db7ccfd0]warning: first frame is no keyframe
[mpeg2video @ 0x2ab0db7ccfd0]warning: first frame is no keyframe
[mpeg2video @ 0x2ab0db7ccfd0]warning: first frame is no keyframe
[mpeg2video @ 0x2ab0db7ccfd0]warning: first frame is no keyframe
[mpeg2video @ 0x2ab0db7ccfd0]warning: first frame is no keyframe
[mpeg2video @ 0x2ab0db7ccfd0]warning: first frame is no keyframe
[mpeg2video @ 0x2ab0db7ccfd0]warning: first frame is no keyframe
[mpeg2video @ 0x2ab0db7ccfd0]warning: first frame is no keyframe
[mpeg2video @ 0x2ab0db7ccfd0]warning: first frame is no keyframe
[mpeg2video @ 0x2ab0db7ccfd0]warning: first frame is no keyframe
[mpeg2video @ 0x2ab0db7ccfd0]warning: first frame is no keyframe
[mpeg2video @ 0x2ab0db7ccfd0]warning: first frame is no keyframe
[mpeg2video @ 0x2ab0db7ccfd0]warning: first frame is no keyframe
[mpeg2video @ 0x2ab0db7ccfd0]warning: first frame is no keyframe
[mpeg2video @ 0x2ab0db7ccfd0]warning: first frame is no keyframe
[mpeg2video @ 0x2ab0db7ccfd0]warning: first frame is no keyframe
[mpeg2video @ 0x2ab0db7ccfd0]warning: first frame is no keyframe
[mpeg2video @ 0x2ab0db7ccfd0]warning: first frame is no keyframe
[mpeg2video @ 0x2ab0db7ccfd0]warning: first frame is no keyframe
[mpeg2video @ 0x2ab0db7ccfd0]warning: first frame is no keyframe
[mpeg2video @ 0x2ab0db7ccfd0]warning: first frame is no keyframe
[mpeg2video @ 0x2ab0db7ccfd0]warning: first frame is no keyframe
[mpeg2video @ 0x2ab0db7ccfd0]warning: first frame is no keyframe
[mpeg2video @ 0x2ab0db7ccfd0]warning: first frame is no keyframe
[mpeg2video @ 0x2ab0db7ccfd0]warning: first frame is no keyframe
[mpeg2video @ 0x2ab0db7ccfd0]warning: first frame is no keyframe
[mpeg2video @ 0x2ab0db7ccfd0]warning: first frame is no keyframe
[mpeg2video @ 0x2ab0db7ccfd0]warning: first frame is no keyframe
[mpeg2video @ 0x2ab0db7ccfd0]warning: first frame is no keyframe
[mpeg2video @ 0x2ab0db7ccfd0]warning: first frame is no keyframe
[mpeg2video @ 0x2ab0db7ccfd0]warning: first frame is no keyframe
[mpeg2video @ 0x2ab0db7ccfd0]warning: first frame is no keyframe
[mpeg2video @ 0x2ab0db7ccfd0]warning: first frame is no keyframe
[mpeg2video @ 0x2ab0db7ccfd0]warning: first frame is no keyframe
[mpeg2video @ 0x2ab0db7ccfd0]warning: first frame is no keyframe
[mpeg2video @ 0x2ab0db7ccfd0]warning: first frame is no keyframe
[mpeg2video @ 0x2ab0db7ccfd0]warning: first frame is no keyframe
[mpeg2video @ 0x2ab0db7ccfd0]warning: first frame is no keyframe
[mpeg2video @ 0x2ab0db7ccfd0]warning: first frame is no keyframe
[mpeg2video @ 0x2ab0db7ccfd0]warning: first frame is no keyframe
[mpeg2video @ 0x2ab0db7ccfd0]warning: first frame is no keyframe
[mpeg2video @ 0x2ab0db7ccfd0]warning: first frame is no keyframe
[mpeg2video @ 0x2ab0db7ccfd0]warning: first frame is no keyframe
[mpeg2video @ 0x2ab0db7ccfd0]warning: first frame is no keyframe
[mpeg2video @ 0x2ab0db7ccfd0]warning: first frame is no keyframe
[mpeg2video @ 0x2ab0db7ccfd0]warning: first frame is no keyframe
[mpeg2video @ 0x2ab0db7ccfd0]warning: first frame is no keyframe
[mpeg2video @ 0x2ab0db7ccfd0]warning: first frame is no keyframe
[mpeg2video @ 0x2ab0db7ccfd0]warning: first frame is no keyframe
[mpeg2video @ 0x2ab0db7ccfd0]warning: first frame is no keyframe
[mpeg2video @ 0x2ab0db7ccfd0]warning: first frame is no keyframe
[mpeg2video @ 0x2ab0db7ccfd0]warning: first frame is no keyframe
[mpeg2video @ 0x2ab0db7ccfd0]warning: first frame is no keyframe
[mpeg2video @ 0x2ab0db7ccfd0]warning: first frame is no keyframe
[mpeg2video @ 0x2ab0db7ccfd0]warning: first frame is no keyframe
[mpeg2video @ 0x2ab0db7ccfd0]warning: first frame is no keyframe
[mpeg2video @ 0x2ab0db7ccfd0]warning: first frame is no keyframe
[mpeg2video @ 0x2ab0db7ccfd0]warning: first frame is no keyframe
[mpeg2video @ 0x2ab0db7ccfd0]warning: first frame is no keyframe
[mpeg2video @ 0x2ab0db7ccfd0]warning: first frame is no keyframe
[mpeg2video @ 0x2ab0db7ccfd0]warning: first frame is no keyframe
[mpeg2video @ 0x2ab0db7ccfd0]warning: first frame is no keyframe
[mpeg2video @ 0x2ab0db7ccfd0]warning: first frame is no keyframe
[mpeg2video @ 0x2ab0db7ccfd0]warning: first frame is no keyframe
[mpeg2video @ 0x2ab0db7ccfd0]warning: first frame is no keyframe
[mpeg2video @ 0x2ab0db7ccfd0]warning: first frame is no keyframe
[mpeg2video @ 0x2ab0db7ccfd0]warning: first frame is no keyframe
[mpeg2video @ 0x2ab0db7ccfd0]warning: first frame is no keyframe
[mpeg2video @ 0x2ab0db7ccfd0]warning: first frame is no keyframe
[mpeg2video @ 0x2ab0db7ccfd0]warning: first frame is no keyframe
[mpeg2video @ 0x2ab0db7ccfd0]warning: first frame is no keyframe
[mpeg2video @ 0x2ab0db7ccfd0]warning: first frame is no keyframe
[mpeg2video @ 0x2ab0db7ccfd0]warning: first frame is no keyframe
[mpeg2video @ 0x2ab0db7ccfd0]warning: first frame is no keyframe
[mpeg2video @ 0x2ab0db7ccfd0]warning: first frame is no keyframe
[mpeg2video @ 0x2ab0db7ccfd0]warning: first frame is no keyframe
[mpeg2video @ 0x2ab0db7ccfd0]warning: first frame is no keyframe
[mpeg2video @ 0x2ab0db7ccfd0]warning: first frame is no keyframe
[mpeg2video @ 0x2ab0db7ccfd0]warning: first frame is no keyframe
[mpeg2video @ 0x2ab0db7ccfd0]warning: first frame is no keyframe
[mpeg2video @ 0x2ab0db7ccfd0]warning: first frame is no keyframe
[mpeg2video @ 0x2ab0db7ccfd0]warning: first frame is no keyframe
[mpeg2video @ 0x2ab0db7ccfd0]warning: first frame is no keyframe
[mpeg2video @ 0x2ab0db7ccfd0]warning: first frame is no keyframe
[mpeg2video @ 0x2ab0db7ccfd0]warning: first frame is no keyframe
[mpeg2video @ 0x2ab0db7ccfd0]warning: first frame is no keyframe
[mpeg2video @ 0x2ab0db7ccfd0]warning: first frame is no keyframe
[mpeg2video @ 0x2ab0db7ccfd0]warning: first frame is no keyframe
[mpeg2video @ 0x2ab0db7ccfd0]warning: first frame is no keyframe
[mpeg2video @ 0x2ab0db7ccfd0]warning: first frame is no keyframe
[mpeg2video @ 0x2ab0db7ccfd0]warning: first frame is no keyframe
[mpeg2video @ 0x2ab0db7ccfd0]warning: first frame is no keyframe
[mpeg2video @ 0x2ab0db7ccfd0]warning: first frame is no keyframe
[mpeg2video @ 0x2ab0db7ccfd0]warning: first frame is no keyframe
[mpeg2video @ 0x2ab0db7ccfd0]warning: first frame is no keyframe
[mpeg2video @ 0x2ab0db7ccfd0]warning: first frame is no keyframe
[mpeg2video @ 0x2ab0db7ccfd0]warning: first frame is no keyframe
[mpeg2video @ 0x2ab0db7ccfd0]warning: first frame is no keyframe
[mpeg2video @ 0x2ab0db7ccfd0]warning: first frame is no keyframe
[mpeg2video @ 0x2ab0db7ccfd0]warning: first frame is no keyframe
[mpeg2video @ 0x2ab0db7ccfd0]warning: first frame is no keyframe
[mpeg2video @ 0x2ab0db7ccfd0]warning: first frame is no keyframe
[mpeg2video @ 0x2ab0db7ccfd0]warning: first frame is no keyframe
[mpeg2video @ 0x2ab0db7ccfd0]warning: first frame is no keyframe
[mpeg2video @ 0x2ab0db7ccfd0]warning: first frame is no keyframe
[mpeg2video @ 0x2ab0db7ccfd0]warning: first frame is no keyframe
[mpeg2video @ 0x2ab0db7ccfd0]warning: first frame is no keyframe
[mpeg2video @ 0x2ab0db7ccfd0]warning: first frame is no keyframe
[mpeg2video @ 0x2ab0db7ccfd0]warning: first frame is no keyframe
[mpeg2video @ 0x2ab0db7ccfd0]warning: first frame is no keyframe
[mpeg2video @ 0x2ab0db7ccfd0]warning: first frame is no keyframe
[mpeg2video @ 0x2ab0db7ccfd0]warning: first frame is no keyframe
[mpeg2video @ 0x2ab0db7ccfd0]warning: first frame is no keyframe
[mpeg2video @ 0x2ab0db7ccfd0]warning: first frame is no keyframe
[mpeg2video @ 0x2ab0db7ccfd0]warning: first frame is no keyframe
[mpeg2video @ 0x2ab0db7ccfd0]warning: first frame is no keyframe
[mpeg2video @ 0x2ab0db7ccfd0]warning: first frame is no keyframe
[mpeg2video @ 0x2ab0db7ccfd0]warning: first frame is no keyframe
[mpeg2video @ 0x2ab0db7ccfd0]warning: first frame is no keyframe
[mpeg2video @ 0x2ab0db7ccfd0]warning: first frame is no keyframe
[mpeg2video @ 0x2ab0db7ccfd0]warning: first frame is no keyframe
[mpeg2video @ 0x2ab0db7ccfd0]warning: first frame is no keyframe
[mpeg2video @ 0x2ab0db7ccfd0]warning: first frame is no keyframe
[mpeg2video @ 0x2ab0db7ccfd0]warning: first frame is no keyframe
[mpeg2video @ 0x2ab0db7ccfd0]warning: first frame is no keyframe
[mpeg2video @ 0x2ab0db7ccfd0]warning: first frame is no keyframe
[mpeg2video @ 0x2ab0db7ccfd0]warning: first frame is no keyframe
[mpeg2video @ 0x2ab0db7ccfd0]warning: first frame is no keyframe
[mpeg2video @ 0x2ab0db7ccfd0]warning: first frame is no keyframe
[mpeg2video @ 0x2ab0db7ccfd0]warning: first frame is no keyframe
[mpeg2video @ 0x2ab0db7ccfd0]warning: first frame is no keyframe
[mpeg2video @ 0x2ab0db7ccfd0]warning: first frame is no keyframe
[mpeg2video @ 0x2ab0db7ccfd0]warning: first frame is no keyframe
[mpeg2video @ 0x2ab0db7ccfd0]warning: first frame is no keyframe
[mpeg2video @ 0x2ab0db7ccfd0]warning: first frame is no keyframe
[mpeg2video @ 0x2ab0db7ccfd0]warning: first frame is no keyframe
[mpeg2video @ 0x2ab0db7ccfd0]warning: first frame is no keyframe
[mpeg2video @ 0x2ab0db7ccfd0]warning: first frame is no keyframe
[mpeg2video @ 0x2ab0db7ccfd0]warning: first frame is no keyframe
[mpeg2video @ 0x2ab0db7ccfd0]warning: first frame is no keyframe
[mpeg2video @ 0x2ab0db7ccfd0]warning: first frame is no keyframe
[mpeg2video @ 0x2ab0db7ccfd0]warning: first frame is no keyframe
[mpeg2video @ 0x2ab0db7ccfd0]warning: first frame is no keyframe
[mpeg2video @ 0x2ab0db7ccfd0]warning: first frame is no keyframe
[mpeg2video @ 0x2ab0db7ccfd0]warning: first frame is no keyframe
[mpeg2video @ 0x2ab0db7ccfd0]warning: first frame is no keyframe
[mpeg2video @ 0x2ab0db7ccfd0]warning: first frame is no keyframe
[mpeg2video @ 0x2ab0db7ccfd0]warning: first frame is no keyframe
[mpeg2video @ 0x2ab0db7ccfd0]warning: first frame is no keyframe
[mpeg2video @ 0x2ab0db7ccfd0]warning: first frame is no keyframe
[mpeg2video @ 0x2ab0db7ccfd0]warning: first frame is no keyframe
[mpeg2video @ 0x2ab0db7ccfd0]warning: first frame is no keyframe
[mpeg2video @ 0x2ab0db7ccfd0]warning: first frame is no keyframe
[mpeg2video @ 0x2ab0db7ccfd0]warning: first frame is no keyframe
[mpeg2video @ 0x2ab0db7ccfd0]warning: first frame is no keyframe
[mpeg2video @ 0x2ab0db7ccfd0]warning: first frame is no keyframe
[mpeg2video @ 0x2ab0db7ccfd0]warning: first frame is no keyframe
[mpeg2video @ 0x2ab0db7ccfd0]warning: first frame is no keyframe
[mpeg2video @ 0x2ab0db7ccfd0]warning: first frame is no keyframe
[mpeg2video @ 0x2ab0db7ccfd0]warning: first frame is no keyframe
[mpeg2video @ 0x2ab0db7ccfd0]warning: first frame is no keyframe
[mpeg2video @ 0x2ab0db7ccfd0]warning: first frame is no keyframe
[mpeg2video @ 0x2ab0db7ccfd0]warning: first frame is no keyframe
[mpeg2video @ 0x2ab0db7ccfd0]warning: first frame is no keyframe
[mpeg2video @ 0x2ab0db7ccfd0]warning: first frame is no keyframe
[mpeg2video @ 0x2ab0db7ccfd0]warning: first frame is no keyframe
[mpeg2video @ 0x2ab0db7ccfd0]warning: first frame is no keyframe
[mpeg2video @ 0x2ab0db7ccfd0]warning: first frame is no keyframe
[mpeg2video @ 0x2ab0db7ccfd0]warning: first frame is no keyframe
[mpeg2video @ 0x2ab0db7ccfd0]warning: first frame is no keyframe
[mpeg2video @ 0x2ab0db7ccfd0]warning: first frame is no keyframe
[mpeg2video @ 0x2ab0db7ccfd0]warning: first frame is no keyframe
[mpeg2video @ 0x2ab0db7ccfd0]warning: first frame is no keyframe
[mpeg2video @ 0x2ab0db7ccfd0]warning: first frame is no keyframe
[mpeg2video @ 0x2ab0db7ccfd0]warning: first frame is no keyframe
[mpeg2video @ 0x2ab0db7ccfd0]warning: first frame is no keyframe
[mpeg2video @ 0x2ab0db7ccfd0]warning: first frame is no keyframe
[mpeg2video @ 0x2ab0db7ccfd0]warning: first frame is no keyframe
[mpeg2video @ 0x2ab0db7ccfd0]warning: first frame is no keyframe
[mpeg2video @ 0x2ab0db7ccfd0]warning: first frame is no keyframe
[mpeg2video @ 0x2ab0db7ccfd0]warning: first frame is no keyframe
[mpeg2video @ 0x2ab0db7ccfd0]warning: first frame is no keyframe
[mpeg2video @ 0x2ab0db7ccfd0]warning: first frame is no keyframe
[mpeg2video @ 0x2ab0db7ccfd0]warning: first frame is no keyframe
[mpeg2video @ 0x2ab0db7ccfd0]warning: first frame is no keyframe
[mpeg2video @ 0x2ab0db7ccfd0]warning: first frame is no keyframe
[mpeg2video @ 0x2ab0db7ccfd0]warning: first frame is no keyframe
[mpeg2video @ 0x2ab0db7ccfd0]warning: first frame is no keyframe
[mpeg2video @ 0x2ab0db7ccfd0]warning: first frame is no keyframe
[mpeg2video @ 0x2ab0db7ccfd0]warning: first frame is no keyframe
[mpeg2video @ 0x2ab0db7ccfd0]warning: first frame is no keyframe
[mpeg2video @ 0x2ab0db7ccfd0]warning: first frame is no keyframe
[mpeg2video @ 0x2ab0db7ccfd0]warning: first frame is no keyframe
[mpeg2video @ 0x2ab0db7ccfd0]warning: first frame is no keyframe
[mpeg2video @ 0x2ab0db7ccfd0]warning: first frame is no keyframe
[mpeg2video @ 0x2ab0db7ccfd0]warning: first frame is no keyframe
[mpeg2video @ 0x2ab0db7ccfd0]warning: first frame is no keyframe
[mpeg2video @ 0x2ab0db7ccfd0]warning: first frame is no keyframe
[mpeg2video @ 0x2ab0db7ccfd0]warning: first frame is no keyframe
[mpeg2video @ 0x2ab0db7ccfd0]warning: first frame is no keyframe
[mpeg2video @ 0x2ab0db7ccfd0]warning: first frame is no keyframe
[mpeg2video @ 0x2ab0db7ccfd0]warning: first frame is no keyframe
[mpeg2video @ 0x2ab0db7ccfd0]warning: first frame is no keyframe
[mpeg2video @ 0x2ab0db7ccfd0]warning: first frame is no keyframe
[mpeg2video @ 0x2ab0db7ccfd0]warning: first frame is no keyframe
[mpeg2video @ 0x2ab0db7ccfd0]warning: first frame is no keyframe
[mpeg2video @ 0x2ab0db7ccfd0]warning: first frame is no keyframe
[mpeg2video @ 0x2ab0db7ccfd0]warning: first frame is no keyframe
[mpeg2video @ 0x2ab0db7ccfd0]warning: first frame is no keyframe
[mpeg2video @ 0x2ab0db7ccfd0]warning: first frame is no keyframe
[mpeg2video @ 0x2ab0db7ccfd0]warning: first frame is no keyframe
[mpeg2video @ 0x2ab0db7ccfd0]warning: first frame is no keyframe
[mpeg2video @ 0x2ab0db7ccfd0]warning: first frame is no keyframe
[mpeg2video @ 0x2ab0db7ccfd0]warning: first frame is no keyframe
[mpeg2video @ 0x2ab0db7ccfd0]warning: first frame is no keyframe
[mpeg2video @ 0x2ab0db7ccfd0]warning: first frame is no keyframe
[mpeg2video @ 0x2ab0db7ccfd0]warning: first frame is no keyframe
[mpeg2video @ 0x2ab0db7ccfd0]warning: first frame is no keyframe
[mpeg2video @ 0x2ab0db7ccfd0]warning: first frame is no keyframe
[mpeg2video @ 0x2ab0db7ccfd0]warning: first frame is no keyframe
[mpeg2video @ 0x2ab0db7ccfd0]warning: first frame is no keyframe
[mpeg2video @ 0x2ab0db7ccfd0]warning: first frame is no keyframe
[mpeg2video @ 0x2ab0db7ccfd0]warning: first frame is no keyframe
[mpeg2video @ 0x2ab0db7ccfd0]warning: first frame is no keyframe
[mpeg2video @ 0x2ab0db7ccfd0]warning: first frame is no keyframe
[mpeg2video @ 0x2ab0db7ccfd0]warning: first frame is no keyframe
[mpeg2video @ 0x2ab0db7ccfd0]warning: first frame is no keyframe
[mpeg2video @ 0x2ab0db7ccfd0]warning: first frame is no keyframe
[mpeg2video @ 0x2ab0db7ccfd0]warning: first frame is no keyframe
[mpeg2video @ 0x2ab0db7ccfd0]warning: first frame is no keyframe
[mpeg2video @ 0x2ab0db7ccfd0]warning: first frame is no keyframe
[mpeg2video @ 0x2ab0db7ccfd0]warning: first frame is no keyframe
[mpeg2video @ 0x2ab0db7ccfd0]warning: first frame is no keyframe
[mpeg2video @ 0x2ab0db7ccfd0]warning: first frame is no keyframe
[mpeg2video @ 0x2ab0db7ccfd0]warning: first frame is no keyframe
[mpeg2video @ 0x2ab0db7ccfd0]warning: first frame is no keyframe
[mpeg2video @ 0x2ab0db7ccfd0]warning: first frame is no keyframe
[mpeg2video @ 0x2ab0db7ccfd0]warning: first frame is no keyframe
[mpeg2video @ 0x2ab0db7ccfd0]warning: first frame is no keyframe
[mpeg2video @ 0x2ab0db7ccfd0]warning: first frame is no keyframe
[mpeg2video @ 0x2ab0db7ccfd0]warning: first frame is no keyframe
[mpeg2video @ 0x2ab0db7ccfd0]warning: first frame is no keyframe
[mpeg2video @ 0x2ab0db7ccfd0]warning: first frame is no keyframe
[mpeg2video @ 0x2ab0db7ccfd0]warning: first frame is no keyframe
[mpeg2video @ 0x2ab0db7ccfd0]warning: first frame is no keyframe
[mpeg2video @ 0x2ab0db7ccfd0]warning: first frame is no keyframe
[mpeg2video @ 0x2ab0db7ccfd0]warning: first frame is no keyframe
[mpeg2video @ 0x2ab0db7ccfd0]warning: first frame is no keyframe
[mpeg2video @ 0x2ab0db7ccfd0]warning: first frame is no keyframe
[mpeg2video @ 0x2ab0db7ccfd0]warning: first frame is no keyframe
[mpeg2video @ 0x2ab0db7ccfd0]warning: first frame is no keyframe
[mpeg2video @ 0x2ab0db7ccfd0]warning: first frame is no keyframe
[mpeg2video @ 0x2ab0db7ccfd0]warning: first frame is no keyframe
[mpeg2video @ 0x2ab0db7ccfd0]warning: first frame is no keyframe
[mpeg2video @ 0x2ab0db7ccfd0]warning: first frame is no keyframe
[mpeg2video @ 0x2ab0db7ccfd0]warning: first frame is no keyframe
[mpeg2video @ 0x2ab0db7ccfd0]warning: first frame is no keyframe
[mpeg2video @ 0x2ab0db7ccfd0]warning: first frame is no keyframe
[mpeg2video @ 0x2ab0db7ccfd0]warning: first frame is no keyframe
[mpeg2video @ 0x2ab0db7ccfd0]warning: first frame is no keyframe
[mpeg2video @ 0x2ab0db7ccfd0]warning: first frame is no keyframe
[mpeg2video @ 0x2ab0db7ccfd0]warning: first frame is no keyframe
[mpeg2video @ 0x2ab0db7ccfd0]warning: first frame is no keyframe
[mpeg2video @ 0x2ab0db7ccfd0]warning: first frame is no keyframe
[mpeg2video @ 0x2ab0db7ccfd0]warning: first frame is no keyframe
[mpeg2video @ 0x2ab0db7ccfd0]warning: first frame is no keyframe
[mpeg2video @ 0x2ab0db7ccfd0]warning: first frame is no keyframe
[mpeg2video @ 0x2ab0db7ccfd0]warning: first frame is no keyframe
[mpeg2video @ 0x2ab0db7ccfd0]warning: first frame is no keyframe
[mpeg2video @ 0x2ab0db7ccfd0]warning: first frame is no keyframe
[mpeg2video @ 0x2ab0db7ccfd0]warning: first frame is no keyframe
[mpeg2video @ 0x2ab0db7ccfd0]warning: first frame is no keyframe
[mpeg2video @ 0x2ab0db7ccfd0]warning: first frame is no keyframe
[mpeg2video @ 0x2ab0db7ccfd0]warning: first frame is no keyframe
[mpeg2video @ 0x2ab0db7ccfd0]warning: first frame is no keyframe
[mpeg2video @ 0x2ab0db7ccfd0]invalid mb type in I Frame at 0 0
[mpeg2video @ 0x2ab0db7ccfd0]invalid mb type in I Frame at 0 1
[mpeg2video @ 0x2ab0db7ccfd0]invalid mb type in I Frame at 0 2
[mpeg2video @ 0x2ab0db7ccfd0]invalid mb type in I Frame at 0 3
[mpeg2video @ 0x2ab0db7ccfd0]invalid mb type in I Frame at 0 4
[mpeg2video @ 0x2ab0db7ccfd0]invalid mb type in I Frame at 0 5
[mpeg2video @ 0x2ab0db7ccfd0]invalid mb type in I Frame at 0 6
[mpeg2video @ 0x2ab0db7ccfd0]invalid mb type in I Frame at 0 7
[mpeg2video @ 0x2ab0db7ccfd0]invalid mb type in I Frame at 0 8
[mpeg2video @ 0x2ab0db7ccfd0]invalid mb type in I Frame at 0 9
[mpeg2video @ 0x2ab0db7ccfd0]invalid mb type in I Frame at 0 10
[mpeg2video @ 0x2ab0db7ccfd0]invalid mb type in I Frame at 0 11
[mpeg2video @ 0x2ab0db7ccfd0]invalid mb type in I Frame at 0 12
[mpeg2video @ 0x2ab0db7ccfd0]invalid mb type in I Frame at 0 13
[mpeg2video @ 0x2ab0db7ccfd0]invalid mb type in I Frame at 0 14
[mpeg2video @ 0x2ab0db7ccfd0]invalid mb type in I Frame at 0 15
[mpeg2video @ 0x2ab0db7ccfd0]invalid mb type in I Frame at 0 16
[mpeg2video @ 0x2ab0db7ccfd0]invalid mb type in I Frame at 0 17
[mpeg2video @ 0x2ab0db7ccfd0]invalid mb type in I Frame at 0 19
[mpeg2video @ 0x2ab0db7ccfd0]invalid mb type in I Frame at 0 20
[mpeg2video @ 0x2ab0db7ccfd0]invalid mb type in I Frame at 0 21
[mpeg2video @ 0x2ab0db7ccfd0]invalid mb type in I Frame at 0 22
[mpeg2video @ 0x2ab0db7ccfd0]invalid mb type in I Frame at 0 23
[mpeg2video @ 0x2ab0db7ccfd0]invalid mb type in I Frame at 0 24
[mpeg2video @ 0x2ab0db7ccfd0]invalid mb type in I Frame at 0 25
[mpeg2video @ 0x2ab0db7ccfd0]invalid mb type in I Frame at 0 26
[mpeg2video @ 0x2ab0db7ccfd0]invalid mb type in I Frame at 0 27
[mpeg2video @ 0x2ab0db7ccfd0]invalid mb type in I Frame at 0 28
[mpeg2video @ 0x2ab0db7ccfd0]invalid mb type in I Frame at 0 29
[mpeg2video @ 0x2ab0db7ccfd0]Warning MVs not available
2007-10-23 20:52:39.545 MainServer::HandleAnnounce Monitor
2007-10-23 20:52:39.549 adding: mythserver as a client (events: 0)
2007-10-23 20:52:39.550 MainServer::HandleAnnounce Monitor
2007-10-23 20:52:39.551 adding: mythserver as a client (events: 1)
2007-10-23 20:56:35.166 RingBuf(/var/lib/mythtv/recordings/1007_20071023200000.mpg): Waited 1.0 seconds for data to become available...
[mpeg2video @ 0x2ab0db7ccfd0]ac-tex damaged at 16 11
2007-10-23 20:56:35.764 commflag: Commercial Flagging Finished: Cavemen "The Mascot" recorded from channel 1007 at Tue Oct 23 20:00:00 2007: 3 commercial break(s)
2007-10-23 20:56:35.767 JobQueue: Commercial Flagging Finished, 3 break(s) found.
0: start_time: 0.036 duration: 161.700
1: start_time: 0.026 duration: 161.676
stream: start_time: 0.289 duration: 1796.773 bitrate=7185 kb/s
2007-10-23 20:56:35.789 AFD: Opened codec 0x7e0160, id(MPEG2VIDEO) type(Video)
2007-10-23 20:56:35.799 AFD: Opened codec 0x7e0600, id(MP2) type(Audio)
2007-10-23 20:56:35.803 NVP: Recording does not have position map.
			Run 'mythcommflag --file 1007_20071023200000.mpg --rebuild' to fix
2007-10-23 21:00:59.418 Reschedule requested for id 2.
2007-10-23 21:00:59.619 DB Error (AddNewRecords):
Query was:
SELECT DISTINCT channel.chanid, channel.sourceid, program.starttime, program.endtime, program.title, program.subtitle, program.description, channel.channum, channel.callsign, channel.name, oldrecorded.endtime IS NOT NULL AS oldrecduplicate, program.category, record.recpriority, record.dupin, recorded.endtime IS NOT NULL AS recduplicate, oldfind.findid IS NOT NULL AS findduplicate, record.type, record.recordid, program.starttime - INTERVAL record.startoffset minute AS recstartts, program.endtime + INTERVAL record.endoffset minute AS recendts, program.previouslyshown, record.recgroup, record.dupmethod, channel.commfree, capturecard.cardid, cardinput.cardinputid, UPPER(cardinput.shareable) = 'Y' AS shareable, program.seriesid, program.programid, program.category_type, program.airdate, program.stars, program.originalairdate, record.inactive, record.parentid, (CASE record.type   WHEN 6    THEN record.findid   WHEN 9    THEN to_days(date_sub(program.starttime, interval                 time_format(record.findtime, '%H:%i') hour_minute))   WHEN 10    THEN floor((to_days(date_sub(program.starttime, interval                time_format(record.findtime, '%H:%i') hour_minute)) -                record.findday)/7) * 7 + record.findday   WHEN 7    THEN record.findid   ELSE 0  END) , record.playgroup, oldrecstatus.recstatus, oldrecstatus.reactivate, channel.recpriority + cardinput.recpriority, record.prefinput, program.hdtv, program.closecaptioned, program.first, program.last, program.stereo FROM recordmatch  INNER JOIN record ON (recordmatch.recordid = record.recordid)  INNER JOIN program ON (recordmatch.chanid = program.chanid AND                         recordmatch.starttime = program.starttime AND                         recordmatch.manualid = program.manualid)  INNER JOIN channel ON (channel.chanid = program.chanid)  INNER JOIN cardinput ON (channel.sourceid = cardinput.sourceid)  INNER JOIN capturecard ON (capturecard.cardid = cardinput.cardid)  LEFT JOIN oldrecorded as oldrecstatus ON   ( oldrecstatus.station = channel.callsign AND     oldrecstatus.starttime = program.starttime AND     oldrecstatus.title = program.title )  LEFT JOIN oldrecorded ON   (     record.dupmethod > 1 AND     oldrecorded.duplicate <> 0 AND     program.title = oldrecorded.title      AND      (       (program.programid <> '' AND program.generic = 0        AND program.programid = oldrecorded.programid)       OR       (oldrecorded.findid <> 0 AND         oldrecorded.findid = (CASE record.type   WHEN 6    THEN record.findid   WHEN 9    THEN to_days(date_sub(program.starttime, interval                 time_format(record.findtime, '%H:%i') hour_minute))   WHEN 10    THEN floor((to_days(date_sub(program.starttime, interval                time_format(record.findtime, '%H:%i') hour_minute)) -                record.findday)/7) * 7 + record.findday   WHEN 7    THEN record.findid   ELSE 0  END) )       OR       (        program.generic = 0        AND        (program.programid = '' OR oldrecorded.programid = '')        AND        (((record.dupmethod & 0x02) = 0) OR (program.subtitle <> ''           AND program.subtitle = oldrecorded.subtitle))        AND        (((record.dupmethod & 0x04) = 0) OR (program.description <> ''           AND program.description = oldrecorded.description))       )      )   )  LEFT JOIN recorded ON   (     record.dupmethod > 1 AND     recorded.duplicate <> 0 AND     program.title = recorded.title AND     recorded.recgroup <> 'LiveTV'      AND      (       (program.programid <> '' AND program.generic = 0        AND program.programid = recorded.programid)       OR       (recorded.findid <> 0 AND         recorded.findid = (CASE record.type   WHEN 6    THEN record.findid   WHEN 9    THEN to_days(date_sub(program.starttime, interval                 time_format(record.findtime, '%H:%i') hour_minute))   WHEN 10    THEN floor((to_days(date_sub(program.starttime, interval                time_format(record.findtime, '%H:%i') hour_minute)) -                record.findday)/7) * 7 + record.findday   WHEN 7    THEN record.findid   ELSE 0  END) )       OR       (        program.generic = 0        AND        (program.programid = '' OR recorded.programid = '')        AND        (((record.dupmethod & 0x02) = 0) OR (program.subtitle <> ''           AND program.subtitle = recorded.subtitle))        AND        (((record.dupmethod & 0x04) = 0) OR (program.description <> ''           AND program.description = recorded.description))       )      )   )  LEFT JOIN oldfind ON   (oldfind.recordid = recordmatch.recordid AND    oldfind.findid = (CASE record.type   WHEN 6    THEN record.findid   WHEN 9    THEN to_days(date_sub(program.starttime, interval                 time_format(record.findtime, '%H:%i') hour_minute))   WHEN 10    THEN floor((to_days(date_sub(program.starttime, interval                time_format(record.findtime, '%H:%i') hour_minute)) -                record.findday)/7) * 7 + record.findday   WHEN 7    THEN record.findid   ELSE 0  END) )  ORDER BY record.recordid DESC
Driver error was [2/145]:
QMYSQL3: Unable to execute query
Database error was:
Table './mythconverg/oldrecorded' is marked as crashed and should be repaired

2007-10-23 21:00:59.622 Scheduled 0 items in 0.3 = 0.27 match + 0.01 place
2007-10-23 21:00:59.625 scheduler: Scheduled items: Scheduled 0 items in 0.3 = 0.27 match + 0.01 place

```

Currently, I can watch live tv on both tuners, but when I go to the program listing to schedule a recording every timeslot shows unknown. It seems like my database is royally screwed.

Any advice to fix this? I really love myth and ubuntu, but crashes like these push me closer buying a tivo.

---

### Post by napsilan on 2007-10-25
try 
```
mythfilldatabase --do-channel-updates
```

If that doesn't work

```

mysqlcheck -r -u mythtv -pmythtv mythconverg

```

---

### Post by superm1 on 2007-10-25
> **napsilan said:**
> try 
```
mythfilldatabase --do-channel-updates
```If that doesn't work

I'm less than optimistic on this.  The issue looks like the oldrecorded table, so guide data won't necessarily fix this.
> 
```

mysqlcheck -r -u mythtv -pmythtv mythconverg

```

Be sure to substitute in the password being used for the mythtv user in the -p field.

So it will be
```
mysqlcheck -r -u mythtv -pblahblah mythconverg
```

You can get this password from```
 /etc/mythtv/mysql.txt
```

---

### Post by crmullins on 2007-10-26
I can now see the guide data on the program guide screen after doing a mysqlcheck:
```

cmullins@mythserver:~$ mysqlcheck -r -u mythtv -pblahblah mythconverg
mythconverg.archiveitems                           OK
mythconverg.callsignnetworkmap                     OK
mythconverg.capturecard                            OK
mythconverg.cardinput                              OK
mythconverg.channel                                OK
mythconverg.codecparams                            OK
mythconverg.credits                                OK
mythconverg.customexample                          OK
mythconverg.diseqc_config                          OK
mythconverg.diseqc_tree                            OK
mythconverg.dtv_multiplex                          OK
mythconverg.dtv_privatetypes                       OK
mythconverg.dvdinput                               OK
mythconverg.dvdtranscode                           OK
mythconverg.eit_cache                              OK
mythconverg.favorites                              OK
mythconverg.filemarkup                             OK
mythconverg.gallerymetadata                        OK
mythconverg.gamemetadata                           OK
mythconverg.gameplayers                            OK
mythconverg.housekeeping                           OK
mythconverg.inuseprograms                          OK
mythconverg.jobqueue                               OK
mythconverg.jumppoints                             OK
mythconverg.keybindings                            OK
mythconverg.keyword                                OK
mythconverg.music_albums                           OK
mythconverg.music_artists                          OK
mythconverg.music_genres                           OK
mythconverg.music_playlists                        OK
mythconverg.music_smartplaylist_categories         OK
mythconverg.music_smartplaylist_items              OK
mythconverg.music_smartplaylists                   OK
mythconverg.music_songs                            OK
mythconverg.music_stats                            OK
mythconverg.musicmetadata                          OK
mythconverg.musicplaylist                          OK
mythconverg.mythlog                                OK
mythconverg.networkiconmap                         OK
mythconverg.oldfind                                OK
mythconverg.oldprogram                             OK
mythconverg.oldrecorded
info     : Found link that points at 21080 (outside data file) at 11936
info     : Found block that points outside data file at 12212
warning  : Number of rows changed from 103 to 102
status   : OK
mythconverg.people                                 OK
mythconverg.phonecallhistory                       OK
mythconverg.phonedirectory                         OK
mythconverg.pidcache                               OK
mythconverg.playgroup                              OK
mythconverg.profilegroups                          OK
mythconverg.program                                OK
mythconverg.programgenres                          OK
mythconverg.programrating                          OK
mythconverg.recgrouppassword                       OK
mythconverg.record                                 OK
mythconverg.recorded                               OK
mythconverg.recordedcredits                        OK
mythconverg.recordedmarkup                         OK
mythconverg.recordedprogram                        OK
mythconverg.recordedrating                         OK
mythconverg.recordedseek
warning  : Number of rows changed from 207000 to 206940
status   : OK
mythconverg.recordingprofiles                      OK
mythconverg.recordmatch                            OK
mythconverg.romdb                                  OK
mythconverg.schemalock                             OK
mythconverg.settings                               OK
mythconverg.streams                                OK
mythconverg.tvchain                                OK
mythconverg.videocategory                          OK
mythconverg.videocountry                           OK
mythconverg.videogenre                             OK
mythconverg.videometadata                          OK
mythconverg.videometadatacountry                   OK
mythconverg.videometadatagenre                     OK
mythconverg.videosource                            OK
mythconverg.videotypes                             OK
cmullins@mythserver:~$ 

```

But all my future scheduled recordings are hosed, even though all my scheduling priorities still exist. Any easy way to fix this other than brute force rescheduling everything?

Also, any ideas how I got into this predictament in the first place? I don't want this to happen again if I can avoid it.

Thanks

---

### Post by crmullins on 2007-10-26
Perhaps superm1 will respond if i say, "Go Cyclones!"

---

### Post by superm1 on 2007-10-28
> **crmullins said:**
> Perhaps superm1 will respond if i say, "Go Cyclones!"

I've been traveling and just got situated.  :)

Most common cause would be if you shut down the box while it was writing data to the SQL tables, or if it froze when doing this.  Otherwise, shouldn't really happen again.

As for rescheduling everything, I think that next time you run mythfilldatabase, it will do this for you.

---

### Post by crmullins on 2007-10-30
You were right about the mythfilldatabase superm1 :KS. All my future recordings were appropriately set after the mythfilldatabase, but tonight around 21:34 myth restarted itself in the middle of a recording.

Why am I having so many issues now after 3 weeks of no problems? I didn't change any settings. I didn't schedule anymore shows. It seems like I have these problems while I'm recording shows on both tuners and also comm flagging a previously recorded show.

Here is my mythbackend.log:
```
2007-10-29 20:00:02.498 TVRec(1): Changing from None to RecordingOnly
2007-10-29 20:00:02.506 TVRec(1): HW Tuner: 1->1
2007-10-29 20:00:02.764 MPEGRec(/dev/video0) Error: Error getting codec params using old IVTV ioctl
			eno: Bad address (14)
2007-10-29 20:00:02.766 Started recording: Chuck "Chuck Versus the Sandworm": channel 1003 on cardid 1, sourceid 1
2007-10-29 20:00:02.806 scheduler: Started recording: Chuck "Chuck Versus the Sandworm": channel 1003 on cardid 1, sourceid 1
2007-10-29 21:00:00.549 TVRec(1): Changing from RecordingOnly to None
2007-10-29 21:00:00.596 Finished recording Chuck "Chuck Versus the Sandworm": channel 1003
2007-10-29 21:00:00.631 scheduler: Finished recording: Chuck "Chuck Versus the Sandworm": channel 1003
2007-10-29 21:00:00.848 Finished recording Chuck "Chuck Versus the Sandworm": channel 1003
0: start_time: 0.036 duration: 323.696
1: start_time: 0.026 duration: 323.678
stream: start_time: 0.289 duration: 3596.737 bitrate=7185 kb/s
2007-10-29 21:00:00.902 AFD: Opened codec 0x82cf60, id(MPEG2VIDEO) type(Video)
2007-10-29 21:00:00.906 AFD: Opened codec 0x813310, id(MP2) type(Audio)
2007-10-29 21:00:02.619 TVRec(1): Changing from None to RecordingOnly
2007-10-29 21:00:02.627 TVRec(1): HW Tuner: 1->1
2007-10-29 21:00:02.790 MPEGRec(/dev/video0) Error: Error getting codec params using old IVTV ioctl
			eno: Bad address (14)
2007-10-29 21:00:02.797 Started recording: Heroes "The Line": channel 1003 on cardid 1, sourceid 1
2007-10-29 21:00:02.819 scheduler: Last message repeated 1 times: Finished recording: Chuck "Chuck Versus the Sandworm": channel 1003
2007-10-29 21:00:02.822 scheduler: Started recording: Heroes "The Line": channel 1003 on cardid 1, sourceid 1
2007-10-29 21:00:03.885 Reschedule requested for id 0.
2007-10-29 21:00:04.193 Scheduled 66 items in 0.3 = 0.00 match + 0.31 place
2007-10-29 21:00:04.196 scheduler: Scheduled items: Scheduled 66 items in 0.3 = 0.00 match + 0.31 place
2007-10-29 21:00:58.584 JobQueue: Commercial Flagging Starting for Chuck "Chuck Versus the Sandworm" recorded from channel 1003 at Mon Oct 29 20:00:00 2007
2007-10-29 21:00:58.591 commflag: Commercial Flagging Starting: Chuck "Chuck Versus the Sandworm" recorded from channel 1003 at Mon Oct 29 20:00:00 2007
2007-10-29 21:00:59.432 Using runtime prefix = /usr
2007-10-29 21:00:59.568 New DB connection, total: 1
2007-10-29 21:00:59.618 Connected to database 'mythconverg' at host: localhost
2007-10-29 21:00:59.623 New DB connection, total: 2
2007-10-29 21:00:59.624 Connected to database 'mythconverg' at host: localhost
2007-10-29 21:00:59.645 Connecting to backend server: 127.0.0.1:6543 (try 1 of 5)
2007-10-29 21:00:59.647 Using protocol version 31
2007-10-29 21:00:59.648 MainServer::HandleAnnounce Monitor
2007-10-29 21:00:59.649 adding: mythserver as a client (events: 0)
2007-10-29 21:00:59.656 MainServer::HandleAnnounce Monitor
2007-10-29 21:00:59.657 adding: mythserver as a client (events: 1)
0: start_time: 0.036 duration: 323.696
1: start_time: 0.026 duration: 323.678
stream: start_time: 0.289 duration: 3596.737 bitrate=7185 kb/s
2007-10-29 21:00:59.689 AFD: Opened codec 0x734c50, id(MPEG2VIDEO) type(Video)
2007-10-29 21:00:59.702 AFD: Opened codec 0x735020, id(MP2) type(Audio)
[mpeg2video @ 0x2b5a6ec43fb0]00 motion_type at 9 0
[mpeg2video @ 0x2b5a6ec43fb0]Warning MVs not available
2007-10-29 21:30:02.170 TVRec(2): Changing from None to RecordingOnly
2007-10-29 21:30:02.188 TVRec(2): HW Tuner: 2->2
2007-10-29 21:30:02.409 MPEGRec(/dev/video1) Error: Error getting codec params using old IVTV ioctl
			eno: Bad address (14)
2007-10-29 21:30:02.435 Started recording: South Park "Pink Eye": channel 1063 on cardid 2, sourceid 1
2007-10-29 21:30:02.481 scheduler: Started recording: South Park "Pink Eye": channel 1063 on cardid 2, sourceid 1
2007-10-29 21:34:12.627 Using runtime prefix = /usr
2007-10-29 21:34:12.765 New DB connection, total: 1
2007-10-29 21:34:12.814 Connected to database 'mythconverg' at host: localhost
2007-10-29 21:34:12.961 Current Schema Version: 1160
Starting up as the master server.
2007-10-29 21:34:13.087 New DB connection, total: 2
2007-10-29 21:34:13.088 Connected to database 'mythconverg' at host: localhost
2007-10-29 21:34:13.089 mythbackend: MythBackend started as master server
2007-10-29 21:34:13.464 EITHelper: localtime offset -7:00:00 
2007-10-29 21:34:13.470 New DB connection, total: 3
2007-10-29 21:34:13.471 Connected to database 'mythconverg' at host: localhost
2007-10-29 21:34:13.677 EITHelper: localtime offset -7:00:00 
2007-10-29 21:34:14.023 New DB scheduler connection
2007-10-29 21:34:14.025 Connected to database 'mythconverg' at host: localhost
2007-10-29 21:34:14.105 DB Error (Error in JobQueue::GetJobs(), Unable to query list of Jobs in Queue.):
Query was:
SELECT j.id, j.chanid, j.starttime, j.inserttime, j.type, j.cmds, j.flags, j.status, j.statustime, j.hostname, j.args, j.comment, r.endtime FROM jobqueue j, recorded r WHERE j.chanid = r.chanid AND j.starttime = r.starttime ORDER BY j.inserttime, j.chanid, j.id;
Driver error was [2/145]:
QMYSQL3: Unable to execute query
Database error was:
Table './mythconverg/jobqueue' is marked as crashed and should be repaired

2007-10-29 21:34:14.111 QMulticastSocket: setsockopt - IP_ADD_MEMBERSHIP Error
2007-10-29 21:34:14.414 QMulticastSocket: setsockopt - IP_ADD_MEMBERSHIP Error
2007-10-29 21:34:15.876 Main::Registering HttpStatus Extension
2007-10-29 21:34:15.876 QMulticastSocket: setsockopt - IP_ADD_MEMBERSHIP Error
2007-10-29 21:34:15.880 mythbackend version: 0.20.20070821-1 www.mythtv.org
2007-10-29 21:34:15.901 Enabled verbose msgs:  important general
2007-10-29 21:34:15.953 AutoExpire: Found 2 recorders w/max rate of 144 MiB/min
2007-10-29 21:34:16.250 AutoExpire: Required Free Space: 3.1 GB w/freq: 10 min
2007-10-29 21:34:16.123 Reschedule requested for id -1.
2007-10-29 21:34:16.472 Scheduled 66 items in 0.3 = 0.22 match + 0.13 place
2007-10-29 21:34:16.485 scheduler: Scheduled items: Scheduled 66 items in 0.3 = 0.22 match + 0.13 place
2007-10-29 21:34:16.520 Recording starts soon, AUTO-Startup assumed
2007-10-29 21:34:16.576 DB Error (Clear seek info on record):
Query was:
DELETE FROM recordedseek WHERE chanid = '1003' AND starttime = '2007-10-29T21:34:00';
Driver error was [2/145]:
QMYSQL3: Unable to execute query
Database error was:
Table './mythconverg/recordedseek' is marked as crashed and should be repaired

2007-10-29 21:34:16.610 TVRec(1): Changing from None to RecordingOnly
2007-10-29 21:34:16.619 TVRec(1): HW Tuner: 1->1
2007-10-29 21:34:16.864 MPEGRec(/dev/video0) Error: Error getting codec params using old IVTV ioctl
			eno: Bad address (14)
2007-10-29 21:34:16.865 Started recording: Heroes "The Line": channel 1003 on cardid 1, sourceid 1
2007-10-29 21:34:16.904 scheduler: Started recording: Heroes "The Line": channel 1003 on cardid 1, sourceid 1
2007-10-29 21:34:16.935 DB Error (Clear seek info on record):
Query was:
DELETE FROM recordedseek WHERE chanid = '1063' AND starttime = '2007-10-29T21:34:00';
Driver error was [2/145]:
QMYSQL3: Unable to execute query
Database error was:
Table './mythconverg/recordedseek' is marked as crashed and should be repaired

2007-10-29 21:34:16.964 TVRec(2): Changing from None to RecordingOnly
2007-10-29 21:34:16.975 TVRec(2): HW Tuner: 2->2
2007-10-29 21:34:17.138 MPEGRec(/dev/video1) Error: Error getting codec params using old IVTV ioctl
			eno: Bad address (14)
2007-10-29 21:34:17.139 Started recording: South Park "Pink Eye": channel 1063 on cardid 2, sourceid 1
2007-10-29 21:34:17.168 scheduler: Started recording: South Park "Pink Eye": channel 1063 on cardid 2, sourceid 1
2007-10-29 21:34:17.742 DB Error (delta position map insert):
Query was:
INSERT INTO recordedseek (chanid, starttime, mark, type, offset) VALUES ( '1003' , '2007-10-29T21:34:00' , '1' , 6 , '0' );
Driver error was [2/145]:
QMYSQL3: Unable to execute query
Database error was:
Table './mythconverg/recordedseek' is marked as crashed and should be repaired

2007-10-29 21:34:17.993 DB Error (delta position map insert):
Query was:
INSERT INTO recordedseek (chanid, starttime, mark, type, offset) VALUES ( '1063' , '2007-10-29T21:34:00' , '1' , 6 , '0' );
Driver error was [2/145]:
QMYSQL3: Unable to execute query
Database error was:
Table './mythconverg/recordedseek' is marked as crashed and should be repaired

2007-10-29 21:34:20.226 DB Error (delta position map insert):
Query was:
INSERT INTO recordedseek (chanid, starttime, mark, type, offset) VALUES ( '1003' , '2007-10-29T21:34:00' , '2' , 6 , '409600' );
Driver error was [2/145]:
QMYSQL3: Unable to execute query
Database error was:
Table './mythconverg/recordedseek' is marked as crashed and should be repaired

2007-10-29 21:34:20.269 DB Error (delta position map insert):
Query was:
INSERT INTO recordedseek (chanid, starttime, mark, type, offset) VALUES ( '1003' , '2007-10-29T21:34:00' , '3' , 6 , '888832' );
Driver error was [2/145]:
QMYSQL3: Unable to execute query
Database error was:
Table './mythconverg/recordedseek' is marked as crashed and should be repaired

2007-10-29 21:34:20.270 DB Error (delta position map insert):
Query was:
INSERT INTO recordedseek (chanid, starttime, mark, type, offset) VALUES ( '1003' , '2007-10-29T21:34:00' , '4' , 6 , '1370112' );
Driver error was [2/145]:
QMYSQL3: Unable to execute query
Database error was:
Table './mythconverg/recordedseek' is marked as crashed and should be repaired

2007-10-29 21:34:20.272 DB Error (delta position map insert):
Query was:
INSERT INTO recordedseek (chanid, starttime, mark, type, offset) VALUES ( '1003' , '2007-10-29T21:34:00' , '5' , 6 , '1847296' );
Driver error was [2/145]:
QMYSQL3: Unable to execute query
Database error was:
Table './mythconverg/recordedseek' is marked as crashed and should be repaired

2007-10-29 21:34:20.273 DB Error (delta position map insert):
Query was:
INSERT INTO recordedseek (chanid, starttime, mark, type, offset) VALUES ( '1003' , '2007-10-29T21:34:00' , '6' , 6 , '2367488' );
Driver error was [2/145]:
QMYSQL3: Unable to execute query
Database error was:
Table './mythconverg/recordedseek' is marked as crashed and should be repaired

2007-10-29 21:34:20.474 DB Error (delta position map insert):
Query was:
INSERT INTO recordedseek (chanid, starttime, mark, type, offset) VALUES ( '1063' , '2007-10-29T21:34:00' , '2' , 6 , '413696' );
Driver error was [2/145]:
QMYSQL3: Unable to execute query
Database error was:
Table './mythconverg/recordedseek' is marked as crashed and should be repaired

2007-10-29 21:34:20.606 DB Error (delta position map insert):
Query was:
INSERT INTO recordedseek (chanid, starttime, mark, type, offset) VALUES ( '1063' , '2007-10-29T21:34:00' , '3' , 6 , '892928' );
Driver error was [2/145]:
QMYSQL3: Unable to execute query
Database error was:
Table './mythconverg/recordedseek' is marked as crashed and should be repaired

2007-10-29 21:34:20.608 DB Error (delta position map insert):
Query was:
INSERT INTO recordedseek (chanid, starttime, mark, type, offset) VALUES ( '1063' , '2007-10-29T21:34:00' , '4' , 6 , '1368064' );
Driver error was [2/145]:
QMYSQL3: Unable to execute query
Database error was:
Table './mythconverg/recordedseek' is marked as crashed and should be repaired

2007-10-29 21:34:20.610 DB Error (delta position map insert):
Query was:
INSERT INTO recordedseek (chanid, starttime, mark, type, offset) VALUES ( '1063' , '2007-10-29T21:34:00' , '5' , 6 , '1873920' );
Driver error was [2/145]:
QMYSQL3: Unable to execute query
Database error was:
Table './mythconverg/recordedseek' is marked as crashed and should be repaired

2007-10-29 21:34:20.611 DB Error (delta position map insert):
Query was:
INSERT INTO recordedseek (chanid, starttime, mark, type, offset) VALUES ( '1063' , '2007-10-29T21:34:00' , '6' , 6 , '2387968' );
Driver error was [2/145]:
QMYSQL3: Unable to execute query
Database error was:
Table './mythconverg/recordedseek' is marked as crashed and should be repaired

2007-10-29 21:34:22.726 DB Error (delta position map insert):
Query was:
INSERT INTO recordedseek (chanid, starttime, mark, type, offset) VALUES ( '1003' , '2007-10-29T21:34:00' , '7' , 6 , '2848768' );
Driver error was [2/145]:
QMYSQL3: Unable to execute query
Database error was:
Table './mythconverg/recordedseek' is marked as crashed and should be repaired

2007-10-29 21:34:22.978 DB Error (delta position map insert):
Query was:
INSERT INTO recordedseek (chanid, starttime, mark, type, offset) VALUES ( '1063' , '2007-10-29T21:34:00' , '7' , 6 , '2824192' );
Driver error was [2/145]:
QMYSQL3: Unable to execute query
Database error was:
Table './mythconverg/recordedseek' is marked as crashed and should be repaired

2007-10-29 21:34:23.046 DB Error (delta position map insert):
Query was:
INSERT INTO recordedseek (chanid, starttime, mark, type, offset) VALUES ( '1003' , '2007-10-29T21:34:00' , '8' , 6 , '3301376' );
Driver error was [2/145]:
QMYSQL3: Unable to execute query
Database error was:
Table './mythconverg/recordedseek' is marked as crashed and should be repaired

2007-10-29 21:34:23.099 New DB connection, total: 4
2007-10-29 21:34:23.279 DB Error (delta position map insert):
Query was:
INSERT INTO recordedseek (chanid, starttime, mark, type, offset) VALUES ( '1063' , '2007-10-29T21:34:00' , '8' , 6 , '3254272' );
Driver error was [2/145]:
QMYSQL3: Unable to execute query
Database error was:
Table './mythconverg/recordedseek' is marked as crashed and should be repaired

2007-10-29 21:34:23.304 DB Error (delta position map insert):
Query was:
INSERT INTO recordedseek (chanid, starttime, mark, type, offset) VALUES ( '1003' , '2007-10-29T21:34:00' , '9' , 6 , '3741696' );
Driver error was [2/145]:
QMYSQL3: Unable to execute query
Database error was:
Table './mythconverg/recordedseek' is marked as crashed and should be repaired

2007-10-29 21:34:23.991 Connected to database 'mythconverg' at host: localhost
2007-10-29 21:34:24.200 DB Error (delta position map insert):
Query was:
INSERT INTO recordedseek (chanid, starttime, mark, type, offset) VALUES ( '1063' , '2007-10-29T21:34:00' , '9' , 6 , '3731456' );
Driver error was [2/145]:
QMYSQL3: Unable to execute query
Database error was:
Table './mythconverg/recordedseek' is marked as crashed and should be repaired

2007-10-29 21:34:24.290 New DB connection, total: 5
2007-10-29 21:34:24.671 DB Error (delta position map insert):
Query was:
INSERT INTO recordedseek (chanid, starttime, mark, type, offset) VALUES ( '1003' , '2007-10-29T21:34:00' , '10' , 6 , '4220928' );
Driver error was [2/145]:
QMYSQL3: Unable to execute query
Database error was:
Table './mythconverg/recordedseek' is marked as crashed and should be repaired

2007-10-29 21:34:25.071 DB Error (delta position map insert):
Query was:
INSERT INTO recordedseek (chanid, starttime, mark, type, offset) VALUES ( '1063' , '2007-10-29T21:34:00' , '10' , 6 , '4206592' );
Driver error was [2/145]:
QMYSQL3: Unable to execute query
Database error was:
Table './mythconverg/recordedseek' is marked as crashed and should be repaired

2007-10-29 21:34:25.074 mythbackend: Running housekeeping thread
2007-10-29 21:34:25.074 Connected to database 'mythconverg' at host: localhost
2007-10-29 21:34:25.079 DB Error (delta position map insert):
Query was:
INSERT INTO recordedseek (chanid, starttime, mark, type, offset) VALUES ( '1003' , '2007-10-29T21:34:00' , '11' , 6 , '4698112' );
Driver error was [2/145]:
QMYSQL3: Unable to execute query
Database error was:
Table './mythconverg/recordedseek' is marked as crashed and should be repaired

2007-10-29 21:34:25.083 DB Error (delta position map insert):
Query was:
INSERT INTO recordedseek (chanid, starttime, mark, type, offset) VALUES ( '1063' , '2007-10-29T21:34:00' , '11' , 6 , '4734976' );
Driver error was [2/145]:
QMYSQL3: Unable to execute query
Database error was:
Table './mythconverg/recordedseek' is marked as crashed and should be repaired

2007-10-29 21:34:25.106 DB Error (Error in JobQueue::GetJobs(), Unable to query list of Jobs in Queue.):
Query was:
SELECT j.id, j.chanid, j.starttime, j.inserttime, j.type, j.cmds, j.flags, j.status, j.statustime, j.hostname, j.args, j.comment, r.endtime FROM jobqueue j, recorded r WHERE j.chanid = r.chanid AND j.starttime = r.starttime ORDER BY j.inserttime, j.chanid, j.id;
Driver error was [2/145]:
QMYSQL3: Unable to execute query
Database error was:
Table './mythconverg/jobqueue' is marked as crashed and should be repaired

2007-10-29 21:34:25.230 DB Error (delta position map insert):
Query was:
INSERT INTO recordedseek (chanid, starttime, mark, type, offset) VALUES ( '1003' , '2007-10-29T21:34:00' , '12' , 6 , '5175296' );
Driver error was [2/145]:
QMYSQL3: Unable to execute query
Database error was:
Table './mythconverg/recordedseek' is marked as crashed and should be repaired

2007-10-29 21:34:25.438 DB Error (delta position map insert):
Query was:
INSERT INTO recordedseek (chanid, starttime, mark, type, offset) VALUES ( '1003' , '2007-10-29T21:34:00' , '13' , 6 , '5496832' );
Driver error was [2/145]:
QMYSQL3: Unable to execute query
Database error was:
Table './mythconverg/recordedseek' is marked as crashed and should be repaired

```

---

### Post by superm1 on 2007-10-30
> **crmullins said:**
> You were right about the mythfilldatabase superm1 :KS. All my future recordings were appropriately set after the mythfilldatabase, but tonight around 21:34 myth restarted itself in the middle of a recording.

Why am I having so many issues now after 3 weeks of no problems? I didn't change any settings. I didn't schedule anymore shows. It seems like I have these problems while I'm recording shows on both tuners and also comm flagging a previously recorded show.

Here is my mythbackend.log:
```
2007-10-29 20:00:02.498 TVRec(1): Changing from None to RecordingOnly
2007-10-29 20:00:02.506 TVRec(1): HW Tuner: 1->1
2007-10-29 20:00:02.764 MPEGRec(/dev/video0) Error: Error getting codec params using old IVTV ioctl
            eno: Bad address (14)
2007-10-29 20:00:02.766 Started recording: Chuck "Chuck Versus the Sandworm": channel 1003 on cardid 1, sourceid 1
2007-10-29 20:00:02.806 scheduler: Started recording: Chuck "Chuck Versus the Sandworm": channel 1003 on cardid 1, sourceid 1
2007-10-29 21:00:00.549 TVRec(1): Changing from RecordingOnly to None
2007-10-29 21:00:00.596 Finished recording Chuck "Chuck Versus the Sandworm": channel 1003
2007-10-29 21:00:00.631 scheduler: Finished recording: Chuck "Chuck Versus the Sandworm": channel 1003
2007-10-29 21:00:00.848 Finished recording Chuck "Chuck Versus the Sandworm": channel 1003
0: start_time: 0.036 duration: 323.696
1: start_time: 0.026 duration: 323.678
stream: start_time: 0.289 duration: 3596.737 bitrate=7185 kb/s
2007-10-29 21:00:00.902 AFD: Opened codec 0x82cf60, id(MPEG2VIDEO) type(Video)
2007-10-29 21:00:00.906 AFD: Opened codec 0x813310, id(MP2) type(Audio)
2007-10-29 21:00:02.619 TVRec(1): Changing from None to RecordingOnly
2007-10-29 21:00:02.627 TVRec(1): HW Tuner: 1->1
2007-10-29 21:00:02.790 MPEGRec(/dev/video0) Error: Error getting codec params using old IVTV ioctl
            eno: Bad address (14)
2007-10-29 21:00:02.797 Started recording: Heroes "The Line": channel 1003 on cardid 1, sourceid 1
2007-10-29 21:00:02.819 scheduler: Last message repeated 1 times: Finished recording: Chuck "Chuck Versus the Sandworm": channel 1003
2007-10-29 21:00:02.822 scheduler: Started recording: Heroes "The Line": channel 1003 on cardid 1, sourceid 1
2007-10-29 21:00:03.885 Reschedule requested for id 0.
2007-10-29 21:00:04.193 Scheduled 66 items in 0.3 = 0.00 match + 0.31 place
2007-10-29 21:00:04.196 scheduler: Scheduled items: Scheduled 66 items in 0.3 = 0.00 match + 0.31 place
2007-10-29 21:00:58.584 JobQueue: Commercial Flagging Starting for Chuck "Chuck Versus the Sandworm" recorded from channel 1003 at Mon Oct 29 20:00:00 2007
2007-10-29 21:00:58.591 commflag: Commercial Flagging Starting: Chuck "Chuck Versus the Sandworm" recorded from channel 1003 at Mon Oct 29 20:00:00 2007
2007-10-29 21:00:59.432 Using runtime prefix = /usr
2007-10-29 21:00:59.568 New DB connection, total: 1
2007-10-29 21:00:59.618 Connected to database 'mythconverg' at host: localhost
2007-10-29 21:00:59.623 New DB connection, total: 2
2007-10-29 21:00:59.624 Connected to database 'mythconverg' at host: localhost
2007-10-29 21:00:59.645 Connecting to backend server: 127.0.0.1:6543 (try 1 of 5)
2007-10-29 21:00:59.647 Using protocol version 31
2007-10-29 21:00:59.648 MainServer::HandleAnnounce Monitor
2007-10-29 21:00:59.649 adding: mythserver as a client (events: 0)
2007-10-29 21:00:59.656 MainServer::HandleAnnounce Monitor
2007-10-29 21:00:59.657 adding: mythserver as a client (events: 1)
0: start_time: 0.036 duration: 323.696
1: start_time: 0.026 duration: 323.678
stream: start_time: 0.289 duration: 3596.737 bitrate=7185 kb/s
2007-10-29 21:00:59.689 AFD: Opened codec 0x734c50, id(MPEG2VIDEO) type(Video)
2007-10-29 21:00:59.702 AFD: Opened codec 0x735020, id(MP2) type(Audio)
[mpeg2video @ 0x2b5a6ec43fb0]00 motion_type at 9 0
[mpeg2video @ 0x2b5a6ec43fb0]Warning MVs not available
2007-10-29 21:30:02.170 TVRec(2): Changing from None to RecordingOnly
2007-10-29 21:30:02.188 TVRec(2): HW Tuner: 2->2
2007-10-29 21:30:02.409 MPEGRec(/dev/video1) Error: Error getting codec params using old IVTV ioctl
            eno: Bad address (14)
2007-10-29 21:30:02.435 Started recording: South Park "Pink Eye": channel 1063 on cardid 2, sourceid 1
2007-10-29 21:30:02.481 scheduler: Started recording: South Park "Pink Eye": channel 1063 on cardid 2, sourceid 1
2007-10-29 21:34:12.627 Using runtime prefix = /usr
2007-10-29 21:34:12.765 New DB connection, total: 1
2007-10-29 21:34:12.814 Connected to database 'mythconverg' at host: localhost
2007-10-29 21:34:12.961 Current Schema Version: 1160
Starting up as the master server.
2007-10-29 21:34:13.087 New DB connection, total: 2
2007-10-29 21:34:13.088 Connected to database 'mythconverg' at host: localhost
2007-10-29 21:34:13.089 mythbackend: MythBackend started as master server
2007-10-29 21:34:13.464 EITHelper: localtime offset -7:00:00 
2007-10-29 21:34:13.470 New DB connection, total: 3
2007-10-29 21:34:13.471 Connected to database 'mythconverg' at host: localhost
2007-10-29 21:34:13.677 EITHelper: localtime offset -7:00:00 
2007-10-29 21:34:14.023 New DB scheduler connection
2007-10-29 21:34:14.025 Connected to database 'mythconverg' at host: localhost
2007-10-29 21:34:14.105 DB Error (Error in JobQueue::GetJobs(), Unable to query list of Jobs in Queue.):
Query was:
SELECT j.id, j.chanid, j.starttime, j.inserttime, j.type, j.cmds, j.flags, j.status, j.statustime, j.hostname, j.args, j.comment, r.endtime FROM jobqueue j, recorded r WHERE j.chanid = r.chanid AND j.starttime = r.starttime ORDER BY j.inserttime, j.chanid, j.id;
Driver error was [2/145]:
QMYSQL3: Unable to execute query
Database error was:
Table './mythconverg/jobqueue' is marked as crashed and should be repaired

2007-10-29 21:34:14.111 QMulticastSocket: setsockopt - IP_ADD_MEMBERSHIP Error
2007-10-29 21:34:14.414 QMulticastSocket: setsockopt - IP_ADD_MEMBERSHIP Error
2007-10-29 21:34:15.876 Main::Registering HttpStatus Extension
2007-10-29 21:34:15.876 QMulticastSocket: setsockopt - IP_ADD_MEMBERSHIP Error
2007-10-29 21:34:15.880 mythbackend version: 0.20.20070821-1 www.mythtv.org
2007-10-29 21:34:15.901 Enabled verbose msgs:  important general
2007-10-29 21:34:15.953 AutoExpire: Found 2 recorders w/max rate of 144 MiB/min
2007-10-29 21:34:16.250 AutoExpire: Required Free Space: 3.1 GB w/freq: 10 min
2007-10-29 21:34:16.123 Reschedule requested for id -1.
2007-10-29 21:34:16.472 Scheduled 66 items in 0.3 = 0.22 match + 0.13 place
2007-10-29 21:34:16.485 scheduler: Scheduled items: Scheduled 66 items in 0.3 = 0.22 match + 0.13 place
2007-10-29 21:34:16.520 Recording starts soon, AUTO-Startup assumed
2007-10-29 21:34:16.576 DB Error (Clear seek info on record):
Query was:
DELETE FROM recordedseek WHERE chanid = '1003' AND starttime = '2007-10-29T21:34:00';
Driver error was [2/145]:
QMYSQL3: Unable to execute query
Database error was:
Table './mythconverg/recordedseek' is marked as crashed and should be repaired

2007-10-29 21:34:16.610 TVRec(1): Changing from None to RecordingOnly
2007-10-29 21:34:16.619 TVRec(1): HW Tuner: 1->1
2007-10-29 21:34:16.864 MPEGRec(/dev/video0) Error: Error getting codec params using old IVTV ioctl
            eno: Bad address (14)
2007-10-29 21:34:16.865 Started recording: Heroes "The Line": channel 1003 on cardid 1, sourceid 1
2007-10-29 21:34:16.904 scheduler: Started recording: Heroes "The Line": channel 1003 on cardid 1, sourceid 1
2007-10-29 21:34:16.935 DB Error (Clear seek info on record):
Query was:
DELETE FROM recordedseek WHERE chanid = '1063' AND starttime = '2007-10-29T21:34:00';
Driver error was [2/145]:
QMYSQL3: Unable to execute query
Database error was:
Table './mythconverg/recordedseek' is marked as crashed and should be repaired

2007-10-29 21:34:16.964 TVRec(2): Changing from None to RecordingOnly
2007-10-29 21:34:16.975 TVRec(2): HW Tuner: 2->2
2007-10-29 21:34:17.138 MPEGRec(/dev/video1) Error: Error getting codec params using old IVTV ioctl
            eno: Bad address (14)
2007-10-29 21:34:17.139 Started recording: South Park "Pink Eye": channel 1063 on cardid 2, sourceid 1
2007-10-29 21:34:17.168 scheduler: Started recording: South Park "Pink Eye": channel 1063 on cardid 2, sourceid 1
2007-10-29 21:34:17.742 DB Error (delta position map insert):
Query was:
INSERT INTO recordedseek (chanid, starttime, mark, type, offset) VALUES ( '1003' , '2007-10-29T21:34:00' , '1' , 6 , '0' );
Driver error was [2/145]:
QMYSQL3: Unable to execute query
Database error was:
Table './mythconverg/recordedseek' is marked as crashed and should be repaired

2007-10-29 21:34:17.993 DB Error (delta position map insert):
Query was:
INSERT INTO recordedseek (chanid, starttime, mark, type, offset) VALUES ( '1063' , '2007-10-29T21:34:00' , '1' , 6 , '0' );
Driver error was [2/145]:
QMYSQL3: Unable to execute query
Database error was:
Table './mythconverg/recordedseek' is marked as crashed and should be repaired

2007-10-29 21:34:20.226 DB Error (delta position map insert):
Query was:
INSERT INTO recordedseek (chanid, starttime, mark, type, offset) VALUES ( '1003' , '2007-10-29T21:34:00' , '2' , 6 , '409600' );
Driver error was [2/145]:
QMYSQL3: Unable to execute query
Database error was:
Table './mythconverg/recordedseek' is marked as crashed and should be repaired

2007-10-29 21:34:20.269 DB Error (delta position map insert):
Query was:
INSERT INTO recordedseek (chanid, starttime, mark, type, offset) VALUES ( '1003' , '2007-10-29T21:34:00' , '3' , 6 , '888832' );
Driver error was [2/145]:
QMYSQL3: Unable to execute query
Database error was:
Table './mythconverg/recordedseek' is marked as crashed and should be repaired

2007-10-29 21:34:20.270 DB Error (delta position map insert):
Query was:
INSERT INTO recordedseek (chanid, starttime, mark, type, offset) VALUES ( '1003' , '2007-10-29T21:34:00' , '4' , 6 , '1370112' );
Driver error was [2/145]:
QMYSQL3: Unable to execute query
Database error was:
Table './mythconverg/recordedseek' is marked as crashed and should be repaired

2007-10-29 21:34:20.272 DB Error (delta position map insert):
Query was:
INSERT INTO recordedseek (chanid, starttime, mark, type, offset) VALUES ( '1003' , '2007-10-29T21:34:00' , '5' , 6 , '1847296' );
Driver error was [2/145]:
QMYSQL3: Unable to execute query
Database error was:
Table './mythconverg/recordedseek' is marked as crashed and should be repaired

2007-10-29 21:34:20.273 DB Error (delta position map insert):
Query was:
INSERT INTO recordedseek (chanid, starttime, mark, type, offset) VALUES ( '1003' , '2007-10-29T21:34:00' , '6' , 6 , '2367488' );
Driver error was [2/145]:
QMYSQL3: Unable to execute query
Database error was:
Table './mythconverg/recordedseek' is marked as crashed and should be repaired

2007-10-29 21:34:20.474 DB Error (delta position map insert):
Query was:
INSERT INTO recordedseek (chanid, starttime, mark, type, offset) VALUES ( '1063' , '2007-10-29T21:34:00' , '2' , 6 , '413696' );
Driver error was [2/145]:
QMYSQL3: Unable to execute query
Database error was:
Table './mythconverg/recordedseek' is marked as crashed and should be repaired

2007-10-29 21:34:20.606 DB Error (delta position map insert):
Query was:
INSERT INTO recordedseek (chanid, starttime, mark, type, offset) VALUES ( '1063' , '2007-10-29T21:34:00' , '3' , 6 , '892928' );
Driver error was [2/145]:
QMYSQL3: Unable to execute query
Database error was:
Table './mythconverg/recordedseek' is marked as crashed and should be repaired

2007-10-29 21:34:20.608 DB Error (delta position map insert):
Query was:
INSERT INTO recordedseek (chanid, starttime, mark, type, offset) VALUES ( '1063' , '2007-10-29T21:34:00' , '4' , 6 , '1368064' );
Driver error was [2/145]:
QMYSQL3: Unable to execute query
Database error was:
Table './mythconverg/recordedseek' is marked as crashed and should be repaired

2007-10-29 21:34:20.610 DB Error (delta position map insert):
Query was:
INSERT INTO recordedseek (chanid, starttime, mark, type, offset) VALUES ( '1063' , '2007-10-29T21:34:00' , '5' , 6 , '1873920' );
Driver error was [2/145]:
QMYSQL3: Unable to execute query
Database error was:
Table './mythconverg/recordedseek' is marked as crashed and should be repaired

2007-10-29 21:34:20.611 DB Error (delta position map insert):
Query was:
INSERT INTO recordedseek (chanid, starttime, mark, type, offset) VALUES ( '1063' , '2007-10-29T21:34:00' , '6' , 6 , '2387968' );
Driver error was [2/145]:
QMYSQL3: Unable to execute query
Database error was:
Table './mythconverg/recordedseek' is marked as crashed and should be repaired

2007-10-29 21:34:22.726 DB Error (delta position map insert):
Query was:
INSERT INTO recordedseek (chanid, starttime, mark, type, offset) VALUES ( '1003' , '2007-10-29T21:34:00' , '7' , 6 , '2848768' );
Driver error was [2/145]:
QMYSQL3: Unable to execute query
Database error was:
Table './mythconverg/recordedseek' is marked as crashed and should be repaired

2007-10-29 21:34:22.978 DB Error (delta position map insert):
Query was:
INSERT INTO recordedseek (chanid, starttime, mark, type, offset) VALUES ( '1063' , '2007-10-29T21:34:00' , '7' , 6 , '2824192' );
Driver error was [2/145]:
QMYSQL3: Unable to execute query
Database error was:
Table './mythconverg/recordedseek' is marked as crashed and should be repaired

2007-10-29 21:34:23.046 DB Error (delta position map insert):
Query was:
INSERT INTO recordedseek (chanid, starttime, mark, type, offset) VALUES ( '1003' , '2007-10-29T21:34:00' , '8' , 6 , '3301376' );
Driver error was [2/145]:
QMYSQL3: Unable to execute query
Database error was:
Table './mythconverg/recordedseek' is marked as crashed and should be repaired

2007-10-29 21:34:23.099 New DB connection, total: 4
2007-10-29 21:34:23.279 DB Error (delta position map insert):
Query was:
INSERT INTO recordedseek (chanid, starttime, mark, type, offset) VALUES ( '1063' , '2007-10-29T21:34:00' , '8' , 6 , '3254272' );
Driver error was [2/145]:
QMYSQL3: Unable to execute query
Database error was:
Table './mythconverg/recordedseek' is marked as crashed and should be repaired

2007-10-29 21:34:23.304 DB Error (delta position map insert):
Query was:
INSERT INTO recordedseek (chanid, starttime, mark, type, offset) VALUES ( '1003' , '2007-10-29T21:34:00' , '9' , 6 , '3741696' );
Driver error was [2/145]:
QMYSQL3: Unable to execute query
Database error was:
Table './mythconverg/recordedseek' is marked as crashed and should be repaired

2007-10-29 21:34:23.991 Connected to database 'mythconverg' at host: localhost
2007-10-29 21:34:24.200 DB Error (delta position map insert):
Query was:
INSERT INTO recordedseek (chanid, starttime, mark, type, offset) VALUES ( '1063' , '2007-10-29T21:34:00' , '9' , 6 , '3731456' );
Driver error was [2/145]:
QMYSQL3: Unable to execute query
Database error was:
Table './mythconverg/recordedseek' is marked as crashed and should be repaired

2007-10-29 21:34:24.290 New DB connection, total: 5
2007-10-29 21:34:24.671 DB Error (delta position map insert):
Query was:
INSERT INTO recordedseek (chanid, starttime, mark, type, offset) VALUES ( '1003' , '2007-10-29T21:34:00' , '10' , 6 , '4220928' );
Driver error was [2/145]:
QMYSQL3: Unable to execute query
Database error was:
Table './mythconverg/recordedseek' is marked as crashed and should be repaired

2007-10-29 21:34:25.071 DB Error (delta position map insert):
Query was:
INSERT INTO recordedseek (chanid, starttime, mark, type, offset) VALUES ( '1063' , '2007-10-29T21:34:00' , '10' , 6 , '4206592' );
Driver error was [2/145]:
QMYSQL3: Unable to execute query
Database error was:
Table './mythconverg/recordedseek' is marked as crashed and should be repaired

2007-10-29 21:34:25.074 mythbackend: Running housekeeping thread
2007-10-29 21:34:25.074 Connected to database 'mythconverg' at host: localhost
2007-10-29 21:34:25.079 DB Error (delta position map insert):
Query was:
INSERT INTO recordedseek (chanid, starttime, mark, type, offset) VALUES ( '1003' , '2007-10-29T21:34:00' , '11' , 6 , '4698112' );
Driver error was [2/145]:
QMYSQL3: Unable to execute query
Database error was:
Table './mythconverg/recordedseek' is marked as crashed and should be repaired

2007-10-29 21:34:25.083 DB Error (delta position map insert):
Query was:
INSERT INTO recordedseek (chanid, starttime, mark, type, offset) VALUES ( '1063' , '2007-10-29T21:34:00' , '11' , 6 , '4734976' );
Driver error was [2/145]:
QMYSQL3: Unable to execute query
Database error was:
Table './mythconverg/recordedseek' is marked as crashed and should be repaired

2007-10-29 21:34:25.106 DB Error (Error in JobQueue::GetJobs(), Unable to query list of Jobs in Queue.):
Query was:
SELECT j.id, j.chanid, j.starttime, j.inserttime, j.type, j.cmds, j.flags, j.status, j.statustime, j.hostname, j.args, j.comment, r.endtime FROM jobqueue j, recorded r WHERE j.chanid = r.chanid AND j.starttime = r.starttime ORDER BY j.inserttime, j.chanid, j.id;
Driver error was [2/145]:
QMYSQL3: Unable to execute query
Database error was:
Table './mythconverg/jobqueue' is marked as crashed and should be repaired

2007-10-29 21:34:25.230 DB Error (delta position map insert):
Query was:
INSERT INTO recordedseek (chanid, starttime, mark, type, offset) VALUES ( '1003' , '2007-10-29T21:34:00' , '12' , 6 , '5175296' );
Driver error was [2/145]:
QMYSQL3: Unable to execute query
Database error was:
Table './mythconverg/recordedseek' is marked as crashed and should be repaired

2007-10-29 21:34:25.438 DB Error (delta position map insert):
Query was:
INSERT INTO recordedseek (chanid, starttime, mark, type, offset) VALUES ( '1003' , '2007-10-29T21:34:00' , '13' , 6 , '5496832' );
Driver error was [2/145]:
QMYSQL3: Unable to execute query
Database error was:
Table './mythconverg/recordedseek' is marked as crashed and should be repaired

```
Looks like you've still got some broken tables.

---

### Post by dualboot on 2008-06-25
I hit this same problem, and followed the advice here without resolution (though it was nice to know I wasn't the only one :)

Found a link on mythtvtalk forum which did sort me out suggested using myisamchk on the mysql databases.



Re producing it here (I hope this doesn't break any rules) incase it speeds someone else's research, but the original link is [here]("http://www.mythtvtalk.com/forum/archive/o_t/t_6009/start_10/index.html")




[FONT="Times New Roman"][COLOR="Navy"]I finally figuered it out. I found a log in /var/log/mythtv on my server that said this:

QMYSQL3: Unable to execute query
Database error was:
Table './mythconverg/recordedprogram' is marked as crashed and should be repaired

AHA!

So I then did this after becoming root

Code:
cd /var/lib/mysql/mythconverg
/etc/init.d/mythtv-backend stop
myisamchk *.MYI


I scrolled up and it confirmed the table was corrupted

MyISAM-table 'recordedprogram.MYI' is corrupted
Fix it using switch "-r" or "-o"

I then did this:

Code:
root@Riesling:/var/lib/mysql# myisamchk -r recordedprogram.MYI


That fixed my table and everything is 100% now. Thanks everyone for your input.[/COLOR][/FONT]

---

