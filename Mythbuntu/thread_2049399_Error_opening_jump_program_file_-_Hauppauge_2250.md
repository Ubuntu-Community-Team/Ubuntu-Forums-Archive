---
title: "Error opening jump program file - Hauppauge 2250"
date: 2012-08-28
forum: Mythbuntu
---

### Post by Lance Mountain on 2012-08-28
changed subject from Error opening jump program file - Hauppauge 2250 as I narrowed down the issue below

-------------
I am banging my head against the wall trying to figure this out. I have searched everywhere and tried many different fixes.

Problem: When changing channels in live tv I get the "Error opening jump program file" on the frontend.

Running MythBuntu 12.04, MythTV .25 w/Hauppauge Win-TV 2250 on a FE/BE single machine.

The frontend log shows "Could not find codec parameters", "Coudn't open decoder for..." & "Jump to program failed"

Backend log shows " Error, socket went unconnected. #012#011#011#011 we wrote 0 of 9 bytes with 1 errors..."

My problem seems similar to ticket [#9177]("http://code.mythtv.org/trac/ticket/9177") but I don't see a solution in there and it seems to be with older versions of mythtv .24-fixes when I'm running .25 Everything I have found on this forum refers to MythBuntu 10 or less so shouldn't it be ok in 12.04?

Here's a few of the troubleshooting steps I have tried:
Turned off all EIT discovery & rescanned, only scanned digital channels, made sure firmware for the hauppauge 2250 was up to date, and set max recording on each tuner to 1. Each time I made a change I deleted the video sources and re-setup, along with new input connections. But I still get the same errors every time.

---

### Post by nickrout on 2012-08-28
> **Lance Mountain said:**
> I am banging my head against the wall trying to figure this out. I have searched everywhere and tried many different fixes.

Problem: When changing channels in live tv I get the "Error opening jump program file" on the frontend.

Running MythBuntu 12.04, MythTV .25 w/Hauppauge Win-TV 2250 on a FE/BE single machine.

The frontend log shows "Could not find codec parameters", "Coudn't open decoder for..." & "Jump to program failed"

Backend log shows " Error, socket went unconnected. #012#011#011#011 we wrote 0 of 9 bytes with 1 errors..."

My problem seems similar to ticket [#9177]("http://code.mythtv.org/trac/ticket/9177") but I don't see a solution in there and it seems to be with older versions of mythtv .24-fixes when I'm running .25 Everything I have found on this forum refers to MythBuntu 10 or less so shouldn't it be ok in 12.04?

Here's a few of the troubleshooting steps I have tried:
Turned off all EIT discovery & rescanned, only scanned digital channels, made sure firmware for the hauppauge 2250 was up to date, and set max recording on each tuner to 1. Each time I made a change I deleted the video sources and re-setup, along with new input connections. But I still get the same errors every time.

Exactly what version of mythtv are you using, ```
dpkg -l mythtv-frontend
```

---

### Post by Lance Mountain on 2012-08-28
> **nickrout said:**
> Exactly what version of mythtv are you using, ```
dpkg -l mythtv-frontend
```

Thanks for the command, here are the results:

Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                                      Version                                   Description
+++-=========================================-=========================================-==================================================================================================
ii  mythtv-frontend                           2:0.25.2+fixes.20120802.46cab93-0ubuntu1  A personal video recorder application (client)

---

### Post by Lance Mountain on 2012-08-28
> **Lance Mountain said:**
> Thanks for the command, here are the results:

Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                                      Version                                   Description
+++-=========================================-=========================================-==================================================================================================
ii  mythtv-frontend                           2:0.25.2+fixes.20120802.46cab93-0ubuntu1  A personal video recorder application (client)

I ran an update check and got some new updates, now the problem didn't happen until I got to a particular channel. I haven't gotten to the point of understanding channel mappings yet so I don't even know if it's a channel I am supposed to get, maybe that's the problem?

Here's my updated version info with more details from the log files:
ii  mythtv-frontend 2:0.25.2+fixes.20120828.d519276-0ubuntu0m 

Front End Log
```

Forcing decode extra audio option on (Video method requires it).
Aug 28 14:58:59 Mythos mythfrontend[1886]: E CoreContext avformatdecoder.cpp:960 (OpenFile) AFD: Could not find codec parameters. file was "/var/lib/mythtv/livetv/64351_20120828145858.mpg".
Aug 28 14:58:59 Mythos mythfrontend[1886]: E CoreContext mythplayer.cpp:969 (OpenFile) Couldn't open decoder for: /var/lib/mythtv/livetv/64351_20120828145858.mpg
Aug 28 14:58:59 Mythos mythfrontend[1886]: E CoreContext mythplayer.cpp:2624 (JumpToProgram) Player(0): JumpToProgram failed.
Aug 28 14:58:59 Mythos mythfrontend[1886]: E CoreContext mythplayer.cpp:2816 (EventLoop) Player(0): Unknown recorder error, exiting decoder

```Backend Log
```

Aug 28 14:58:59 Mythos mythbackend[1473]: I TVRecEvent tv_rec.cpp:1029 (HandleStateChange) TVRec(1): Changing from WatchingLiveTV to None
Aug 28 14:58:59 Mythos mythbackend[1473]: E DVBRead dvbstreamhandler.cpp:214 (RunTS) DVBSH(/dev/dvb/adapter0/frontend0): Device EOF detected
Aug 28 14:58:59 Mythos mythbackend[1473]: I TVRecEvent tv_rec.cpp:816 (FinishedRecording) TVRec(1): FinishedRecording(64351_2012-08-28T14:58:58) damaged recq:<RecordingQuality overall_score="0" key="64351_2012-08-28T14:58:58" countinuity_error_count="0" packet_count="45">#012    <Gap start="2012-08-28T14:58:59" end="2012-08-28T15:00:00" duration="61" />#012</RecordingQuality>
Aug 28 14:58:59 Mythos mythbackend[1473]: I ProcessRequest mainserver.cpp:1360 (HandleAnnounce) MainServer::ANN Playback
Aug 28 14:58:59 Mythos mythbackend[1473]: I ProcessRequest mainserver.cpp:1362 (HandleAnnounce) adding: Mythos as a client (events: 0)
Aug 28 14:58:59 Mythos mythbackend[1473]: I TVRecEvent tv_rec.cpp:1029 (HandleStateChange) TVRec(1): Changing from None to WatchingLiveTV
Aug 28 14:58:59 Mythos mythbackend[1473]: I TVRecEvent tv_rec.cpp:3495 (TuningCheckForHWChange) TVRec(1): HW Tuner: 1->1
Aug 28 14:58:59 Mythos mythbackend[1473]: N CoreContext autoexpire.cpp:263 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 3.0 GB w/freq: 14 min
Aug 28 14:58:59 Mythos mythbackend[1473]: I TVRecEvent tv_rec.cpp:1029 (HandleStateChange) TVRec(1): Changing from WatchingLiveTV to None
Aug 28 14:59:00 Mythos mythbackend[1473]: W ProcessRequest mainserver.cpp:5801 (connectionClosed) MainServer: Unknown socket closing MythSocket(0x92b6f48)
Aug 28 14:59:00 Mythos mythbackend[1473]: E ProcessRequest mythsocket.cpp:358 (writeStringList) MythSocket(92b6f48:-1): writeStringList: Error, socket went unconnected.#012#011#011#011We wrote 0 of 9 bytes with 1 errors#012#011#011#011starts with: 1       1

```

---

### Post by Lance Mountain on 2012-08-30
Ok by changing the DVB tuning delay to 5ms I am able to avoid a majority of the jump failure errors. Now instead I just get the no lock message on the channel.

So this leads me to believe I either do not have the Hauppauge setup properly or I am not supposed to get certain channels. 

If I look at SiliconDust site and change the provider to the first Cox Cable, I see all the channels I actually am getting properly via the Hauppage 2250. So are these the only channels I should get?

I am confused because if I hook a tv with a ClearQAM tuner directly to the cable I will get more channels like ESPN, Bravo, Fox Sports. These other channels are also listed in Schedules Direct lineup for Cox Cable (basic) not even digital cable.

So have I setup my 2250 wrong so that it's not picking up these other cable channels? Or is that a limitation of this tuner card? I have connected the tuner directly to the cable too, to eliminate any splitters. I noticed the subtype of the card is ATSC, is that causing a problem?

---

