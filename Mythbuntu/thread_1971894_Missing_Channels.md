---
title: "Missing Channels"
date: 2012-05-03
forum: Mythbuntu
---

### Post by Quadari on 2012-05-03
Hi All,

I'm hoping that someone might be able to help out with this as it has been a very perplexing experience for me so far.

The background:
I don't pay for cable, but my local company (Comcast, in the US) broadcasts the local stations in HD over their cables, so I plug that into the back of my Hauppauge 1600 and get all the local stations in HD, or at least I used to.

The story:
I was running mythtv 0.24 on mythubuntu 10.04.  Over the weekend I upgraded everything to 0.25 and 12.04.  Everything seemed to work fine except a few of the local channels simply do not come in anymore on my machine.  Now the perplexing part is that when I plug the cable into the back of my tv (bypassing my myth box) I get the channel just fine.  I can run a channel scan on my 5 year old tv and it picks up the channels with no problems.  I figure if the dumb tv can display the channels, shouldn't myth?  But yet if I run any sort of scan on my myth box (either within the myth backend setup, or using 'scan' or 'scte65-scan' from the command line) a few of the channels just refuse to show up, and thus I can't seem to tune to them.  As I mentioned, before all the upgrades I could tune to them just fine.


So I've spent the last four days or so trying everything I could to manually tune into and/or find those channels.  I'm happy to give any more information people want, but I'm sort of at the end of the line in terms of my knowledge of what is going on or how to get the information about those channels.

Thanks for any help,
Q

---

### Post by nickrout on 2012-05-03
> **Quadari said:**
> Hi All,

I'm hoping that someone might be able to help out with this as it has been a very perplexing experience for me so far.

The background:
I don't pay for cable, but my local company (Comcast, in the US) broadcasts the local stations in HD over their cables, so I plug that into the back of my Hauppauge 1600 and get all the local stations in HD, or at least I used to.

The story:
I was running mythtv 0.24 on mythubuntu 10.04.  Over the weekend I upgraded everything to 0.25 and 12.04.  Everything seemed to work fine except a few of the local channels simply do not come in anymore on my machine.  Now the perplexing part is that when I plug the cable into the back of my tv (bypassing my myth box) I get the channel just fine.  I can run a channel scan on my 5 year old tv and it picks up the channels with no problems.  I figure if the dumb tv can display the channels, shouldn't myth?  But yet if I run any sort of scan on my myth box (either within the myth backend setup, or using 'scan' or 'scte65-scan' from the command line) a few of the channels just refuse to show up, and thus I can't seem to tune to them.  As I mentioned, before all the upgrades I could tune to them just fine.


So I've spent the last four days or so trying everything I could to manually tune into and/or find those channels.  I'm happy to give any more information people want, but I'm sort of at the end of the line in terms of my knowledge of what is going on or how to get the information about those channels.

Thanks for any help,
Q

Tuning and recording is done by the backend. Check it's logs when tuning a channel.

---

### Post by Quadari on 2012-05-03
> **nickrout said:**
> Tuning and recording is done by the backend. Check it's logs when tuning a channel.

Here is my backend log when:
• Start watching live tv, tuned to a working HD channel.
• Then hit channel up a few times to scroll to the should-be-working-but-isn't channel and try to wait for it to tune.

After a few seconds, on screen an error box pops up saying" You should have received a channel lock by now...." 

While it is trying to tune, the pop-up info screen has on it:
Signal 0% | S/N  0 or 2.5dB (lips back and forth)  | BE 0 or 13008 or 13029 (again, changes around) | (_|___) | No Lock

I'm not sure what some of that means.


Here is the log while I did this:
```
May  3 13:04:33 mythbackend[1674]: I TVRecEvent tv_rec.cpp:1014 (HandleStateChange) TVRec(1): Changing from None to WatchingLiveTV
May  3 13:04:33 mythbackend[1674]: I TVRecEvent tv_rec.cpp:3456 (TuningCheckForHWChange) TVRec(1): HW Tuner: 1->1
May  3 13:04:34 mythbackend[1674]: N CoreContext autoexpire.cpp:263 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 2.0 GB w/freq: 14 min
May  3 13:04:37 mythbackend[1674]: N CoreContext autoexpire.cpp:263 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 2.0 GB w/freq: 14 min
May  3 13:04:40 mythbackend[1674]: I ProcessRequest recorderbase.cpp:386 (GetKeyframePositions) RecBase(1:/dev/dvb/adapter0/frontend0): GetKeyframePositions(1,9223372036854775807,#1) out of 2
May  3 13:04:40 mythbackend[1674]: I ProcessRequest recorderbase.cpp:386 (GetKeyframePositions) RecBase(1:/dev/dvb/adapter0/frontend0): GetKeyframePositions(1,9223372036854775807,#1) out of 2
May  3 13:04:55 mythbackend[1674]: I ProcessRequest mainserver.cpp:1360 (HandleAnnounce) MainServer::ANN Playback
May  3 13:04:55 mythbackend[1674]: I ProcessRequest mainserver.cpp:1362 (HandleAnnounce) adding: mymythbox as a client (events: 0)
May  3 13:04:55 mythbackend[1674]: I ProcessRequest mainserver.cpp:1475 (HandleAnnounce) MainServer::HandleAnnounce FileTransfer
May  3 13:04:55 mythbackend[1674]: I ProcessRequest mainserver.cpp:1477 (HandleAnnounce) adding: mymythbox as a remote file transfer
May  3 13:04:55 mythbackend[1674]: E ProcessRequest fileringbuffer.cpp:284 (OpenFile) FileRingBuf(/home/mymythbox/.mythtv/channels/NBC_Chicago.png): OpenFile(): Could not open.
May  3 13:04:55 mythbackend[1674]: W ProcessRequest mainserver.cpp:5801 (connectionClosed) MainServer: Unknown socket closing MythSocket(0x95eb3c0)
May  3 13:04:55 mythbackend[1674]: E ProcessRequest mythsocket.cpp:358 (writeStringList) MythSocket(95eb3c0:-1): writeStringList: Error, socket went unconnected.#012#011#011#011We wrote 0 of 10 bytes with 1 errors#012#011#011#011starts with: 2       ok
May  3 13:04:55 mythbackend[1674]: W ProcessRequest mainserver.cpp:5801 (connectionClosed) MainServer: Unknown socket closing MythSocket(0x95d1300)
May  3 13:04:55 mythbackend[1674]: E ProcessRequest mythsocket.cpp:358 (writeStringList) MythSocket(95d1300:-1): writeStringList: Error, socket went unconnected.#012#011#011#011We wrote 0 of 23 bytes with 1 errors#012#011#011#011starts with: 15      OK[]:[]66[]:[]0
May  3 13:04:55 mythbackend[1674]: I ProcessRequest mainserver.cpp:1360 (HandleAnnounce) MainServer::ANN Playback
May  3 13:04:55 mythbackend[1674]: I ProcessRequest mainserver.cpp:1362 (HandleAnnounce) adding: mymythbox as a client (events: 0)
May  3 13:04:55 mythbackend[1674]: I ProcessRequest mainserver.cpp:1475 (HandleAnnounce) MainServer::HandleAnnounce FileTransfer
May  3 13:04:55 mythbackend[1674]: I ProcessRequest mainserver.cpp:1477 (HandleAnnounce) adding: mymythbox as a remote file transfer
May  3 13:04:55 mythbackend[1674]: E ProcessRequest fileringbuffer.cpp:284 (OpenFile) FileRingBuf(/home/mymythbox/.mythtv/channels/universal_sports.jpg): OpenFile(): Could not open.
May  3 13:04:56 mythbackend[1674]: I ProcessRequest mainserver.cpp:1360 (HandleAnnounce) MainServer::ANN Playback
May  3 13:04:56 mythbackend[1674]: I ProcessRequest mainserver.cpp:1362 (HandleAnnounce) adding: mymythbox as a client (events: 0)
May  3 13:04:56 mythbackend[1674]: I ProcessRequest mainserver.cpp:1475 (HandleAnnounce) MainServer::HandleAnnounce FileTransfer
May  3 13:04:56 mythbackend[1674]: I ProcessRequest mainserver.cpp:1477 (HandleAnnounce) adding: mymythbox as a remote file transfer
May  3 13:04:56 mythbackend[1674]: E ProcessRequest fileringbuffer.cpp:284 (OpenFile) FileRingBuf(/home/mymythbox/.mythtv/channels/ECTV.png): OpenFile(): Could not open.
May  3 13:04:58 mythbackend[1674]: I ProcessRequest mainserver.cpp:1360 (HandleAnnounce) MainServer::ANN Playback
May  3 13:04:58 mythbackend[1674]: I ProcessRequest mainserver.cpp:1362 (HandleAnnounce) adding: mymythbox as a client (events: 0)
May  3 13:04:58 mythbackend[1674]: I ProcessRequest mainserver.cpp:1475 (HandleAnnounce) MainServer::HandleAnnounce FileTransfer
May  3 13:04:58 mythbackend[1674]: I ProcessRequest mainserver.cpp:1477 (HandleAnnounce) adding: mymythbox as a remote file transfer
May  3 13:04:58 mythbackend[1674]: E ProcessRequest fileringbuffer.cpp:284 (OpenFile) FileRingBuf(/home/mymythbox/.mythtv/channels/live_well_hd.jpg): OpenFile(): Could not open.
May  3 13:04:58 mythbackend[1674]: W ProcessRequest mainserver.cpp:5801 (connectionClosed) MainServer: Unknown socket closing MythSocket(0x95ead38)
May  3 13:04:58 mythbackend[1674]: E ProcessRequest mythsocket.cpp:358 (writeStringList) MythSocket(95ead38:-1): writeStringList: Error, socket went unconnected.#012#011#011#011We wrote 0 of 10 bytes with 1 errors#012#011#011#011starts with: 2       ok
May  3 13:05:00 mythbackend[1674]: E DVBRead dvbstreamhandler.cpp:214 (RunTS) DVBSH(/dev/dvb/adapter0/frontend0): Device EOF detected
May  3 13:05:00 mythbackend[1674]: I TVRecEvent tv_rec.cpp:3456 (TuningCheckForHWChange) TVRec(1): HW Tuner: 1->1
May  3 13:05:01 mythbackend[1674]: N CoreContext autoexpire.cpp:263 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 2.0 GB w/freq: 14 min
May  3 13:05:16 mythbackend[1674]: N Expire autoexpire.cpp:263 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 2.0 GB w/freq: 14 min
May  3 13:05:16 mythbackend[1674]: N Expire autoexpire.cpp:640 (SendDeleteMessages) Expiring 2816 MB for 5666 at 2012-04-26T20:30:00 => "Parks and Recreation":"The Debate"
May  3 13:05:16 mythbackend[1674]: N Expire autoexpire.cpp:640 (SendDeleteMessages) Expiring 2749 MB for 5666 at 2012-04-26T20:00:00 => "The Office":Fundraiser
May  3 13:05:16 mythbackend[1674]: N Expire autoexpire.cpp:640 (SendDeleteMessages) Expiring 2717 MB for 5666 at 2012-04-26T19:30:00 => "30 Rock":"Live From Studio 6H"
May  3 13:05:16 mythbackend[1674]: N Expire autoexpire.cpp:640 (SendDeleteMessages) Expiring 2677 MB for 5664 at 2012-04-14T14:28:00 => "America's Test Kitchen From Cook's Illustrated":"Crepes and Croissants"
May  3 13:05:16 mythbackend[1674]: N Expire autoexpire.cpp:640 (SendDeleteMessages) Expiring 726 MB for 3112 at 2012-03-21T18:58:00 => "Check, Please"
May  3 13:05:16 mythbackend[1674]: N Expire autoexpire.cpp:640 (SendDeleteMessages) Expiring 679 MB for 3112 at 2011-12-21T18:58:00 => "Check, Please"
May  3 13:05:16 mythbackend[1674]: N Expire autoexpire.cpp:640 (SendDeleteMessages) Expiring 746 MB for 3112 at 2011-12-14T18:58:00 => "Check, Please"
May  3 13:05:16 mythbackend[1674]: N Expire autoexpire.cpp:640 (SendDeleteMessages) Expiring 728 MB for 3112 at 2011-11-30T18:58:00 => "Check, Please"
May  3 13:05:16 mythbackend[1674]: N Expire autoexpire.cpp:640 (SendDeleteMessages) Expiring 768 MB for 3112 at 2011-11-23T18:58:00 => "Check, Please"
May  3 13:05:16 mythbackend[1674]: N Expire autoexpire.cpp:640 (SendDeleteMessages) Expiring 709 MB for 3112 at 2011-11-16T18:58:00 => "Check, Please"
May  3 13:05:16 mythbackend[1674]: N Expire autoexpire.cpp:640 (SendDeleteMessages) Expiring 833 MB for 3112 at 2011-11-10T01:58:00 => "Check, Please"
May  3 13:05:16 mythbackend[1674]: N Expire autoexpire.cpp:640 (SendDeleteMessages) Expiring 688 MB for 3112 at 2011-11-02T18:58:00 => "Check, Please"
May  3 13:05:16 mythbackend[1674]: E CoreContext programinfo.cpp:2278 (GetPlaybackURL) ProgramInfo(5666_20120426203000.mpg): GetPlaybackURL: '5666_20120426203000.mpg' should be local, but it can not be found.
May  3 13:05:16 mythbackend[1674]: E CoreContext mainserver.cpp:2582 (DoHandleDeleteRecording) ERROR when trying to delete file: GetPlaybackURL/UNABLE/TO/FIND/LOCAL/FILE/ON/mymythbox/5666_20120426203000.mpg. File doesn't exist.  Database metadata will not be removed.
May  3 13:05:16 mythbackend[1674]: E CoreContext programinfo.cpp:2278 (GetPlaybackURL) ProgramInfo(5666_20120426200000.mpg): GetPlaybackURL: '5666_20120426200000.mpg' should be local, but it can not be found.
May  3 13:05:16 mythbackend[1674]: E CoreContext mainserver.cpp:2582 (DoHandleDeleteRecording) ERROR when trying to delete file: GetPlaybackURL/UNABLE/TO/FIND/LOCAL/FILE/ON/mymythbox/5666_20120426200000.mpg. File doesn't exist.  Database metadata will not be removed.
May  3 13:05:16 mythbackend[1674]: E CoreContext programinfo.cpp:2278 (GetPlaybackURL) ProgramInfo(5666_20120426193000.mpg): GetPlaybackURL: '5666_20120426193000.mpg' should be local, but it can not be found.
May  3 13:05:16 mythbackend[1674]: E CoreContext mainserver.cpp:2582 (DoHandleDeleteRecording) ERROR when trying to delete file: GetPlaybackURL/UNABLE/TO/FIND/LOCAL/FILE/ON/mymythbox/5666_20120426193000.mpg. File doesn't exist.  Database metadata will not be removed.
May  3 13:05:16 mythbackend[1674]: E CoreContext programinfo.cpp:2278 (GetPlaybackURL) ProgramInfo(5664_20120414142800.mpg): GetPlaybackURL: '5664_20120414142800.mpg' should be local, but it can not be found.
May  3 13:05:16 mythbackend[1674]: E CoreContext mainserver.cpp:2582 (DoHandleDeleteRecording) ERROR when trying to delete file: GetPlaybackURL/UNABLE/TO/FIND/LOCAL/FILE/ON/mymythbox/5664_20120414142800.mpg. File doesn't exist.  Database metadata will not be removed.
May  3 13:05:16 mythbackend[1674]: E CoreContext programinfo.cpp:2278 (GetPlaybackURL) ProgramInfo(3112_20120321185800.mpg): GetPlaybackURL: '3112_20120321185800.mpg' should be local, but it can not be found.
May  3 13:05:16 mythbackend[1674]: E CoreContext mainserver.cpp:2582 (DoHandleDeleteRecording) ERROR when trying to delete file: GetPlaybackURL/UNABLE/TO/FIND/LOCAL/FILE/ON/mymythbox/3112_20120321185800.mpg. File doesn't exist.  Database metadata will not be removed.
May  3 13:05:16 mythbackend[1674]: E CoreContext programinfo.cpp:2278 (GetPlaybackURL) ProgramInfo(3112_20111221185800.mpg): GetPlaybackURL: '3112_20111221185800.mpg' should be local, but it can not be found.
May  3 13:05:16 mythbackend[1674]: E CoreContext mainserver.cpp:2582 (DoHandleDeleteRecording) ERROR when trying to delete file: GetPlaybackURL/UNABLE/TO/FIND/LOCAL/FILE/ON/mymythbox/3112_20111221185800.mpg. File doesn't exist.  Database metadata will not be removed.
May  3 13:05:16 mythbackend[1674]: E CoreContext programinfo.cpp:2278 (GetPlaybackURL) ProgramInfo(3112_20111214185800.mpg): GetPlaybackURL: '3112_20111214185800.mpg' should be local, but it can not be found.
May  3 13:05:16 mythbackend[1674]: E CoreContext mainserver.cpp:2582 (DoHandleDeleteRecording) ERROR when trying to delete file: GetPlaybackURL/UNABLE/TO/FIND/LOCAL/FILE/ON/mymythbox/3112_20111214185800.mpg. File doesn't exist.  Database metadata will not be removed.
May  3 13:05:16 mythbackend[1674]: E CoreContext programinfo.cpp:2278 (GetPlaybackURL) ProgramInfo(3112_20111130185800.mpg): GetPlaybackURL: '3112_20111130185800.mpg' should be local, but it can not be found.
May  3 13:05:16 mythbackend[1674]: E CoreContext mainserver.cpp:2582 (DoHandleDeleteRecording) ERROR when trying to delete file: GetPlaybackURL/UNABLE/TO/FIND/LOCAL/FILE/ON/mymythbox/3112_20111130185800.mpg. File doesn't exist.  Database metadata will not be removed.
May  3 13:05:16 mythbackend[1674]: E CoreContext programinfo.cpp:2278 (GetPlaybackURL) ProgramInfo(3112_20111123185800.mpg): GetPlaybackURL: '3112_20111123185800.mpg' should be local, but it can not be found.
May  3 13:05:16 mythbackend[1674]: E CoreContext mainserver.cpp:2582 (DoHandleDeleteRecording) ERROR when trying to delete file: GetPlaybackURL/UNABLE/TO/FIND/LOCAL/FILE/ON/mymythbox/3112_20111123185800.mpg. File doesn't exist.  Database metadata will not be removed.
May  3 13:05:16 mythbackend[1674]: E CoreContext programinfo.cpp:2278 (GetPlaybackURL) ProgramInfo(3112_20111116185800.mpg): GetPlaybackURL: '3112_20111116185800.mpg' should be local, but it can not be found.
May  3 13:05:16 mythbackend[1674]: E CoreContext mainserver.cpp:2582 (DoHandleDeleteRecording) ERROR when trying to delete file: GetPlaybackURL/UNABLE/TO/FIND/LOCAL/FILE/ON/mymythbox/3112_20111116185800.mpg. File doesn't exist.  Database metadata will not be removed.
May  3 13:05:16 mythbackend[1674]: E CoreContext programinfo.cpp:2278 (GetPlaybackURL) ProgramInfo(3112_20111110015800.mpg): GetPlaybackURL: '3112_20111110015800.mpg' should be local, but it can not be found.
May  3 13:05:16 mythbackend[1674]: E CoreContext mainserver.cpp:2582 (DoHandleDeleteRecording) ERROR when trying to delete file: GetPlaybackURL/UNABLE/TO/FIND/LOCAL/FILE/ON/mymythbox/3112_20111110015800.mpg. File doesn't exist.  Database metadata will not be removed.
May  3 13:05:16 mythbackend[1674]: E CoreContext programinfo.cpp:2278 (GetPlaybackURL) ProgramInfo(3112_20111102185800.mpg): GetPlaybackURL: '3112_20111102185800.mpg' should be local, but it can not be found.
May  3 13:05:16 mythbackend[1674]: E CoreContext mainserver.cpp:2582 (DoHandleDeleteRecording) ERROR when trying to delete file: GetPlaybackURL/UNABLE/TO/FIND/LOCAL/FILE/ON/mymythbox/3112_20111102185800.mpg. File doesn't exist.  Database metadata will not be removed.
May  3 13:05:43 mythbackend[1674]: I TVRecEvent tv_rec.cpp:1014 (HandleStateChange) TVRec(1): Changing from WatchingLiveTV to None
May  3 13:05:43 mythbackend[1674]: I TVRecEvent tv_rec.cpp:812 (FinishedRecording) TVRec(1): FinishedRecording(3205_2012-05-03T13:05:01) damaged recq:<RecordingQuality overall_score="0" key="5666_2012-05-03T13:04:37" countinuity_error_count="0" packet_count="211708">#012    <Gap start="2012-05-03T13:00:00" end="2012-05-03T13:04:37" duration="277" />#012    <Gap start="2012-05-03T13:04:59" end="2012-05-03T14:00:00" duration="3301" />#012</RecordingQuality>
```

---

### Post by Quadari on 2012-05-03
Update:

I think that I am missing channels if and only if they are on multiplex channel 29 (which I believe is frequency 255.0125 MHz).  Specifically they are at 29.1, 29.2, 29.3, 29.4, and 29.6.  (They get mapped to different virtual channels, but I think they're all on that same multiplex.)

Now, what's weird is that I _sometimes_ get them on my myth box.  This afternoon I sat in front of the tv and tried to tune in to them lots of times.  Every once in a while (maybe 1 in 10) the tuner connects and then I can watch the channels just fine.  Most of the time however, I just get stalled at the screen trying to tune into them.  And just to re-iterate, when I bypass the myth box and just watch directly on my tv I never have any problems tuning into them.  :confused:

I'm hoping maybe this info helps someone help my diagnose the problem a bit more.

Thanks.

---

### Post by nickrout on 2012-05-03
> **Quadari said:**
> Update:

I think that I am missing channels if and only if they are on multiplex channel 29 (which I believe is frequency 255.0125 MHz).  Specifically they are at 29.1, 29.2, 29.3, 29.4, and 29.6.  (They get mapped to different virtual channels, but I think they're all on that same multiplex.)

Now, what's weird is that I _sometimes_ get them on my myth box.  This afternoon I sat in front of the tv and tried to tune in to them lots of times.  Every once in a while (maybe 1 in 10) the tuner connects and then I can watch the channels just fine.  Most of the time however, I just get stalled at the screen trying to tune into them.  And just to re-iterate, when I bypass the myth box and just watch directly on my tv I never have any problems tuning into them.  :confused:

I'm hoping maybe this info helps someone help my diagnose the problem a bit more.

Thanks.

Are you sure the tuner is recording something else on that multiplex?

---

### Post by Quadari on 2012-05-04
> **nickrout said:**
> Are you sure the tuner is recording something else on that multiplex?

I'm not sure I understand the question.   With two or three random exceptions this afternoon, I can't get the tuner to lock in on anything on that multiplex, even though I know that those channels are being broadcast because my TV can watch them directly.

---

### Post by Quadari on 2012-05-06
OK - so my latest hypothesis is that there's some sort of driver issue going on.  Does that sound like a possibility to people?

I.e., the tuning card worked fine on all channels under 10.04 and 0.24.  Now I upgraded to 12.04 and 0.25 and suddenly the card won't tune to one multiplex.

My tuner card is a Hauppage HVR-1600.   I found a lot of pages talking about tuning problems with this card, but they all seem to be >2 years old, so I assume that all that has been resolved.  Just for kicks I just tried re-building and installing the V4L-DVB drivers, using the instructions here:
[http://linuxtv.org/wiki/index.php/How_to_Obtain,_Build_and_Install_V4L-DVB_Device_Drivers]("http://linuxtv.org/wiki/index.php/How_to_Obtain,_Build_and_Install_V4L-DVB_Device_Drivers")

But that hasn't seemed to have had any effect.

I suppose I could test this hypothesis by downgrading myself back to 0.24 and 10.04, but that seems like a giant pain, so I'm hoping to avoid it if anyone has any advice about the topic.

Thoughts?

Again, I'm not sure what logs are helpful for people to look at, so just let me know.  Here is a backend log to help get started.  First I tune to a channel that works (11.1), then try tuning to one that most of the time doesn't (9.1).

```

2012-05-06 22:43:56.538442 I  TVRec(1): SetChannel(11.1) -- begin
2012-05-06 22:43:56.538689 I  ChannelBase(1): Looking for startchannel '11.1' on input 'DVBInput'
2012-05-06 22:43:56.545145 I  ChannelBase(1): Found startchannel '11.1' on input 'DVBInput'
2012-05-06 22:43:56.548239 I  IsOnSameMultiplex? 62==54 -> 0
2012-05-06 22:43:56.548273 I  TVRec(1): HW Tuner: 1->1
2012-05-06 22:43:56.607131 E  DVBSH(/dev/dvb/adapter0/frontend0): Device EOF detected
2012-05-06 22:43:57.209923 I  DVBChan(1:/dev/dvb/adapter0/frontend0): Opening DVB channel
2012-05-06 22:43:57.209950 I  DTVChan(/dev/dvb/adapter0/frontend0): SetChannelByString(11.1): 
2012-05-06 22:43:57.216904 I  DVBChan(1:/dev/dvb/adapter0/frontend0): 747000000 qam_256 a auto auto a a auto a v fec: auto msys: UNDEFINED rolloff: 0.35
2012-05-06 22:43:57.217026 I  DVBChan(1:/dev/dvb/adapter0/frontend0): Old Params: 555000000 qam_256 a auto auto a a auto a v fec: auto msys: UNDEFINED rolloff: 0.35
                        DVBChan(1:/dev/dvb/adapter0/frontend0): New Params: 747000000 qam_256 a auto auto a a auto a v fec: auto msys: UNDEFINED rolloff: 0.35
2012-05-06 22:43:57.217051 I  DVBChan(1:/dev/dvb/adapter0/frontend0): Tune(): Tuning to 747000000Hz
2012-05-06 22:43:57.504965 I  DVBChan: wait_for_backend: Status: 
2012-05-06 22:43:57.505016 I  DVBChan(1:/dev/dvb/adapter0/frontend0): Tune(): Frequency tuning successful.
2012-05-06 22:43:57.505034 I  DTVChan(/dev/dvb/adapter0/frontend0): SetChannelByString(11.1): success
2012-05-06 22:43:57.515117 N  AutoExpire: CalcParams(): Max required Free Space: 2.0 GB w/freq: 14 min
2012-05-06 22:43:57.561738 I  DVBChan(1:/dev/dvb/adapter0/frontend0): Opening DVB channel
2012-05-06 22:43:57.564822 I  DVBSM(/dev/dvb/adapter0/frontend0): Can measure Signal Strength
2012-05-06 22:43:57.565728 I  DVBSM(/dev/dvb/adapter0/frontend0): Can measure S/N
2012-05-06 22:43:57.566712 I  DVBSM(/dev/dvb/adapter0/frontend0): Can measure Bit Error Rate
2012-05-06 22:43:57.567610 I  DVBSM(/dev/dvb/adapter0/frontend0): Can count Uncorrected Blocks
2012-05-06 22:43:57.567638 I  DVBSM(/dev/dvb/adapter0/frontend0): DVBSignalMonitor::ctor initial flags Seen() Match() Wait(Sig,SNR,BER,UB,)
2012-05-06 22:43:57.573040 I  DTVSM(/dev/dvb/adapter0/frontend0)::SetProgramNumber(2): 
2012-05-06 22:43:57.576768 I  TVRec(1): SetChannel(11.1) -- end
2012-05-06 22:43:57.913088 I  DVBSM(/dev/dvb/adapter0/frontend0): UpdateValues -- Signal Locked
2012-05-06 22:43:58.373126 E  DTVSM(/dev/dvb/adapter0/frontend0): Wrong PMT; pmt->pn(3) desired(2)
2012-05-06 22:43:58.373182 E  DTVSM(/dev/dvb/adapter0/frontend0): Wrong PMT; pmt->pn(4) desired(2)
2012-05-06 22:43:58.423489 E  DTVSM(/dev/dvb/adapter0/frontend0): Wrong PMT; pmt->pn(6) desired(2)
2012-05-06 22:43:58.424231 I  DVBSM(/dev/dvb/adapter0/frontend0): Stop() -- begin
2012-05-06 22:43:58.474259 E  DTVSM(/dev/dvb/adapter0/frontend0): Wrong PMT; pmt->pn(1) desired(2)
2012-05-06 22:43:59.122927 I  DVBSM(/dev/dvb/adapter0/frontend0): Stop() -- end
2012-05-06 22:43:59.139797 N  AutoExpire: CalcParams(): Max required Free Space: 2.0 GB w/freq: 14 min
2012-05-06 22:44:02.495253 I  RecBase(1:/dev/dvb/adapter0/frontend0): GetKeyframePositions(41,9223372036854775807,#1) out of 3
2012-05-06 22:44:03.272098 I  RecBase(1:/dev/dvb/adapter0/frontend0): GetKeyframePositions(107,9223372036854775807,#0) out of 4
2012-05-06 22:44:10.433288 I  TVRec(1): SetChannel(9.1) -- begin
2012-05-06 22:44:10.433461 I  ChannelBase(1): Looking for startchannel '9.1' on input 'DVBInput'
2012-05-06 22:44:10.439526 I  ChannelBase(1): Found startchannel '9.1' on input 'DVBInput'
2012-05-06 22:44:10.441812 I  IsOnSameMultiplex? 54==51 -> 0
2012-05-06 22:44:10.441847 I  TVRec(1): HW Tuner: 1->1
2012-05-06 22:44:10.443642 E  DVBSH(/dev/dvb/adapter0/frontend0): Device EOF detected
2012-05-06 22:44:11.046475 I  DVBChan(1:/dev/dvb/adapter0/frontend0): Opening DVB channel
2012-05-06 22:44:11.046504 I  DTVChan(/dev/dvb/adapter0/frontend0): SetChannelByString(9.1): 
2012-05-06 22:44:11.053403 I  DVBChan(1:/dev/dvb/adapter0/frontend0): 255012500 qam_256 a auto auto a a auto a v fec: auto msys: UNDEFINED rolloff: 0.35
2012-05-06 22:44:11.053572 I  DVBChan(1:/dev/dvb/adapter0/frontend0): Old Params: 747000000 qam_256 a auto auto a a auto a v fec: auto msys: UNDEFINED rolloff: 0.35
                        DVBChan(1:/dev/dvb/adapter0/frontend0): New Params: 255012500 qam_256 a auto auto a a auto a v fec: auto msys: UNDEFINED rolloff: 0.35
2012-05-06 22:44:11.053597 I  DVBChan(1:/dev/dvb/adapter0/frontend0): Tune(): Tuning to 255012500Hz
2012-05-06 22:44:11.340949 I  DVBChan: wait_for_backend: Status: 
2012-05-06 22:44:11.340998 I  DVBChan(1:/dev/dvb/adapter0/frontend0): Tune(): Frequency tuning successful.
2012-05-06 22:44:11.341015 I  DTVChan(/dev/dvb/adapter0/frontend0): SetChannelByString(9.1): success
2012-05-06 22:44:11.350893 N  AutoExpire: CalcParams(): Max required Free Space: 2.0 GB w/freq: 14 min
2012-05-06 22:44:11.404103 I  DVBChan(1:/dev/dvb/adapter0/frontend0): Opening DVB channel
2012-05-06 22:44:11.407348 I  DVBSM(/dev/dvb/adapter0/frontend0): Can measure Signal Strength
2012-05-06 22:44:11.408307 I  DVBSM(/dev/dvb/adapter0/frontend0): Can measure S/N
2012-05-06 22:44:11.409277 I  DVBSM(/dev/dvb/adapter0/frontend0): Can measure Bit Error Rate
2012-05-06 22:44:11.410256 I  DVBSM(/dev/dvb/adapter0/frontend0): Can count Uncorrected Blocks
2012-05-06 22:44:11.410285 I  DVBSM(/dev/dvb/adapter0/frontend0): DVBSignalMonitor::ctor initial flags Seen() Match() Wait(Sig,SNR,BER,UB,)
2012-05-06 22:44:11.415747 I  DTVSM(/dev/dvb/adapter0/frontend0)::SetProgramNumber(2): 
2012-05-06 22:44:11.417303 I  TVRec(1): SetChannel(9.1) -- end

```

Thanks.
Q

---

### Post by Lance Mountain on 2012-08-30
any updates on this, I am experiencing the same issue with a Hauppauge 2250 on Mythbuntu 12.04 (Myth .25+fixes)

---

### Post by klc5555 on 2012-08-31
I have no clue about the 2250, which I don't use, but the problem with the OP's HVR-1600 looks like signal swamping. 

The DVB amplification in the cx18 module included in 10.04 was terrible. Usually one needed a signal amp for DVB. By about 11.04, DVB amplification in the cx18 suddenly became very, very good. Far from requiring a sig amp, with the newer cx18 strong DVB signals would swamp the tuner, so it couldn't get a lock. I found that all my 1600s would require a signal attenuator before they could lock on the strongest DVB signals. I generally add an extra 2-way splitter ahead of the DVB input in order to cut the DVB signal a another 50% --a $2.00 Ace Hardware model, which seems to get the job done. All of my DVB channels thereafter became lockable again, Including the strongest ones. 

The 1600's analog signal strength requirements, on the other hand, remained the same, so that requiring attenuation only applied to the DVB input of the 1600.

---

### Post by DinghyMan on 2013-02-05
I had the same problem as Quadari when upgrading from 10.10 to 12.04. I cannot get all the channels I had before.

I have tried retuning with the two transmitters I can access, and with 167kHz offset, but nothing works to recapture a few channels.

Any guidance would be most appreciated.

Kind Regards,

---

### Post by nickrout on 2013-02-05
You shouldn't need to retune at all if you have properly backed up and restored your database.

---

