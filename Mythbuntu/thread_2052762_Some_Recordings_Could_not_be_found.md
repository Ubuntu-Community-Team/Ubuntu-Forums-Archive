---
title: "Some Recordings Could not be found"
date: 2012-09-03
forum: Mythbuntu
---

### Post by grygub on 2012-09-03
I have recently done a fresh install and a database restore. All my old recordings work fine. Of my new recordings off the same tuner some work fine and some say that they can not be found. Here is my mythtv backend log when it is attempting to make a recording that did not work.

```
Sep  1 20:59:30 myth-server mythbackend[2101]: E Scheduler storagegroup.cpp:184 (Init) SG(Default): Unable to find any Storage Group Directories.  Using hardcoded default value of '/mnt/store'
Sep  1 20:59:30 myth-server mythbackend[2101]: I TVRecEvent tv_rec.cpp:1536 (HandlePendingRecordings) TVRec(15): ASK_RECORDING 15 20 0 0
Sep  1 20:59:52 myth-server mythbackend[2101]: I CoreContext mythdbcon.cpp:395 (PurgeIdleConnections) New DB connection, total: 11
Sep  1 20:59:52 myth-server mythbackend[2101]: I TVRecEvent tv_rec.cpp:1029 (HandleStateChange) TVRec(15): Changing from None to RecordingOnly
Sep  1 20:59:52 myth-server mythbackend[2101]: I TVRecEvent mythdbcon.cpp:395 (PurgeIdleConnections) New DB connection, total: 11
Sep  1 20:59:52 myth-server mythbackend[2101]: I TVRecEvent tv_rec.cpp:3495 (TuningCheckForHWChange) TVRec(15): HW Tuner: 15->15
Sep  1 20:59:52 myth-server mythbackend[2101]: I TVRecEvent v4lchannel.cpp:661 (SetInputAndFormat) V4LChannel(/dev/video0): SetInputAndFormat(7, NTSC) (v4l v2) input_switch: 0 mode_switch: 0
Sep  1 20:59:52 myth-server mythbackend[2101]: N Scheduler autoexpire.cpp:263 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 3.0 GB w/freq: 15 min
Sep  1 20:59:52 myth-server mythbackend[2101]: I Scheduler scheduler.cpp:2514 (HandleRecordingStatusChange) Tuning recording: "Gold Rush":"The Jungle": channel 5197 on cardid 15, sourceid 3
Sep  1 20:59:52 myth-server mythbackend[2101]: I Scheduler mythdbcon.cpp:237 (Reconnect) MySQL reconnected successfully
Sep  1 20:59:55 myth-server mythbackend[2101]: I CoreContext scheduler.cpp:637 (UpdateRecStatus) Updating status for "Gold Rush":"The Jungle" on cardid 15 (Tuning => Recording)
Sep  1 20:59:55 myth-server mythbackend[2101]: I TVRecEvent tv_rec.cpp:3989 (TuningNewRecorder) TVRec(15): rec->GetPathname(): '/mnt/store/5197_20120901210000.mpg'
Sep  1 20:59:55 myth-server mythbackend[2101]: E TVRecEvent ThreadedFileWriter.cpp:119 (Open) TFW(/mnt/store/5197_20120901210000.mpg:-1): Opening file '/mnt/store/5197_20120901210000.mpg'.#012#011#011#011eno: No such file or directory (2)
Sep  1 20:59:55 myth-server mythbackend[2101]: E TVRecEvent tv_rec.cpp:3995 (TuningNewRecorder) TVRec(15): RingBuffer '/mnt/store/5197_20120901210000.mpg' not open...
Sep  1 20:59:55 myth-server mythbackend[2101]: I TVRecEvent tv_rec.cpp:1029 (HandleStateChange) TVRec(15): Changing from RecordingOnly to None
Sep  1 21:00:10 myth-server mythbackend[2101]: E JobQueue storagegroup.cpp:184 (Init) SG(Default): Unable to find any Storage Group Directories.  Using hardcoded default value of '/mnt/store'
Sep  1 21:00:10 myth-server mythbackend[2101]: E JobQueue programinfo.cpp:2278 (GetPlaybackURL) ProgramInfo(5197_20120901210000.mpg): GetPlaybackURL: '5197_20120901210000.mpg' should be local, but it can not be found.
Sep  1 21:00:10 myth-server mythbackend[2101]: E JobQueue storagegroup.cpp:184 (Init) SG(Default): Unable to find any Storage Group Directories.  Using hardcoded default value of '/mnt/store'
Sep  1 21:00:10 myth-server mythbackend[2101]: E JobQueue programinfo.cpp:2278 (GetPlaybackURL) ProgramInfo(5197_20120901210000.mpg): GetPlaybackURL: '5197_20120901210000.mpg' should be local, but it can not be found.
Sep  1 21:00:10 myth-server mythbackend[2101]: I Commflag_1631 jobqueue.cpp:2276 (DoFlagCommercialsThread) JobQueue: Commercial Detection Starting for "Gold Rush":"The Jungle" recorded from channel 5197 at 2012-09-01T21:00:00
Sep  1 21:00:10 myth-server mythbackend[2101]: E Commflag_1631 storagegroup.cpp:184 (Init) SG(Default): Unable to find any Storage Group Directories.  Using hardcoded default value of '/mnt/store'
Sep  1 21:00:10 myth-server mythbackend[2101]: E Commflag_1631 programinfo.cpp:2278 (GetPlaybackURL) ProgramInfo(5197_20120901210000.mpg): GetPlaybackURL: '5197_20120901210000.mpg' should be local, but it can not be found.
```

I have storage directories setup. My recording directory is set for. "/var/lib/mythtv/recordings"
Any help would be appreciated.

---

### Post by nickrout on 2012-09-04
run find_orphans.py (availble in the wiki) and see what it tells you.

---

### Post by grygub on 2012-09-04
Thanks for the help, the python script told me what was missing but no new information. One thing in the log that stood out is where it said "unable to find any storage directories, using hard coded defaults". I had directories set for recordings, livetv, artwork and all the rest but had no path set for default. After setting the default to mythtv/recordings all new recordings have worked. I feel like it should have used the recordings storage directory not default storage directory but it seems to work now.

---

### Post by nickrout on 2012-09-05
> **grygub said:**
> Thanks for the help, the python script told me what was missing but no new information. One thing in the log that stood out is where it said "unable to find any storage directories, using hard coded defaults". I had directories set for recordings, livetv, artwork and all the rest but had no path set for default. After setting the default to mythtv/recordings all new recordings have worked. I feel like it should have used the recordings storage directory not default storage directory but it seems to work now.

Yeah i saw that after I posted but got distracted and haven't had a chance to come back and post again. 

Not sure where you got a Recordings SG, i don't have one and default is the default place for recordings to go.

---

### Post by grygub on 2012-09-05
I think it has to do with my database originally coming from an older version of mythtv that used a recordings directory. Thanks for the help.

---

