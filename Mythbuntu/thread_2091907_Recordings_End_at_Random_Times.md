---
title: "Recordings End at Random Times"
date: 2012-12-06
forum: Mythbuntu
---

### Post by km782 on 2012-12-06
I am having a strange issue with the latest version of 0.25 running on 12.04.  All of my recordings seem to end randomly.  If it is listed as a 30 minute show, I would expect the recording to last for exactly 30 minutes.  Some are a minute or two longer than that (31:47, 30:54, etc.) and others are shorter (29:22, 26:55, etc.).  Most of the time it is good enough to record the entire show, but occassionally I will miss the ending or in a few cases the recording only lasts something like 12 or 16 minutes.  I have yet to see a recording that was exactly 30:00 long.  Is anyone else having this problem?

---

### Post by nickrout on 2012-12-07
> **km782 said:**
> I am having a strange issue with the latest version of 0.25 running on 12.04.  All of my recordings seem to end randomly.  If it is listed as a 30 minute show, I would expect the recording to last for exactly 30 minutes.  Some are a minute or two longer than that (31:47, 30:54, etc.) and others are shorter (29:22, 26:55, etc.).  Most of the time it is good enough to record the entire show, but occassionally I will miss the ending or in a few cases the recording only lasts something like 12 or 16 minutes.  I have yet to see a recording that was exactly 30:00 long.  Is anyone else having this problem?Check your backend log to see if there is any error or other clue shown when a recording ends.

---

### Post by km782 on 2012-12-07
> **nickrout said:**
> Check your backend log to see if there is any error or other clue shown when a recording ends.

Here is the log from Monday Dec. 3rd.  The show titled "How I Met Your Mother":"Lobster Crawl" is set to record at 8:00pm.  Prior to that the show "Family Guy":"A Picture Is Worth 1,000 Bucks" had been recorded.  I have all of my recordings set to start 1 minute early and end -1 minutes late (in other words end 1 min early).  So one recording was set to end at 7:59pm and the next one was set to record from 7:59pm to 8:29pm.

The show  "How I Met Your Mother":"Lobster Crawl" is 26:33 long so the end of the show was not recorded.  I don't see anything wrong in the log.  It looks like the recording starts at 7:59:01pm and ends at 8:29:00pm like it is supposed to.

```
Dec  3 19:55:19 HTPC mythbackend[1503]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
Dec  3 19:58:31 HTPC mythbackend[1503]: I TVRecEvent tv_rec.cpp:1544 (HandlePendingRecordings) TVRec(1): ASK_RECORDING 1 28 0 0
Dec  3 19:59:00 HTPC mythbackend[1503]: I TVRecEvent tv_rec.cpp:1030 (HandleStateChange) TVRec(1): Changing from RecordingOnly to None
Dec  3 19:59:00 HTPC mythbackend[1503]: I TVRecEvent tv_rec.cpp:817 (FinishedRecording) TVRec(1): FinishedRecording(1541_2012-12-03T19:28:00) damaged recq:<RecordingQuality overall_score="0.782222" key="1541_2012-12-03T19:28:00" countinuity_error_count="38" packet_count="16017706">#012    <Gap start="2012-12-03T19:35:49" end="2012-12-03T19:35:51" duration="1" />#012    <Gap start="2012-12-03T19:58:55" end="2012-12-03T20:00:00" duration="65" />#012</RecordingQuality>
Dec  3 19:59:00 HTPC mythbackend[1503]: I CoreContext scheduler.cpp:637 (UpdateRecStatus) Updating status for "Family Guy":"A Picture Is Worth 1,000 Bucks" on cardid 1 (Recording => Recorded)
Dec  3 19:59:01 HTPC mythbackend[1503]: E CoreContext mainserver.cpp:871 (customEvent) MainServer: PREVIEW_SUCCESS but no receivers.
Dec  3 19:59:01 HTPC mythbackend[1503]: I TVRecEvent tv_rec.cpp:1030 (HandleStateChange) TVRec(1): Changing from None to RecordingOnly
Dec  3 19:59:01 HTPC mythbackend[1503]: I TVRecEvent tv_rec.cpp:3503 (TuningCheckForHWChange) TVRec(1): HW Tuner: 1->1
Dec  3 19:59:01 HTPC mythbackend[1503]: N Scheduler autoexpire.cpp:263 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 3.0 GB w/freq: 14 min
Dec  3 19:59:01 HTPC mythbackend[1503]: I Scheduler scheduler.cpp:2513 (HandleRecordingStatusChange) Tuning recording: "How I Met Your Mother":"Lobster Crawl": channel 1131 on cardid 1, sourceid 3
Dec  3 19:59:02 HTPC mythbackend[1503]: I Scheduler scheduler.cpp:2033 (HandleReschedule) Reschedule requested for id 0.
Dec  3 19:59:04 HTPC mythbackend[1503]: I Scheduler scheduler.cpp:2093 (HandleReschedule) Scheduled 186 items in 1.6 = 0.00 match + 1.56 place
Dec  3 19:59:11 HTPC mythbackend[1503]: I ProcessRequest mainserver.cpp:1360 (HandleAnnounce) MainServer::ANN Monitor
Dec  3 19:59:11 HTPC mythbackend[1503]: I ProcessRequest mainserver.cpp:1362 (HandleAnnounce) adding: HTPC as a client (events: 0)
Dec  3 19:59:11 HTPC mythbackend[1503]: I ProcessRequest mainserver.cpp:1360 (HandleAnnounce) MainServer::ANN Monitor
Dec  3 19:59:11 HTPC mythbackend[1503]: I ProcessRequest mainserver.cpp:1362 (HandleAnnounce) adding: HTPC as a client (events: 1)
Dec  3 19:59:41 HTPC mythbackend[1503]: E JobQueue programinfo.cpp:2278 (GetPlaybackURL) ProgramInfo(1131_20121203195900.mpg): GetPlaybackURL: '1131_20121203195900.mpg' should be local, but it can not be found.
Dec  3 19:59:41 HTPC mythbackend[1503]: E JobQueue programinfo.cpp:2278 (GetPlaybackURL) ProgramInfo(1131_20121203195900.mpg): GetPlaybackURL: '1131_20121203195900.mpg' should be local, but it can not be found.
Dec  3 19:59:41 HTPC mythbackend[1503]: I Commflag_3004 jobqueue.cpp:2276 (DoFlagCommercialsThread) JobQueue: Commercial Detection Starting for "How I Met Your Mother":"Lobster Crawl" recorded from channel 1131 at 2012-12-03T19:59:00
Dec  3 19:59:41 HTPC mythbackend[1503]: E Commflag_3004 programinfo.cpp:2278 (GetPlaybackURL) ProgramInfo(1131_20121203195900.mpg): GetPlaybackURL: '1131_20121203195900.mpg' should be local, but it can not be found.
Dec  3 20:00:22 HTPC mythbackend[1503]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
Dec  3 20:01:40 HTPC mythbackend[1503]: N Expire autoexpire.cpp:263 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 3.0 GB w/freq: 14 min
Dec  3 20:02:26 HTPC mythbackend[1503]: I CoreContext scheduler.cpp:637 (UpdateRecStatus) Updating status for "How I Met Your Mother":"Lobster Crawl" on cardid 1 (Tuning => Recording)
Dec  3 20:02:26 HTPC mythbackend[1503]: I TVRecEvent tv_rec.cpp:3997 (TuningNewRecorder) TVRec(1): rec->GetPathname(): '/var/lib/mythtv/recordings/1131_20121203195900.mpg'
Dec  3 20:05:26 HTPC mythbackend[1503]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
Dec  3 20:10:26 HTPC mythbackend[1503]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
Dec  3 20:15:29 HTPC mythbackend[1503]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
Dec  3 20:15:40 HTPC mythbackend[1503]: N Expire autoexpire.cpp:263 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 3.0 GB w/freq: 14 min
Dec  3 20:15:41 HTPC mythbackend[1503]: N Expire autoexpire.cpp:640 (SendDeleteMessages) Expiring 2792 MB for 1541 at 2012-10-24T23:59:00 => "How I Met Your Mother":"First Time in New York"
Dec  3 20:15:41 HTPC mythbackend[1503]: I Scheduler scheduler.cpp:2033 (HandleReschedule) Reschedule requested for id 0.
Dec  3 20:15:41 HTPC mythbackend[1503]: I Scheduler scheduler.cpp:2033 (HandleReschedule) Reschedule requested for id 0.
Dec  3 20:15:42 HTPC mythbackend[1503]: I Scheduler scheduler.cpp:2093 (HandleReschedule) Scheduled 185 items in 0.5 = 0.00 match + 0.49 place
Dec  3 20:15:49 HTPC mythbackend[1503]: I Scheduler scheduler.cpp:2033 (HandleReschedule) Reschedule requested for id 0.
Dec  3 20:15:49 HTPC mythbackend[1503]: I Scheduler scheduler.cpp:2093 (HandleReschedule) Scheduled 185 items in 0.3 = 0.00 match + 0.35 place
Dec  3 20:20:34 HTPC mythbackend[1503]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
Dec  3 20:25:37 HTPC mythbackend[1503]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
Dec  3 20:29:00 HTPC mythbackend[1503]: I TVRecEvent tv_rec.cpp:1030 (HandleStateChange) TVRec(1): Changing from RecordingOnly to None
Dec  3 20:29:00 HTPC mythbackend[1503]: E DVBRead dvbstreamhandler.cpp:214 (RunTS) DVBSH(/dev/dvb/adapter0/frontend0): Device EOF detected
Dec  3 20:29:00 HTPC mythbackend[1503]: I TVRecEvent tv_rec.cpp:817 (FinishedRecording) TVRec(1): FinishedRecording(1131_2012-12-03T19:59:00) damaged recq:<RecordingQuality overall_score="0" key="1131_2012-12-03T19:59:00" countinuity_error_count="0" packet_count="17923261">#012    <Gap start="2012-12-03T20:00:00" end="2012-12-03T20:02:26" duration="146" />#012    <Gap start="2012-12-03T20:28:59" end="2012-12-03T20:30:00" duration="61" />#012</RecordingQuality>
Dec  3 20:29:00 HTPC mythbackend[1503]: I CoreContext scheduler.cpp:637 (UpdateRecStatus) Updating status for "How I Met Your Mother":"Lobster Crawl" on cardid 1 (Recording => Recorded)
Dec  3 20:29:01 HTPC mythbackend[1503]: I Scheduler scheduler.cpp:2033 (HandleReschedule) Reschedule requested for id 0.
Dec  3 20:29:01 HTPC mythbackend[1503]: I Scheduler scheduler.cpp:2080 (HandleReschedule) Reschedule interrupted, will retry
Dec  3 20:29:01 HTPC mythbackend[1503]: I Scheduler scheduler.cpp:2033 (HandleReschedule) Reschedule requested for id 0.
Dec  3 20:29:01 HTPC mythbackend[1503]: I Scheduler scheduler.cpp:2093 (HandleReschedule) Scheduled 185 items in 0.4 = 0.00 match + 0.36 place
Dec  3 20:29:02 HTPC mythbackend[1503]: I ProcessRequest mainserver.cpp:1360 (HandleAnnounce) MainServer::ANN Monitor
Dec  3 20:29:02 HTPC mythbackend[1503]: I ProcessRequest mainserver.cpp:1362 (HandleAnnounce) adding: HTPC as a client (events: 0)
Dec  3 20:29:02 HTPC mythbackend[1503]: I ProcessRequest mainserver.cpp:1360 (HandleAnnounce) MainServer::ANN Monitor
Dec  3 20:29:02 HTPC mythbackend[1503]: I ProcessRequest mainserver.cpp:1362 (HandleAnnounce) adding: HTPC as a client (events: 1)
Dec  3 20:29:40 HTPC mythbackend[1503]: N Expire autoexpire.cpp:263 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
Dec  3 20:30:38 HTPC mythbackend[1503]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
```

---

### Post by azmyth on 2012-12-08
There's two ways to extend a recording with this being hard and soft. Which one do you have set?

Also, make sure your OS clock is displaying the proper time. I had mine set to check the nntp server and something went wrong and it stopped working thus I had recordings with all messed up times before I realized.

$date

---

### Post by nickrout on 2012-12-08
Also check the actual recorded file with mediainfo to see how long it says the recording is. Sometimes myth's ui shows the time wrong, so it may be that your recording rule (somewhat predictably) cut the end off.

Why are you doing that by the way? Looks like you need more tuners, or (if you have digital) use more virtual tuners.

---

### Post by lisati on 2012-12-08
Just an observation, based more on using a Tivo than mythbuntu:

If you're setting your recording times based on an EPG (or similar), recording can be messed up when programs are running early or late. What I usually do is set my machine to start recording a minute or two early, and keep on recording a minute or two after the scheduled air time. As others have noted, recording can also be messed up when there's some kind of overlap between shows that exceeds any spare capacity your tuner system might have.

---

### Post by km782 on 2012-12-08
> **azmyth said:**
> There's two ways to extend a recording with this being hard and soft. Which one do you have set?

Also, make sure your OS clock is displaying the proper time. I had mine set to check the nntp server and something went wrong and it stopped working thus I had recordings with all messed up times before I realized.

$date

I'm not really sure what you mean.  In the individual recording rules for each show I want to record I have the setting for "Start Early" set to 1 and the setting for "End Late" set to -1.

Also, I checked my OS clock and it is displaying the correct time.

---

### Post by km782 on 2012-12-08
> **nickrout said:**
> Also check the actual recorded file with mediainfo to see how long it says the recording is. Sometimes myth's ui shows the time wrong, so it may be that your recording rule (somewhat predictably) cut the end off.

Why are you doing that by the way? Looks like you need more tuners, or (if you have digital) use more virtual tuners.

I downloaded and installed mediainfo and the lengths it is giving me for the recordings matches what MythTv is displaying.

My thinking on the recordings goes like this.  I want to make sure to get the beginning of a show in case one of the networks is running a little fast.  I only have two tuners right now (maybe I'll look into buying another card soon) so I set the recording to end a minute early so that there isn't any overlap with recordings that start right after that show ends.  I figure in the worst case I just won't record the credits.  When the right amount of time is recorded it seems to work well.

I tried changing the start early and end late settings both to 0 just in case that had something to do with it but I'm getting the same behavior.

---

### Post by nickrout on 2012-12-08
Thanks for your update. This is very odd.

Sometimes if the stream being recorded is a little glitchy (like if maybe your antenna or cabling or general reception are dodgy) mythtv will stop recording, or alternatively the frontend will not play back past a particular  glitch.

If it had stoppped recording early I would say it was the backend giving up due to glitches, and there would be something in the logs.

Can you try playing a recording in another player like vlc or mplayer that might be a bit more tolerant of a glitch in the recording? See if there is anything on the end that myth's frontend is missing?

What sort of tuners do you have? And is it recording a digital transmission or analogue? Cable or OTA?

---

### Post by nickrout on 2012-12-08
> **lisati said:**
> Just an observation, based more on using a Tivo than mythbuntu:

If you're setting your recording times based on an EPG (or similar), recording can be messed up when programs are running early or late. What I usually do is set my machine to start recording a minute or two early, and keep on recording a minute or two after the scheduled air time. As others have noted, recording can also be messed up when there's some kind of overlap between shows that exceeds any spare capacity your tuner system might have.Hi to another Kiwi!

---

### Post by km782 on 2012-12-09
> **nickrout said:**
> Thanks for your update. This is very odd.

Sometimes if the stream being recorded is a little glitchy (like if maybe your antenna or cabling or general reception are dodgy) mythtv will stop recording, or alternatively the frontend will not play back past a particular  glitch.

If it had stoppped recording early I would say it was the backend giving up due to glitches, and there would be something in the logs.

Can you try playing a recording in another player like vlc or mplayer that might be a bit more tolerant of a glitch in the recording? See if there is anything on the end that myth's frontend is missing?

What sort of tuners do you have? And is it recording a digital transmission or analogue? Cable or OTA?

nickrout, thanks for your responses.

I have the Hauppauge HVR-2250 dual tuner card and am watching digital transmissions OTA.  I live in the US.

I know what you mean about the glitches shortening the recording.  That has happened to me before on other stations where the signal is much weaker.  This particular station has its tower only a few miles from my home so the signal is very strong and there aren't any glitches that show up at all.  I tried playing the video file in vlc and it stops at the same point as the Myth frontend.

I pulled up this episode online on cbs.com to see what I missed.  Not only does the recording end early but it also starts late.  I missed about 2:20 of the beginning of the episode and the last 1:00.  I don't know if the network was running early that night, but if myth backend actually started recording when it was supposed to that would mean the network was ahead of schedule by 3:30 because it is set to start a minute early.  I know they aren't always exactly on time, but my experience has always been that they are within a minute so I'm not sure that that is likely.  It looks like the recording both started later than it was supposed to and ended earlier.

To be fair, this doesn't really happen very often.  Actually, the last few updates seemed to have cut down on the number of times it happens.  

I still find it strange though that some recordings are almost 31 mins and others are almost 30.  (Obviously, it doesn't really matter that much because either way the whole show is recorded.)  As an example, I have a recording rule set up to record all Family Guy episodes.  Yesterday, there were two that came on (both on the same network) and one recorded for 29:57 and the other for 30:55.  So the same rule, but different recording times.  The 29:57 is probably perfect because it takes the tuner a second or two to lock on the channel.  The extra minute on the other recording though is still unexplained.

---

