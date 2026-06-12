---
title: "Error message &quot;fehler beim öffnen des puffers zum springen&quot;"
date: 2011-08-28
forum: Mythbuntu
---

### Post by natomb on 2011-08-28
Hi,

I am using Mythbuntu 11.04 and get the following error message when I try to change channel:

"fehler beim öffnen des puffers zum springen" 

The german error message as well as my attempt for english translation did not yield any usable result. In the mythfrontend.log I can see the following messages:

2011-08-28 18:04:56.312 We have a playbackURL(/Multimedia/Aufnahmen/29110_20110828180455.mpg) & cardtype(DUMMY)
2011-08-28 18:04:56.313 We have a RingBuffer
2011-08-28 18:04:56.314 TV Error: LiveTV not successfully started


On the mount "Multimedia" I have approx. 2 TB free space. It is a NFS mount with following mount options:

192.168.76.2:/Multimedia /Multimedia nfs defaults,acl 0 0


The export statement of the NFS mount is:

/Multimedia *(rw,async,no_subtree_check)



Any assistance is highly appreciated.
(There are approx. two dozen of problems I am currently fighting with in MythTv, ranging from unreliable DVB card detection, failing database logins on first three attempts, etc.)


Thanks
  Bjoern

---

### Post by ian dobson on 2011-08-31
Hi,

It looks as if one of your problems could well be that mythtv thinks your tuner card is type "DUMMY". This tuner type was added when the dev's decided that the backend MUST have atleast one tuner installed. So they created a dummy tuner that it's attached to any hardware.

So mythtv has a fit when it tries to open the dummy tuner for liveTV.

Regards
Ian Dobson

---

### Post by natomb on 2011-08-31
Hi Ian,


thank you for this tip. I checked my myth database and could not find any indication that I am using a dummy card. Attached are my "capturecard", "cardinput" and "mythlog" tables.

What I am wondering about is that in the mythlog table it says that cards 1 to 4 (actually, two Technisat Skystart HD2 DVB-S tuner cards) failed to init, but watching TV (without zapping) and recording (sometimes) works.

Are there any settings where I can make my system more "talkative"?


Regards
  Bjoern

---

### Post by ian dobson on 2011-08-31
Hi,

Hmmmm, ok, your mythtv tables look ok. The error about the cards not ititalising correctly looks bad.

What do you see in the kernel log (dmesg)? It sounds as if there is a driver problem.

Regards
Ian Dobson

---

### Post by agamotto on 2011-09-02
Your German error translates to 'error: jumping lines in buffers,' if my somewhat dodgy memory is up to par today...

---

### Post by realzippy on 2011-09-02
No,it means something like

"not enough buffer to switch (channels)"

---

### Post by ian dobson on 2011-09-03
Hi Guys,

A translation of the error is "error when opening the buffer to jump". So the frontnd couldn't access the ring buffer when trying to playback.

The OP should try increaing the ring buffer/timeouts, it could well be a timing/nfs interaction.

Regards
Ian Dobson (Englander living in Switzerland for 20 years)

---

### Post by natomb on 2011-09-03
Hi,

I have tried the following things in the meantime:

- Increasing ring buffer to maximum (96something MB) but without success
- Avoiding NFS but using local hard disk instead but without success
- Double-check my hardware with an old Windows setup running MediaPortal

Attached are also some of the latest logs:

[U]Frontend:
[/U]
```

2011-09-03 10:59:26.417 TV: Attempting to change from None to WatchingLiveTV
2011-09-03 10:59:26.417 MythCoreContext: Connecting to backend server: 127.0.0.1:6543 (try 1 of 1)
2011-09-03 10:59:26.418 Using protocol version 63
2011-09-03 10:59:26.477 Spawning LiveTV Recorder -- begin
2011-09-03 10:59:27.220 Spawning LiveTV Recorder -- end
2011-09-03 10:59:27.270 We have a playbackURL(/Multimedia/Aufnahmen/29007_20110903105926.mpg) & cardtype(DUMMY)
2011-09-03 10:59:27.271 We have a RingBuffer
2011-09-03 10:59:27.509 VideoOutputXv: XVideo Adaptor Name: 'ATI Radeon AVIVO Video'
2011-09-03 10:59:27.574 OSD: Base theme size: 1280x720
2011-09-03 10:59:27.574 OSD: Scaling factors: 0.5625x0.8
2011-09-03 10:59:27.660 OSD: Base theme size: 1280x720
2011-09-03 10:59:27.660 OSD: Scaling factors: 0.5625x0.8
2011-09-03 10:59:27.667 Player(0): Video sync method can't support double framerate (refresh rate too low for 2x deint)
2011-09-03 10:59:27.670 Player(0): Video timing method: USleep with busy wait
2011-09-03 10:59:27.671 TV: Changing from None to WatchingLiveTV
2011-09-03 10:59:27.671 TV: State is LiveTV & mctx == ctx
2011-09-03 10:59:27.673 TV: UpdateOSDInput done
2011-09-03 10:59:27.673 TV: UpdateLCD done
2011-09-03 10:59:27.673 TV: ITVRestart done
2011-09-03 10:59:27.850 VideoOutput: Created YV12 OSD.
2011-09-03 10:59:38.258 VideoOutputXv: XVideo Adaptor Name: 'ATI Radeon AVIVO Video'
2011-09-03 10:59:38.307 Player(0): Video sync method can't support double framerate (refresh rate too low for 2x deint)
2011-09-03 10:59:38.308 AFD: Opened codec 0x41a24d0, id(MPEG2VIDEO) type(Video)
2011-09-03 10:59:38.308 AFD: codec MP2 has 2 channels
2011-09-03 10:59:38.308 AFD: Opened codec 0x417a520, id(MP2) type(Audio)
2011-09-03 10:59:38.308 AFD: codec MP2 has 1 channels
2011-09-03 10:59:38.309 AFD: Opened codec 0x417ee80, id(MP2) type(Audio)
2011-09-03 10:59:38.309 AFD: codec AC3 has 2 channels
2011-09-03 10:59:38.309 AFD: Opened codec 0x417f500, id(AC3) type(Audio)
2011-09-03 10:59:38.309 AFD: Opened codec 0x1786830, id(DVB_SUBTITLE) type(Subtitle)
2011-09-03 10:59:38.388 AO: Opening audio device 'default' ch 2(2) sr 48000 sf signed 16 bit reenc 0
2011-09-03 10:59:38.405 AudioPlayer: Enabling Audio
2011-09-03 10:59:38.454 AFD: Resetting byte context eof (livetv 1 was eof 0)
2011-09-03 10:59:38.569 OSD: Base theme size: 1280x720
2011-09-03 10:59:38.569 OSD: Scaling factors: 0.5625x0.6
2011-09-03 10:59:45.013 OSD: Base theme size: 1280x720
2011-09-03 10:59:45.014 OSD: Scaling factors: 0.5625x0.8
2011-09-03 11:00:00.819 BrowseDispInfo()
2011-09-03 11:00:00.819 BrowseStart()
2011-09-03 11:00:00.855 browsechanid: 0 -> 29014
2011-09-03 11:00:02.003 BrowseEnd()
2011-09-03 11:00:02.558 RingBuf(/Multimedia/Aufnahmen/29014_20110903110002.mpg) Error: OpenFile(): File too small (0B).
2011-09-03 11:00:02.558 Player(0), Error: JumpToProgram's OpenFile failed (card type: DVB).
2011-09-03 11:00:02.558 
LiveTVChain has 4 entries
   DUMMY: 29007 (10:59:26 to 10:59:32)
     DVB: 29007 (10:59:32 to 11:00:01) discontinuous
     DVB: 29007 (11:00:00 to 11:00:02)
*    DVB: 29014 (11:00:02 to 11:25:00) discontinuous

2011-09-03 11:00:02.558 Player(0), Error: Unknown recorder error, exiting decoder
2011-09-03 11:00:02.612 msg: On known multiplex...
2011-09-03 11:00:02.626 TV: Attempting to change from WatchingLiveTV to None
2011-09-03 11:00:02.637 MythPainter: 18 images not yet de-allocated.
2011-09-03 11:00:03.111 TV: Changing from WatchingLiveTV to None
2011-09-03 11:00:03.120 TV: Attempting to change from None to WatchingLiveTV
2011-09-03 11:00:03.120 MythCoreContext: Connecting to backend server: 127.0.0.1:6543 (try 1 of 1)
2011-09-03 11:00:03.121 Using protocol version 63
2011-09-03 11:00:03.265 Spawning LiveTV Recorder -- begin
2011-09-03 11:00:04.052 Spawning LiveTV Recorder -- end
2011-09-03 11:00:04.065 We have a playbackURL(/Multimedia/Aufnahmen/29007_20110903110003.mpg) & cardtype(DUMMY)
2011-09-03 11:00:04.066 We have a RingBuffer
2011-09-03 11:00:04.067 TV Error: LiveTV not successfully started

```


[U]Backend:
[/U]
```

2011-09-03 10:59:26.482 TVRec(1): Changing from None to WatchingLiveTV
2011-09-03 10:59:26.526 TVRec(1): HW Tuner: 1->1
2011-09-03 10:59:26.555 LoadFromScheduler(): Error, called from backend.
2011-09-03 10:59:26.563 AutoExpire: CalcParams(): Max required Free Space: 3.0 GB w/freq: 14 min
2011-09-03 10:59:26.641 DVBChan(1:/dev/dvb/adapter0/frontend0) Warning: Unsupported fec_inner parameter.
2011-09-03 10:59:27.182 DVBSM(/dev/dvb/adapter0/frontend0), Warning: Cannot count Uncorrected Blocks
            eno: Operation not supported (95)
2011-09-03 10:59:32.326 Finished recording Geschichten vom Kaisermühlen-Blues: channel 29007
2011-09-03 10:59:32.386 scheduler: Finished recording: Geschichten vom KaisermÃ¼hlen-Blues: channel 29007
2011-09-03 10:59:32.429 LoadFromScheduler(): Error, called from backend.
2011-09-03 10:59:32.438 AutoExpire: CalcParams(): Max required Free Space: 3.0 GB w/freq: 14 min
2011-09-03 10:59:32.504 Finished recording Geschichten vom Kaisermühlen-Blues: channel 29007
2011-09-03 10:59:38.406 RecBase(1:/dev/dvb/adapter0/frontend0): GetKeyframePositions(109,9223372036854775807,#2) out of 12
2011-09-03 10:59:38.455 RecBase(1:/dev/dvb/adapter0/frontend0): GetKeyframePositions(109,9223372036854775807,#2) out of 12
2011-09-03 11:00:00.691 LoadFromScheduler(): Error, called from backend.
2011-09-03 11:00:00.705 AutoExpire: CalcParams(): Max required Free Space: 3.0 GB w/freq: 14 min
2011-09-03 11:00:00.796 Finished recording Geschichten vom Kaisermühlen-Blues: channel 29007
2011-09-03 11:00:01.342 TVRec(1): RingBufferChanged()
2011-09-03 11:00:01.503 MainServer::ANN Monitor
2011-09-03 11:00:01.566 adding: myth-wz as a client (events: 0)
2011-09-03 11:00:01.595 MainServer::ANN Monitor
2011-09-03 11:00:01.656 adding: myth-wz as a client (events: 1)
2011-09-03 11:00:02.033 TVRec(1): HW Tuner: 1->1
2011-09-03 11:00:02.100 DVBChan(1:/dev/dvb/adapter0/frontend0) Warning: Unsupported fec_inner parameter.
2011-09-03 11:00:02.159 LoadFromScheduler(): Error, called from backend.
2011-09-03 11:00:02.170 AutoExpire: CalcParams(): Max required Free Space: 3.0 GB w/freq: 14 min
2011-09-03 11:00:02.246 Finished recording Kaisermühlen-Blues (1/10) "Wie im ewigen Leben": channel 29007
2011-09-03 11:00:02.280 scheduler: Last message repeated 2 times: Finished recording: Geschichten vom KaisermÃ¼hlen-Blues: channel 29007
2011-09-03 11:00:02.308 scheduler: Finished recording: KaisermÃ¼hlen-Blues (1/10) "Wie im ewigen Leben": channel 29007
2011-09-03 11:00:02.460 TVRec(1): RingBufferChanged()
2011-09-03 11:00:02.685 TVRec(1): Changing from WatchingLiveTV to None
2011-09-03 11:00:03.268 TVRec(1): Changing from None to WatchingLiveTV
2011-09-03 11:00:03.308 TVRec(1): HW Tuner: 1->1
2011-09-03 11:00:03.404 LoadFromScheduler(): Error, called from backend.
2011-09-03 11:00:03.415 AutoExpire: CalcParams(): Max required Free Space: 3.0 GB w/freq: 14 min
2011-09-03 11:00:03.480 DVBChan(1:/dev/dvb/adapter0/frontend0) Warning: Unsupported fec_inner parameter.
2011-09-03 11:00:04.022 DVBSM(/dev/dvb/adapter0/frontend0), Warning: Cannot count Uncorrected Blocks
            eno: Operation not supported (95)
2011-09-03 11:00:04.073 TVRec(1): Changing from WatchingLiveTV to None
Error in my_thread_global_end(): 1 threads didn't exit

```


[U]And finally dmesg:
[/U]
```

[   32.385064] Mantis 0000:03:05.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[   32.388528] DVB: registering new adapter (Mantis DVB adapter)
[   33.313721] stb0899_attach: Attaching STB0899 
[   33.315716] stb6100_attach: Attaching STB6100 
[   33.318505] LNBx2x attached on addr=8
[   33.318511] DVB: registering adapter 0 frontend 0 (STB0899 Multistandard)...
[   33.318861] Mantis 0000:03:06.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[   33.319966] DVB: registering new adapter (Mantis DVB adapter)
[   34.251678] stb0899_attach: Attaching STB0899 
[   34.251763] stb6100_attach: Attaching STB6100 
[   34.252097] LNBx2x attached on addr=8
[   34.252101] DVB: registering adapter 1 frontend 0 (STB0899 Multistandard)...

```


Concluding, I can see the following things from the logs that look strange to me:

(1) it continues to talk about DUMMY card in the frontend while, as checked earlier, I do not have any card called "DUMMY"
(2) Just before or right after - it is difficult to tell on a microsecond basis - the frontend complains about file size of 0 Byte; yet at 11:00:04, it tells that it could acquire a RingBuffer, right before a screen appears telling me "Fehler beim Öffnen des Puffers zum springen" (error when opening the buffer to jump)
(3) There are numerous warnings in the backend log
(4) Even the backend complains that it could not init the DVB cards, dmesg looks fine to me


Thank you for your support.

---

### Post by ian dobson on 2011-09-03
Hi,

DO you have the option "Always stream from backend set"? try changing it from yes to no, or no to yes.

Are the tuners s2 compatible tuners? Also what version of mythtv are you running?

Regards
Ian Dobson

---

### Post by natomb on 2011-09-05
Hi,

I have tried to change the "Masterbackend übersteuern" setting, which I think is closest to "Always stream from master backend". Yet, still the same problem.

The tuners are Technisat SkyStar HD2 cards. I assume that they are compatible with DVB-S and DVB-S2, as this is what they receive in MediaPortal.

I have attached a screenshot with my installed myth-software as well as my dmesg .

---

### Post by natomb on 2011-09-06
Today I tried to reinstall, just in case I messed up the system at another place.

I installed from the 11.04 Mythbuntu CD, default settings. Then went to Mythbackend, installed my tuner cards (both), assigned them LNB, created the video group and scanned for channels. The rest I left unmodified.

Yet, the same problem remains.

Could it be a Mantis driver problem?

---

### Post by Ares Drake on 2012-11-20
I know this thread is quite old, but may still be found via google so people might still look for answers here. As no solutions is posted yet, I will post mine.

I got the same error and the problem were wrong entries in the mysql database.+

Login in to mysql via:
```
mysql --user root --password mythconverg
```

showed me this:
```

mysql> select mplexid,transportid,sistandard,networkid from dtv_multiplex;

+---------+-------------+------------+-----------+

| mplexid | transportid | sistandard | networkid |

+---------+-------------+------------+-----------+
|           1 |            1011 | dvb            |          NULL |
|           2 |            1107 | dvb            |          NULL |
|           3 |            1201 | dvb            |          NULL |
```

I could fix it via:
```

mysql> update dtv_multiplex set networkid = 1, sistandard = 'dvb';
mysql> quit
```

Maybe this helps someone

---

