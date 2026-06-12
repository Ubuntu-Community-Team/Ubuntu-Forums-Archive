---
title: "Seemingly Random UserJob Transcoding"
date: 2008-08-26
forum: Mythbuntu
---

### Post by thatkidandy on 2008-08-26
Weird problem/inconvenience I could use a lil' help with: every once in a while, random shows that I watch live (NOT specified to record or transcode) will be run through one of my userjobs to transcode to ipod format. Can't seem to track down the trigger.

Suggestions where to start?
Here are the surrounding logs around one such incident with the closing ceremonies...

```

2008-08-24 21:30:02.155 Started recording: American Dad "Of Ice & Men": channel 1026 on cardid 1, sourceid 1
2008-08-24 21:30:02.169 TVRec(1): HW Tuner: 1->1
2008-08-24 21:30:02.426 Finished recording XXIX Summer Olympics "Volleyball, Closing Ceremony": channel 1005
2008-08-24 21:30:03.554 Finished recording XXIX Summer Olympics "Volleyball, Closing Ceremony": channel 1005
2008-08-24 21:30:03.602 TVRec(1): RingBufferChanged()
2008-08-24 21:30:03.611 Finished recording XXIX Summer Olympics "Volleyball, Closing Ceremony": channel 1005
2008-08-24 21:30:03.736 AutoExpire: CalcParams(): Max required Free Space: 2.0 GB w/freq: 15 min
2008-08-24 21:30:03.913 Using runtime prefix = /usr, libdir = /usr/lib
2008-08-24 21:30:06.421 AFD: Opened codec 0x829ee20, id(MPEG2VIDEO) type(Video)
2008-08-24 21:30:06.425 AFD: codec MP2 has 2 channels
2008-08-24 21:30:06.426 AFD: Opened codec 0x829f2a0, id(MP2) type(Audio)
2008-08-24 21:30:06.508 Preview: Grabbed preview '/media/storage/recordings/1005_20080824211159.mpg' 480x480@84s
2008-08-24 21:30:07.261 JobQueue: Commercial Flagging Starting for XXIX Summer Olympics "Volleyball, Closing Ceremony" recorded from channel 1005 at Sun Aug 24 21:11:59 2008
2008-08-24 21:30:07.491 Using runtime prefix = /usr, libdir = /usr/lib
2008-08-24 21:30:10.073 AFD: Opened codec 0x81fff80, id(MPEG2VIDEO) type(Video)
2008-08-24 21:30:10.078 AFD: codec MP2 has 2 channels
2008-08-24 21:30:10.079 AFD: Opened codec 0x8200400, id(MP2) type(Audio)
2008-08-24 21:36:04.956 AutoExpire: CalcParams(): Max required Free Space: 2.0 GB w/freq: 15 min
2008-08-24 21:38:14.197 [mpeg2video @ 0xb73cdb88]ac-tex damaged at 5 9
2008-08-24 21:38:14.199 [mpeg2video @ 0xb73cdb88]Warning MVs not available
2008-08-24 21:38:14.659 Using runtime prefix = /usr, libdir = /usr/lib
2008-08-24 21:38:17.157 AFD: Opened codec 0x829ee50, id(MPEG2VIDEO) type(Video)
2008-08-24 21:38:17.159 AFD: codec MP2 has 2 channels
2008-08-24 21:38:17.159 AFD: Opened codec 0x829f2d0, id(MP2) type(Audio)
2008-08-24 21:38:17.233 Preview: Grabbed preview '/media/storage/recordings/1005_20080824211159.mpg' 480x480@84s
2008-08-24 21:39:12.319 JobQueue: Started "Export to Stream (Low)" for "XXIX Summer Olympics" recorded from channel 1005 at Sun Aug 24 21:11:59 2008

```

---

