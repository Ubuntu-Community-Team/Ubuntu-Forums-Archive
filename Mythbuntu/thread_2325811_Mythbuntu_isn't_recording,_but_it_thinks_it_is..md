---
title: "Mythbuntu isn't recording, but it thinks it is."
date: 2016-05-25
forum: Mythbuntu
---

### Post by tim129 on 2016-05-25
Slowly making my way thru to a working pvr. I'm using Mythbuntu ubuntu 16.04 with MythTV .28. I have a working mythweb. Currently though it isn't recording though it says it is. 

I'm using a HDhomerun extend (but also have another hdhomerun dual and a hauppauge 2250 but haven't set those up yet to make debugging simpler)

It appears Mythtv thinks it is recording according to the Mythweb recorded programs page, but it can't find the stored file. Here is a copy of the mythbackend.log from lastnight's attempt of 2 back to back recordings. I'm wondering what might be going on. I'm seeing a couple failures in the log. I think I have the setup done correctly. I followed the set up shown by [https://www.youtube.com/watch?v=dmSZ8krQM_8&list=PLBtmNw99p_iURWCxSLv2bvFRpLXFTZ4tr&index=2](https://www.youtube.com/watch?v=dmSZ8krQM_8&list=PLBtmNw99p_iURWCxSLv2bvFRpLXFTZ4tr&index=2) and adapted it to my setup. Though it shows setting up the myth master backend server as the ip address of your current box, but I had to change it to 127.0.0.1 to get mythweb working. 

Any help would be appreciated. I'm sort of stumped on why the recording isn't working right now.

As I side note, I'm also trying to connect Kodi from my main machine to the backend box, but I'm getting in the kodi logs --  Error Message : 'No response from MythTV backend' But I'm not worried about that since getting working recordings is my first priority. I think the kodi issue might be related to maybe mysql not being accessible from outside the box... but that's my fumbling guess too... anyway... that's a side step and will try to tackle that after getting some recordings working.)

Here is a section of the logs from a bit before the start of the recordings to the end of those recording attempts.

```
May 24 19:59:00 tim-mythtv mythbackend: mythbackend[891]: I Scheduler scheduler.cpp:2267 (HandleReschedule) Reschedule requested for PLACE PrepareToRecordMay 24 19:59:00 tim-mythtv mythbackend: mythbackend[891]: I Scheduler scheduler.cpp:2380 (HandleReschedule) Scheduled 4 items in 0.0 = 0.00 match + 0.00 check + 0.01 place
May 24 19:59:30 tim-mythtv mythbackend: mythbackend[891]: I Scheduler mythdbcon.cpp:422 (PurgeIdleConnections) New DB connection, total: 10
May 24 19:59:30 tim-mythtv mythbackend: mythbackend[891]: I TVRecEvent tv_rec.cpp:1610 (HandlePendingRecordings) TVRec[1]: ASK_RECORDING 1 29 0 0
May 24 20:00:00 tim-mythtv mythbackend: mythbackend[891]: I TVRecEvent tv_rec.cpp:1073 (HandleStateChange) TVRec[1]: Changing from None to RecordingOnly
May 24 20:00:00 tim-mythtv mythbackend: mythbackend[891]: I TVRecEvent mythdbcon.cpp:422 (PurgeIdleConnections) New DB connection, total: 10
May 24 20:00:00 tim-mythtv mythbackend: mythbackend[891]: I TVRecEvent tv_rec.cpp:3563 (TuningCheckForHWChange) TVRec[1]: HW Tuner: 1->1
May 24 20:00:00 tim-mythtv mythbackend: mythbackend[891]: I TVRecEvent tv_rec.cpp:3685 (TuningFrequency) TVRec[1]: TuningFrequency
May 24 20:00:00 tim-mythtv mythbackend: mythbackend[891]: E TVRecEvent dtvmultiplex.cpp:379 (ParseTuningParams) DTVMux: ParseTuningParams -- Unknown tuner type = 0xffffffff80000000
May 24 20:00:00 tim-mythtv mythbackend: mythbackend[891]: E TVRecEvent recorders/dtvchannel.cpp:299 (SetChannelByString) DTVChan[1](10534239-0): SetChannelByString(4_1): Failed to initialize multiplex options
May 24 20:00:00 tim-mythtv mythbackend: mythbackend[891]: E TVRecEvent tv_rec.cpp:3763 (TuningFrequency) TVRec[1]: Failed to set channel to 4_1. Reverting to kState_None
May 24 20:00:00 tim-mythtv mythbackend: mythbackend[891]: I TVRecEvent tv_rec.cpp:1073 (HandleStateChange) TVRec[1]: Changing from RecordingOnly to None
May 24 20:00:00 tim-mythtv mythbackend: mythbackend[891]: I CoreContext scheduler.cpp:725 (UpdateRecStatus) Updating status for "Person of Interest":QSO on cardid 1 (Will Record => Recorder Failed)
May 24 20:00:00 tim-mythtv mythbackend: mythbackend[891]: I CoreContext mythdbcon.cpp:422 (PurgeIdleConnections) New DB connection, total: 10
May 24 20:00:00 tim-mythtv mythbackend: mythbackend[891]: I Scheduler scheduler.cpp:2819 (HandleRecordingStatusChange) Tuning recording: "Person of Interest":QSO: channel 1041 on cardid 1, sourceid 1
May 24 20:00:00 tim-mythtv mythbackend: mythbackend[891]: I Scheduler scheduler.cpp:2267 (HandleReschedule) Reschedule requested for CHECK -9 8 0 UpdateRecStatus2 | Person of Interest | QSO | Root goes under cover to protect the host of a radio show; Samaritan's agents try to assure a team member that their intentions are noble. | EP014198470098
May 24 20:00:00 tim-mythtv mythbackend: mythbackend[891]: E Scheduler recordinginfo.cpp:1025 (InsertProgram) RecordingInfo::InsertProgram(ProgramInfo(1041_20160525020000.ts): channame(KCNC-TV) startts(Wed May 25 02:00:00 2016 GMT) endts(Wed May 25 03:00:00 2016 GMT)#012             recstartts(Wed May 25 02:00:00 2016 GMT) recendts(Wed May 25 03:00:00 2016 GMT)#012             title(Person of Interest)): recording already exists...
May 24 20:00:00 tim-mythtv mythbackend: mythbackend[891]: I TVRecEvent tv_rec.cpp:1073 (HandleStateChange) TVRec[1]: Changing from None to RecordingOnly
May 24 20:00:00 tim-mythtv mythbackend: mythbackend[891]: I TVRecEvent tv_rec.cpp:3563 (TuningCheckForHWChange) TVRec[1]: HW Tuner: 1->1
May 24 20:00:00 tim-mythtv mythbackend: mythbackend[891]: I TVRecEvent tv_rec.cpp:3685 (TuningFrequency) TVRec[1]: TuningFrequency
May 24 20:00:00 tim-mythtv mythbackend: mythbackend[891]: E TVRecEvent dtvmultiplex.cpp:379 (ParseTuningParams) DTVMux: ParseTuningParams -- Unknown tuner type = 0xffffffff80000000
May 24 20:00:00 tim-mythtv mythbackend: mythbackend[891]: E TVRecEvent recorders/dtvchannel.cpp:299 (SetChannelByString) DTVChan[1](10534239-0): SetChannelByString(4_1): Failed to initialize multiplex options
May 24 20:00:00 tim-mythtv mythbackend: mythbackend[891]: E TVRecEvent tv_rec.cpp:3763 (TuningFrequency) TVRec[1]: Failed to set channel to 4_1. Reverting to kState_None
May 24 20:00:00 tim-mythtv mythbackend: mythbackend[891]: I TVRecEvent tv_rec.cpp:1073 (HandleStateChange) TVRec[1]: Changing from RecordingOnly to None
May 24 20:00:00 tim-mythtv mythbackend: mythbackend[891]: I CoreContext scheduler.cpp:725 (UpdateRecStatus) Updating status for "Person of Interest":QSO on cardid 1 (Tuning => Recorder Failed)
May 24 20:00:00 tim-mythtv mythbackend: mythbackend[891]: E Scheduler scheduler.cpp:787 (ChangeRecordingEnd) Failed to change end time on card 1 to 2016-05-25T03:00:00Z
May 24 20:00:00 tim-mythtv mythbackend: mythbackend[891]: I Scheduler scheduler.cpp:2371 (HandleReschedule) Reschedule interrupted, will retry
May 24 20:00:00 tim-mythtv mythbackend: mythbackend[891]: I Scheduler scheduler.cpp:2267 (HandleReschedule) Reschedule requested for CHECK -9 8 0 UpdateRecStatus2 | Person of Interest | QSO | Root goes under cover to protect the host of a radio show; Samaritan's agents try to assure a team member that their intentions are noble. | EP014198470098
May 24 20:00:00 tim-mythtv mythbackend: mythbackend[891]: I Scheduler scheduler.cpp:2267 (HandleReschedule) Reschedule requested for PLACE Interrupted
May 24 20:00:00 tim-mythtv mythbackend: mythbackend[891]: I Scheduler scheduler.cpp:2380 (HandleReschedule) Scheduled 4 items in 0.0 = 0.00 match + 0.00 check + 0.01 place
May 24 20:00:00 tim-mythtv mythbackend: mythbackend[891]: C CoreContext programinfo.cpp:351 (ProgramInfo) ProgramInfo(): Failed to find recorded entry for 0.
May 24 20:00:02 tim-mythtv mythbackend: mythbackend[891]: I ProcessRequest mainserver.cpp:1698 (HandleAnnounce) MainServer: MainServer::ANN Monitor
May 24 20:00:02 tim-mythtv mythbackend: mythbackend[891]: I ProcessRequest mainserver.cpp:1703 (HandleAnnounce) MainServer: adding: tim-mythtv(1ccd290) as a client (events: 0)
May 24 20:00:02 tim-mythtv mythbackend: mythbackend[891]: I MythSocketThread(64) mainserver.cpp:7629 (connectionClosed) Monitor sock(1ccd290) 'tim-mythtv' disconnected
May 24 20:00:05 tim-mythtv mythbackend: mythbackend[891]: N Update autoexpire.cpp:264 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 0.0 GB w/freq: 15 min
May 24 20:01:40 tim-mythtv mythbackend: mythbackend[891]: E JobQueue programinfo.cpp:2594 (GetPlaybackURL) ProgramInfo(1041_20160525020000.ts): GetPlaybackURL: '1041_20160525020000.ts' should be local, but it can not be found.
May 24 20:01:40 tim-mythtv mythbackend: mythbackend[891]: E JobQueue programinfo.cpp:2594 (GetPlaybackURL) ProgramInfo(1041_20160525020000.ts): GetPlaybackURL: '1041_20160525020000.ts' should be local, but it can not be found.
May 24 20:01:40 tim-mythtv mythbackend: mythbackend[891]: I Metadata_13 jobqueue.cpp:2157 (DoMetadataLookupThread) JobQueue: Metadata Lookup Starting for "Person of Interest":QSO recorded from channel 1041 at 2016-05-25T02:00:00Z
May 24 20:01:42 tim-mythtv mythbackend: mythbackend[891]: I ProcessRequest mainserver.cpp:1698 (HandleAnnounce) MainServer: MainServer::ANN Monitor
May 24 20:01:42 tim-mythtv mythbackend: mythbackend[891]: I ProcessRequest mainserver.cpp:1703 (HandleAnnounce) MainServer: adding: tim-mythtv(1ccd290) as a client (events: 0)
May 24 20:01:42 tim-mythtv mythbackend: mythbackend[891]: I ProcessRequest mainserver.cpp:1698 (HandleAnnounce) MainServer: MainServer::ANN Monitor
May 24 20:01:42 tim-mythtv mythbackend: mythbackend[891]: I ProcessRequest mainserver.cpp:1703 (HandleAnnounce) MainServer: adding: tim-mythtv(1c35c10) as a client (events: 1)
May 24 20:01:46 tim-mythtv mythbackend: mythbackend[891]: I ProcessRequest mainserver.cpp:1698 (HandleAnnounce) MainServer: MainServer::ANN Playback
May 24 20:01:46 tim-mythtv mythbackend: mythbackend[891]: I ProcessRequest mainserver.cpp:1703 (HandleAnnounce) MainServer: adding: tim-mythtv(1cc99f0) as a client (events: 0)
May 24 20:01:46 tim-mythtv mythbackend: mythbackend[891]: E ProcessRequest threadedfilewriter.cpp:129 (Open) TFW(/media/tim/maindata/mythtvdata/coverart//Person of Interest Season 5_coverart.jpg:-1): Opening file '/media/tim/maindata/mythtvdata/coverart//Person of Interest Season 5_coverart.jpg'.#012#011#011#011eno: Permission denied (13)
May 24 20:03:45 tim-mythtv mythbackend: mythbackend[891]: E JobQueue programinfo.cpp:2594 (GetPlaybackURL) ProgramInfo(1041_20160525020001.ts): GetPlaybackURL: '1041_20160525020001.ts' should be local, but it can not be found.
May 24 20:03:45 tim-mythtv mythbackend: mythbackend[891]: E JobQueue programinfo.cpp:2594 (GetPlaybackURL) ProgramInfo(1041_20160525020001.ts): GetPlaybackURL: '1041_20160525020001.ts' should be local, but it can not be found.
May 24 20:03:45 tim-mythtv mythbackend: mythbackend[891]: I Metadata_14 jobqueue.cpp:2157 (DoMetadataLookupThread) JobQueue: Metadata Lookup Starting for "Person of Interest":QSO recorded from channel 1041 at 2016-05-25T02:00:01Z
May 24 20:59:00 tim-mythtv mythbackend: mythbackend[891]: I Scheduler scheduler.cpp:2267 (HandleReschedule) Reschedule requested for PLACE PrepareToRecord
May 24 20:59:00 tim-mythtv mythbackend: mythbackend[891]: I Scheduler scheduler.cpp:2380 (HandleReschedule) Scheduled 4 items in 0.0 = 0.00 match + 0.00 check + 0.01 place
May 24 20:59:30 tim-mythtv mythbackend: mythbackend[891]: I TVRecEvent tv_rec.cpp:1610 (HandlePendingRecordings) TVRec[1]: ASK_RECORDING 1 29 0 0
May 24 21:00:00 tim-mythtv mythbackend: mythbackend[891]: I TVRecEvent tv_rec.cpp:1073 (HandleStateChange) TVRec[1]: Changing from None to RecordingOnly
May 24 21:00:00 tim-mythtv mythbackend: mythbackend[891]: I TVRecEvent tv_rec.cpp:3563 (TuningCheckForHWChange) TVRec[1]: HW Tuner: 1->1
May 24 21:00:00 tim-mythtv mythbackend: mythbackend[891]: I TVRecEvent tv_rec.cpp:3685 (TuningFrequency) TVRec[1]: TuningFrequency
May 24 21:00:00 tim-mythtv mythbackend: mythbackend[891]: E TVRecEvent dtvmultiplex.cpp:379 (ParseTuningParams) DTVMux: ParseTuningParams -- Unknown tuner type = 0xffffffff80000000
May 24 21:00:00 tim-mythtv mythbackend: mythbackend[891]: E TVRecEvent recorders/dtvchannel.cpp:299 (SetChannelByString) DTVChan[1](10534239-0): SetChannelByString(4_1): Failed to initialize multiplex options
May 24 21:00:00 tim-mythtv mythbackend: mythbackend[891]: E TVRecEvent tv_rec.cpp:3763 (TuningFrequency) TVRec[1]: Failed to set channel to 4_1. Reverting to kState_None
May 24 21:00:00 tim-mythtv mythbackend: mythbackend[891]: I TVRecEvent tv_rec.cpp:1073 (HandleStateChange) TVRec[1]: Changing from RecordingOnly to None
May 24 21:01:50 tim-mythtv mythbackend: mythbackend[891]: E JobQueue programinfo.cpp:2594 (GetPlaybackURL) ProgramInfo(1041_20160525030000.ts): GetPlaybackURL: '1041_20160525030000.ts' should be local, but it can not be found.
May 24 21:01:50 tim-mythtv mythbackend: mythbackend[891]: E JobQueue programinfo.cpp:2594 (GetPlaybackURL) ProgramInfo(1041_20160525030000.ts): GetPlaybackURL: '1041_20160525030000.ts' should be local, but it can not be found.
May 24 21:01:50 tim-mythtv mythbackend: mythbackend[891]: I Metadata_15 jobqueue.cpp:2157 (DoMetadataLookupThread) JobQueue: Metadata Lookup Starting for "Person of Interest":Reassortment recorded from channel 1041 at 2016-05-25T03:00:00Z
May 25 09:12:36 tim-mythtv mythbackend: mythbackend[878]: C thread_unknown mythcommandlineparser.cpp:2599 (ConfigureLogging) mythbackend version: fixes/0.28 [v28.0-26-gf58b100] www.mythtv.org
May 25 09:12:36 tim-mythtv mythbackend: mythbackend[878]: C thread_unknown mythcommandlineparser.cpp:2601 (ConfigureLogging) Qt version: compile: 5.5.1, runtime: 5.5.1
May 25 09:12:36 tim-mythtv mythbackend: mythbackend[878]: N thread_unknown mythcommandlineparser.cpp:2603 (ConfigureLogging) Enabled verbose msgs:  general
```

---

### Post by tim129 on 2016-05-31
I've let the machine run even though it wasn't doing anything succesfully. Maybe that kicked it in gear cause it reports recording a program correctly, and I do have a  4gig file on the drive.... Now I'm just trying to figure out how to get it from the machine to my main one to see how it plays back.... But mythweb reports the file doesn't exist, but looking at the harddrive it does. Access problem or a pointer problem from what I can see so far.

---

