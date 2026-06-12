---
title: "Error when transcoding"
date: 2010-06-12
forum: Mythbuntu
---

### Post by NautiusMaximus on 2010-06-12
I can normally transcode recordings (to edit out the adverts), but I have tried to transcode one today which has failed.

It first failed with error 232, and after a little Googling I discovered that this is apparently a known bug, for which a workaround is described [here]("http://www.mythtv.org/wiki/Mythtranscode#Fixing_.22Deadlock_detected.__One_buffer_is_full_when_the_other_is_empty.21.22").

I tried the workaround, and now I get a different error, No 247. I'm at a loss to know what could be wrong here. Here is the relevant bit of the backend log:


```
2010-06-12 12:49:51.881 Transcoding from /var/lib/mythtv/recordings/1002_20100606220000.mpg to /var/lib/mythtv/recordings/1002_20100606220000.mpg.tmp
2010-06-12 12:49:52.000 MythContext: Connecting to backend server: 172.16.100.20:6543 (try 1 of 1)
2010-06-12 12:49:52.067 Using protocol version 50
2010-06-12 12:49:52.120 MainServer::ANN Monitor
2010-06-12 12:49:52.176 adding: htpc as a client (events: 0)
2010-06-12 12:49:52.232 MainServer::ANN Monitor
2010-06-12 12:49:52.298 adding: htpc as a client (events: 1)
2010-06-12 12:49:54.789 AFD: codec MP2 has 2 channels
2010-06-12 12:49:54.843 AFD: Opened codec 0x1376a80, id(MP2) type(Audio)
2010-06-12 12:49:54.901 AFD: Opened codec 0x13737d0, id(MPEG2VIDEO) type(Video)
2010-06-12 12:49:54.996 Honoring the cutlist while transcoding
2010-06-12 12:49:55.044 Cutlist        : 0-3031,172073-179877
2010-06-12 12:49:55.099 Original Length: 179877 frames
2010-06-12 12:49:55.154 New Length     : 169042 frames
2010-06-12 12:49:55.213 Transcode: Looking for autodetect profile: Autodetect from 576i
2010-06-12 12:49:55.267 New DB connection, total: 3
2010-06-12 12:49:55.322 Connected to database 'mythconverg' at host: localhost
2010-06-12 12:49:55.409 SampleRate: Attempted to add a rate 32000 Hz, which is not in the list of allowed rates.
2010-06-12 12:49:55.481 Transcode: Using autodetect profile: MPEG2
2010-06-12 12:49:55.533 Switching to MPEG-2 transcoder.
2010-06-12 12:49:55.598 Opening /var/lib/mythtv/recordings/1002_20100606220000.mpg
2010-06-12 12:49:55.659 Input #0, mpeg, from '/var/lib/mythtv/recordings/1002_20100606220000.mpg':
2010-06-12 12:49:55.712   Duration: 01:59:55.88, start: 0.500000, bitrate: 2919 kb/s
2010-06-12 12:49:55.789     Stream #0.0[0x1c0]: Audio: mp2, 48000 Hz, 2 channels, s16, 256 kb/s
2010-06-12 12:49:55.867     Stream #0.1[0x1e0]: Video: mpeg2video, yuv420p, 720x576 [PAR 64:45 DAR 16:9], 15000 kb/s, 25 tbr, 90k tbn, 50 tbc
2010-06-12 12:49:56.001 #1 PTS:00:00:00.944 Delta: 0.0ms queue: 15
2010-06-12 12:49:56.090 #0 PTS:00:00:00.932 Delta: 12.8667ms queue: 2
2010-06-12 12:49:57.560 Converting frame #3 from B to I 
2010-06-12 12:49:57.652 Converting frame #4 from B to I 
2010-06-12 12:49:57.727 Converting frame #5 from P to I 
Mux rate: 15.51 Mbit/s
2010-06-12 12:50:32.118 Converting frame #0 from B to I 
2010-06-12 12:50:32.262 Converting frame #1 from B to I 
2010-06-12 12:50:32.355 Inserting 2 I-Frames after #11 
2010-06-12 12:50:32.405 Generating Keyframe Index
2010-06-12 12:50:32.459 Opening /var/lib/mythtv/recordings/1002_20100606220000.mpg.tmp
2010-06-12 12:50:32.504 Couldn't open input file, error #-84
2010-06-12 12:50:32.564 Transcoding /var/lib/mythtv/recordings/1002_20100606220000.mpg failed
2010-06-12 12:50:32.605 Deleting /var/lib/mythtv/recordings/1002_20100606220000.mpg.tmp
2010-06-12 12:50:32.650 Error Truncating '/var/lib/mythtv/recordings/1002_20100606220000.mpg.tmp' could not determine size of the file, unlinking immediately.
2010-06-12 12:50:32.707 JobQueue: Transcode Errored: Michael Clayton: Autodetect (exit status 247, job status was "Errored")

```

Any idea what could be going on? The bit that says "Couldn't open input file" made me wonder if it could be a permissions thing. However, after creating the new .mpg file with the workaround I described above, I did chown the owner of the file to mythtv, which should mean that the permissions are correct, right? Or am I overlooking something?

I'm using Mythbuntu 9.10.

Thanks
NM

---

### Post by NautiusMaximus on 2010-06-17
Bump

---

### Post by joshoekstra on 2010-06-17
[transcode error]("http://www.mythtv.org/wiki/Removing_Commercials#Transcode_error_-_Transcode_failed_with_status:_247") doesn't provide any insight?
Your logs seem to indicate that some sample rate is outside allowance and that 'yourrecording.mpg.tmp' cannot be opened. Try a manual profile instead of this one or see if the info from the wiki helps.

I always used a 'manual' profile because of the hassle of the auto-detect....

---

