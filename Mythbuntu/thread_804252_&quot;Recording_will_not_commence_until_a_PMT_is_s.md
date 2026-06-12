---
title: "&quot;Recording will not commence until a PMT is set&quot;"
date: 2008-05-22
forum: Mythbuntu
---

### Post by larsolav on 2008-05-22
Good evening!
My wife was excited to watch the first episodes of this years "So you think you can dance", but when she selected it, a black little box popped up saying "The file for this recording is empty".

The mythbackend.log says this:
> 2008-05-22 18:23:19.490 mythfilldatabase run complete.
2008-05-22 18:23:19.543 DataDirect: Deleting temporary files
2008-05-22 18:23:20.091 Scheduled 78 items in 0.6 = 0.11 match + 0.51 place
2008-05-22 18:25:14.569 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-05-22 18:40:14.692 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-05-22 18:55:14.806 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-05-22 18:58:00.236 Reschedule requested for id 0.
2008-05-22 18:58:00.565 Scheduled 78 items in 0.3 = 0.00 match + 0.32 place
2008-05-22 18:58:29.821 TVRec(1): ASK_RECORDING 1 29 0 0
2008-05-22 18:59:02.736 TVRec(1): Changing from None to RecordingOnly
2008-05-22 18:59:02.757 TVRec(1): HW Tuner: 1->1
2008-05-22 18:59:02.832 AutoExpire: CalcParams(): Max required Free Space: 3.0 GB w/freq: 15 min
2008-05-22 18:59:02.870 Started recording: So You Think You Can Dance: channel 1261 on cardid 1, sourceid 1
2008-05-22 18:59:03.493 [COLOR="Red"]Could not find channel 26_1 in TVCT[/COLOR]
2008-05-22 18:59:03.505 
VCT Terra: channels(3) tsid(0xb2d) seclength(160)
Channel #0 name(KUHT-HD) 8-1 mod(ATSC 8-VSB) cTSID(0xb2d)
 pnum(1) ETM_loc(1) access_ctrl(0) hidden(0) hide_guide(1) service_type(2) source_id(1)
 descriptors length(17) count(1)
  Service Location Descriptor (0xa1) length(15)

Channel #1 name(KUHT-SD) 8-2 mod(ATSC 8-VSB) cTSID(0xb2d)
 pnum(2) ETM_loc(1) access_ctrl(0) hidden(0) hide_guide(1) service_type(2) source_id(2)
 descriptors length(17) count(1)
  Service Location Descriptor (0xa1) length(15)

Channel #2 name(KUHTSD2) 8-3 mod(ATSC 8-VSB) cTSID(0xb2d)
 pnum(3) ETM_loc(1) access_ctrl(0) hidden(0) hide_guide(1) service_type(2) source_id(3)
 descriptors length(17) count(1)
  Service Location Descriptor (0xa1) length(15)


2008-05-22 18:59:03.550 DTVSM(0) [COLOR="Red"]Error: Wrong PMT;[/COLOR] pmt->pn(1) desired(3)
2008-05-22 18:59:03.626 DVBRec(1:0) [COLOR="Red"]Warning: Recording will not commence until a PMT is set.[/COLOR]
2008-05-22 18:59:03.684 DVBRec(1:0) Warning: Recording will not commence until a PMT is set.

[[Many many more lines like this until:]]


2008-05-22 21:06:00.794 DVBRec(1:0) Warning: Recording will not commence until a PMT is set.
2008-05-22 21:06:00.823 TVRec(1): Changing from RecordingOnly to None
2008-05-22 21:06:00.850 DVBRec(1:0) Warning: Recording will not commence until a PMT is set.
2008-05-22 21:06:00.864 Finished recording So You Think You Can Dance: channel 1261
2008-05-22 21:06:00.906 Reschedule requested for id 0.
2008-05-22 21:06:00.916 DVBRec(1:0) Warning: Recording will not commence until a PMT is set.
2008-05-22 21:06:01.139 Finished recording So You Think You Can Dance: channel 1261
2008-05-22 21:06:01.717 Scheduled 77 items in 0.8 = 0.00 match + 0.80 place
2008-05-22 21:06:01.936 Using runtime prefix = /usr, libdir = /usr/lib
2008-05-22 21:06:01.958 Empty LocalHostName.
2008-05-22 21:06:01.959 Using localhost value of MythBox1
2008-05-22 21:06:02.047 New DB connection, total: 1
2008-05-22 21:06:02.073 Connected to database 'mythconverg' at host: localhost
2008-05-22 21:06:02.075 Closing DB connection named 'DBManager0'
2008-05-22 21:06:02.077 Connected to database 'mythconverg' at host: localhost
2008-05-22 21:06:02.079 New DB connection, total: 2
2008-05-22 21:06:02.079 Connected to database 'mythconverg' at host: localhost
2008-05-22 21:06:02.113 Current Schema Version: 1214
2008-05-22 21:06:02.153 Preview Error: Previewer file '/var/lib/mythtv/recordings/1261_20080522185900.mpg' is not valid.
2008-05-22 21:06:02.159 Preview Error: Run() file not local: '/var/lib/mythtv/recordings/1261_20080522185900.mpg'
2008-05-22 21:06:02.299 Preview Error: Preview process not ok.
			fileinfo(/var/lib/mythtv/recordings/1261_20080522185900.mpg.png) exists: 0 readable: 0 size: 0
2008-05-22 21:10:16.338 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min



The local Fox affiliate is on channel 26. 

What does the "Error: Wrong PMT" message mean? and how can I set PMT?

My system (if at all relevant):
Foxconn 955X7AA motherboard, Intel Pentium D 820 Smithfield 2.8GHz CPU, 1 GB RAM, 1.2 TB LVM var/lib, 2 AirStar-HD5000-PCI tuners, eVGA GeForce 7300GS GPU, Streamzap PC remote control

Mythtv version info:
> ~$ apt-cache policy mythtv-common
mythtv-common:
  Installed: 0.21.0-0ubuntu2~gutsy1
  Candidate: 0.21.0-0ubuntu2~gutsy1
  Version table:
 *** 0.21.0-0ubuntu2~gutsy1 0
        500 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports/multiverse Packages
        100 /var/lib/dpkg/status
     0.20.2-0ubuntu10.1 0
        500 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/multiverse Packages
     0.20.2-0ubuntu10 0
        500 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/multiverse Packages


Thanks for any help! The wife was a bit bummed out that her show didn't record...

Cheers!

---

### Post by solitaire on 2008-05-22
Can't help you but the's a joke about PMT and an upset wife just begging to be told....:lolflag::lolflag:


Just a longshot..
Also could PMT be the region; Mountain time? check to see what your date / time settings are to..

---

### Post by larsolav on 2008-05-23
:lolflag: :biggrin: :lolflag:

My box is set to central time.
It also recorded a children's program on the local PBS channel (channel 8 ) this morning, and I was able to view that just fine. I have set the box to record a show on the Fox affiliate (channel 26) to see if it is something with the channel, but won't be able to check until after work. However, this morning Live TV on channel 26 worked just fine.

I am very puzzled as to why this PMT stuff happened. 

Cheers!

---

### Post by larsolav on 2008-05-23
After some more searching I found out what PMT is:  [http://en.wikipedia.org/wiki/Transport_stream#PMT](http://en.wikipedia.org/wiki/Transport_stream#PMT) :
> PMT

Program Map Tables, or PMTs, contain information about programs. For each program, there is a PMT, with the PMT for each program appearing on its own PID. The PMTs describe which PIDs contain data relevant to the program. PMTs also provide metadata about the streams in their constituent PIDs. For example, if a program contains an MPEG-2 video stream, the PMT will list this PID, describe it as a video stream, and provide the type of video that it contains (in this case, MPEG-2). The PMT may also contain additional descriptors providing data about its constituent streams.

Also, it contains a &#8220;special&#8221; PMT (with the program_number (field in the PMT) equal to 0) which is the NIT PID on the TS. This &#8220;special PMT&#8221; is optional. But the NIT is not. So we can not find a NIT PID in the PAT, we MUST use the default value for the NIT PID.

Also, bug #229797 reported on 2008-05-13 discloses the same error message, "Recording will not commence until a PMT is set."  [https://bugs.launchpad.net/ubuntu/+source/mythtv/+bug/229797](https://bugs.launchpad.net/ubuntu/+source/mythtv/+bug/229797)

An older bug (16-13 months ago) is at [http://svn.mythtv.org/trac/ticket/3031](http://svn.mythtv.org/trac/ticket/3031) .

Any one know why my wife's show didn't record?

---

### Post by larsolav on 2008-05-23
So I got home, and this mornings recording on channel 26 worked just fine. We have recorded several programs on this channel before without problems. I think something like this has happened a couple times before on this and an other channel. The funny thing is that the frontend showed that "so you think ..." was recording (it was in green text in the recorded list). So the frontend had no clue the backend wasn't recording. It would have been nice if the backend could communicate to the frontend that it wasn't recording so that I maybe could have restarted the recording or something like that...

---

### Post by larsolav on 2008-06-07
It happened again. The same channel, the same show! I have recorded several episodes of "so you think you can dance" since the first incident, and thought it was just a weird one-time quirk. It happened again on Thursday. My user-group was not happy, to say the least.

Backend log:
> 2008-06-05 18:54:58.542 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-06-05 18:58:00.180 Reschedule requested for id 0.
2008-06-05 18:58:00.654 Scheduled 78 items in 0.5 = 0.00 match + 0.47 place
2008-06-05 18:58:30.130 TVRec(1): ASK_RECORDING 1 29 0 0
2008-06-05 18:59:02.770 TVRec(1): Changing from None to RecordingOnly
2008-06-05 18:59:02.773 TVRec(1): HW Tuner: 1->1
2008-06-05 18:59:02.809 AutoExpire: CalcParams(): Max required Free Space: 3.0 GB w/freq: 15 min
2008-06-05 18:59:02.816 Started recording: So You Think You Can Dance: channel 1261 on cardid 1, sourceid 1
2008-06-05 18:59:03.327 DTVSM(0) Error: Wrong PMT; pmt->pn(1) desired(3)
2008-06-05 18:59:03.336 Could not find channel 26_1 in TVCT
2008-06-05 18:59:03.338 
VCT Terra: channels(3) tsid(0xb2d) seclength(160)
Channel #0 name(KUHT-HD) 8-1 mod(ATSC 8-VSB) cTSID(0xb2d)
 pnum(1) ETM_loc(1) access_ctrl(0) hidden(0) hide_guide(1) service_type(2) source_id(1)
 descriptors length(17) count(1)
  Service Location Descriptor (0xa1) length(15)

Channel #1 name(KUHT-SD) 8-2 mod(ATSC 8-VSB) cTSID(0xb2d)
 pnum(2) ETM_loc(1) access_ctrl(0) hidden(0) hide_guide(1) service_type(2) source_id(2)
 descriptors length(17) count(1)
  Service Location Descriptor (0xa1) length(15)

Channel #2 name(KUHTSD2) 8-3 mod(ATSC 8-VSB) cTSID(0xb2d)
 pnum(3) ETM_loc(1) access_ctrl(0) hidden(0) hide_guide(1) service_type(2) source_id(3)
 descriptors length(17) count(1)
  Service Location Descriptor (0xa1) length(15)


2008-06-05 18:59:03.372 Could not find channel 26_1 in TVCT
2008-06-05 18:59:03.373 
VCT Terra: channels(3) tsid(0xb2d) seclength(160)
Channel #0 name(KUHT-HD) 8-1 mod(ATSC 8-VSB) cTSID(0xb2d)
 pnum(1) ETM_loc(1) access_ctrl(0) hidden(0) hide_guide(1) service_type(2) source_id(1)
 descriptors length(17) count(1)
  Service Location Descriptor (0xa1) length(15)

Channel #1 name(KUHT-SD) 8-2 mod(ATSC 8-VSB) cTSID(0xb2d)
 pnum(2) ETM_loc(1) access_ctrl(0) hidden(0) hide_guide(1) service_type(2) source_id(2)
 descriptors length(17) count(1)
  Service Location Descriptor (0xa1) length(15)

Channel #2 name(KUHTSD2) 8-3 mod(ATSC 8-VSB) cTSID(0xb2d)
 pnum(3) ETM_loc(1) access_ctrl(0) hidden(0) hide_guide(1) service_type(2) source_id(3)
 descriptors length(17) count(1)
  Service Location Descriptor (0xa1) length(15)


2008-06-05 18:59:03.453 DVBRec(1:0) Warning: Recording will not commence until a PMT is set.
2008-06-05 18:59:03.510 DVBRec(1:0) Warning: Recording will not commence until a PMT is set.
2008-06-05 18:59:03.566 DVBRec(1:0) Warning: Recording will not commence until a PMT is set.
2008-06-05 18:59:03.622 DVBRec(1:0) Warning: Recording will not commence until a PMT is set.
2008-06-05 18:59:03.678 DVBRec(1:0) Warning: Recording will not commence until a PMT is set.
2008-06-05 18:59:03.734 DVBRec(1:0) Warning: Recording will not commence until a PMT is set.
2008-06-05 18:59:03.790 DVBRec(1:0) Warning: Recording will not commence until a PMT is set.
2008-06-05 18:59:03.847 DVBRec(1:0) Warning: Recording will not commence until a PMT is set.
2008-06-05 18:59:03.905 DVBRec(1:0) Warning: Recording will not commence until a PMT is set.
2008-06-05 18:59:03.961 DVBRec(1:0) Warning: Recording will not commence until a PMT is set.
2008-06-05 18:59:04.017 DVBRec(1:0) Warning: Recording will not commence until a PMT is set.
2008-06-05 18:59:04.073 DVBRec(1:0) Warning: Recording will not commence until a PMT is set.
2008-06-05 18:59:04.129 DVBRec(1:0) Warning: Recording will not commence until a PMT is set.
2008-06-05 18:59:04.184 DVBRec(1:0) Warning: Recording will not commence until a PMT is set

...

2008-06-05 18:59:19.637 DVBRec(1:0) Warning: Recording will not commence until a PMT is set.
2008-06-05 18:59:19.640 RingBuf(/var/lib/mythtv/recordings/1261_20080605185900.mpg): Invalid file (fd -1) when opening '/var/lib/mythtv/recordings/1261_20080605185900.mpg'.
2008-06-05 18:59:19.692 Connecting to backend server: 127.0.0.1:6543 (try 1 of 5)
2008-06-05 18:59:19.693 DVBRec(1:0) Warning: Recording will not commence until a PMT is set.
2008-06-05 18:59:19.694 Using protocol version 40
2008-06-05 18:59:19.699 MainServer::HandleAnnounce Monitor
2008-06-05 18:59:19.704 adding: MythBox1 as a client (events: 0)
2008-06-05 18:59:19.705 MainServer::HandleAnnounce Monitor
2008-06-05 18:59:19.705 adding: MythBox1 as a client (events: 1)
2008-06-05 18:59:19.750 DVBRec(1:0) Warning: Recording will not commence until a PMT is set.

....

2008-06-05 18:59:31.702 DVBRec(1:0) Warning: Recording will not commence until a PMT is set.
2008-06-05 18:59:31.728 NVP::OpenFile(): Error, file not found: /var/lib/mythtv/recordings/1261_20080605185900.mpg
2008-06-05 18:59:31.758 DVBRec(1:0) Warning: Recording will not commence until a PMT is set.
2008-06-05 18:59:31.830 DVBRec(1:0) Warning: Recording will not commence until a PMT is set.
2008-06-05 18:59:31.949 DVBRec(1:0) Warning: Recording will not commence until a PMT is set.
2008-06-05 18:59:32.007 DVBRec(1:0) Warning: Recording will not commence until a PMT is set.
2008-06-05 18:59:32.063 DVBRec(1:0) Warning: Recording will not commence until a PMT is set.
2008-06-05 18:59:32.092 Using runtime prefix = /usr, libdir = /usr/lib
2008-06-05 18:59:32.100 Empty LocalHostName.
2008-06-05 18:59:32.101 Using localhost value of MythBox1
2008-06-05 18:59:32.114 New DB connection, total: 1
2008-06-05 18:59:32.119 DVBRec(1:0) Warning: Recording will not commence until a PMT is set.
2008-06-05 18:59:32.126 Connected to database 'mythconverg' at host: localhost
2008-06-05 18:59:32.128 Closing DB connection named 'DBManager0'
2008-06-05 18:59:32.129 Connected to database 'mythconverg' at host: localhost
2008-06-05 18:59:32.131 New DB connection, total: 2
2008-06-05 18:59:32.132 Connected to database 'mythconverg' at host: localhost
2008-06-05 18:59:32.135 Current Schema Version: 1214
2008-06-05 18:59:32.165 Preview Error: Previewer file '/var/lib/mythtv/recordings/1261_20080605185900.mpg' is not valid.
2008-06-05 18:59:32.168 Preview Error: Run() file not local: '/var/lib/mythtv/recordings/1261_20080605185900.mpg'
2008-06-05 18:59:32.176 Preview Error: Preview process not ok.
			fileinfo(/var/lib/mythtv/recordings/1261_20080605185900.mpg.png) exists: 0 readable: 0 size: 0
2008-06-05 18:59:32.178 DVBRec(1:0) Warning: Recording will not commence until a PMT is set.

...

2008-06-05 21:06:00.738 DVBRec(1:0) Warning: Recording will not commence until a PMT is set.
2008-06-05 21:06:00.794 DVBRec(1:0) Warning: Recording will not commence until a PMT is set.
2008-06-05 21:06:00.850 DVBRec(1:0) Warning: Recording will not commence until a PMT is set.
2008-06-05 21:06:00.906 DVBRec(1:0) Warning: Recording will not commence until a PMT is set.
2008-06-05 21:06:00.918 TVRec(1): Changing from RecordingOnly to None
2008-06-05 21:06:00.954 Finished recording So You Think You Can Dance: channel 1261
2008-06-05 21:06:00.961 DVBRec(1:0) Warning: Recording will not commence until a PMT is set.
2008-06-05 21:06:00.986 Reschedule requested for id 0.
2008-06-05 21:06:01.040 Finished recording So You Think You Can Dance: channel 1261
2008-06-05 21:06:02.195 Scheduled 77 items in 1.2 = 0.03 match + 1.17 place
2008-06-05 21:06:02.346 Using runtime prefix = /usr, libdir = /usr/lib
2008-06-05 21:06:02.417 Empty LocalHostName.
2008-06-05 21:06:02.421 Using localhost value of MythBox1
2008-06-05 21:06:02.493 New DB connection, total: 1
2008-06-05 21:06:02.520 Connected to database 'mythconverg' at host: localhost
2008-06-05 21:06:02.523 Closing DB connection named 'DBManager0'
2008-06-05 21:06:02.524 Connected to database 'mythconverg' at host: localhost
2008-06-05 21:06:02.527 New DB connection, total: 2
2008-06-05 21:06:02.529 Connected to database 'mythconverg' at host: localhost
2008-06-05 21:06:02.559 Current Schema Version: 1214
2008-06-05 21:06:02.590 Preview Error: Previewer file '/var/lib/mythtv/recordings/1261_20080605185900.mpg' is not valid.
2008-06-05 21:06:02.592 Preview Error: Run() file not local: '/var/lib/mythtv/recordings/1261_20080605185900.mpg'
2008-06-05 21:06:02.757 Preview Error: Preview process not ok.


Any one have any idea what the heck is going on?
Did my local PBS stations (8_1, 8_2, and 8_3) hijack my tuners or something? the last thing recorded before this were some kids PBS shows.

Anybody know what is going on?

It would be nice if the frontend could ping a message that a recording was not being recorded. Who checks the backend logs when things seem to go OK? Now I will have to check the backend log everytime the show is supposed to record, just to make sure it is recording...

---

### Post by edvale on 2008-07-03
Same problem for me as well.  Never saw this issue before upgrading to 8.04.  Current running mythtv-backend version "0.21.0+fixes16838-0ubuntu3.1".

[...]
2008-07-03 16:00:02.685 TVRec(3): Changing from None to RecordingOnly
2008-07-03 16:00:02.707 TVRec(3): HW Tuner: 3->3
2008-07-03 16:00:02.989 AutoExpire: CalcParams(): Max required Free Space: 3.0 GB w/freq: 15 min
2008-07-03 16:00:02.994 Started recording: Oprah Winfrey: channel 1091 on cardid 3, sourceid 1
2008-07-03 16:00:04.562 Could not find channel 9_1 in TVCT
2008-07-03 16:00:04.568
VCT Terra: channels(2) tsid(0x851) seclength(111)
Channel #0 name(WGRZ-HD) 2-1 mod(ATSC 8-VSB) cTSID(0x851)
 pnum(1) ETM_loc(0) access_ctrl(0) hidden(0) hide_guide(1) service_type(2) source_id(1)
 descriptors length(17) count(1)
  Service Location Descriptor (0xa1) length(15)

Channel #1 name(WGRZ-SD) 2-2 mod(ATSC 8-VSB) cTSID(0x851)
 pnum(2) ETM_loc(0) access_ctrl(0) hidden(0) hide_guide(1) service_type(2) source_id(2)
 descriptors length(17) count(1)
  Service Location Descriptor (0xa1) length(15)


2008-07-03 16:00:04.592 Program #4 not found in PAT!
Program Association Table
 PSIP tableID(0x0) length(17) extension(0x851)
      version(7) current(1) section(0) last_section(0)
         tsid: 2129
 programCount: 2
  program number     1 has PID 0x  30   data  0x 0 0x 1 0xe0 0x30
  program number     2 has PID 0x  40   data  0x 0 0x 2 0xe0 0x40

2008-07-03 16:00:04.721 DVBRec(3:0) Warning: Recording will not commence until a PMT is set.
2008-07-03 16:00:04.778 DVBRec(3:0) Warning: Recording will not commence until a PMT is set.
2008-07-03 16:00:04.834 DVBRec(3:0) Warning: Recording will not commence until a PMT is set.
2008-07-03 16:00:04.889 DVBRec(3:0) Warning: Recording will not commence until a PMT is set.
[...]

---

### Post by frankO on 2010-02-04
Hi. I had the problem of wrong PMT set. This seemed to happen because of confusion in the mysql database.
The easiest solution is to go into the channel editor and delete all your channels.
Then go into input connections and delete all your inputs.
Then go into video sources and delete your video sources.

Then reverse your steps adding back your video sources, input connections and channels.

---

### Post by ian dobson on 2010-02-04
Hi,

PMT is part of the DVB standard, so just rescan you channels. It sounds as if there's some information missing in the database for the dvb-multiplex.

If the worst comes to the worst just delete all your channels and recreate them.

Regards
Ian Dobson

---

### Post by nickrout on 2010-02-04
More info:

> PMT

Program Map Tables (PMTs) contain information about programs. For each program, there is one PMT. While the MPEG-2 standard permits more than one PMT section to be transmitted on a single PID, most MPEG-2 "users" such as ATSC and SCTE require each PMT to be transmitted on a separate PID that is not used for any other packets. The PMTs provide information on each program present in the transport stream, including the program_number, and list the elementary streams that comprise the described MPEG-2 program. There are also locations for optional descriptors that describe the entire MPEG-2 program, as well as an optional descriptor for each elementary stream. Each elementary stream is labeled with a stream_type value.

[http://en.wikipedia.org/wiki/MPEG_transport_stream#PMT](http://en.wikipedia.org/wiki/MPEG_transport_stream#PMT)

I think rescan is the right answer!

---

### Post by larsolav on 2010-02-04
Honestly, I'm not so sure a rescan would do the trick, at least in my situation... Because without a rescan, would not the same channel never work once it happened? Also, after building a new system when 9.10 came out and setting it up from scratch (including a fresh scan of the channels) I had the same problem pretty quickly. I posted about it here: [http://ubuntuforums.org/showthread.php?t=1350474](http://ubuntuforums.org/showthread.php?t=1350474)

Hopefully the rescan works just fine for frankO, but if doesn't work give the script in the post I mention above a try. I haven't had the problem again since...

---

### Post by 4dognight on 2010-02-04
I had this problem too. It would always fail on one specific channel(9). I checked the 'quicktune ' setting to 'always' in the config, and it resolved the problem.

---

