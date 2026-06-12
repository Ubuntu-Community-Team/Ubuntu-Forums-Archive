---
title: "Can commercial flagging leave you with little to watch?"
date: 2011-01-26
forum: Mythbuntu
---

### Post by NightStorm on 2011-01-26
Since upgrading to 10.0 w/.24 I keep getting these very short programs.  Looking at the logs it appears as though the program records and then commercial flagging gets an error and ruins the file.  Or at least that is what I'm speculating.  Here is what I see in the mythbackend.log:

2011-01-26 18:29:29.490 TVRec(7): ASK_RECORDING 7 29 0 0
2011-01-26 18:30:02.561 TVRec(7): Changing from None to RecordingOnly
2011-01-26 18:30:02.667 TVRec(7): HW Tuner: 7->7
2011-01-26 18:30:02.787 AutoExpire: CalcParams(): Max required Free Space: 3.0 GB w/freq: 14 min
2011-01-26 18:30:02.866 Started recording: "ABC World News With Diane Sawyer": channel 2051 on cardid 7, sourceid 2
2011-01-26 18:30:03.274 AutoExpire: CalcParams(): Max required Free Space: 3.0 GB w/freq: 14 min
2011-01-26 18:30:03.761 Updating status for "ABC World News With Diane Sawyer" on cardid 7 (Tuning => Recording)
2011-01-26 18:30:03.797 New DB connection, total: 5
2011-01-26 18:30:03.877 New DB connection, total: 6
2011-01-26 18:30:03.877 Connected to database 'mythconverg' at host: localhost
2011-01-26 18:30:03.933 Connected to database 'mythconverg' at host: localhost
2011-01-26 18:30:03.991 TVRec(7): rec->GetPathname(): '/var/lib/mythtv/recordings/2051_20110126183000.mpg'
2011-01-26 18:31:56.539 Reschedule requested for id -1.
2011-01-26 18:31:57.256 Scheduled 217 items in 0.7 = 0.07 match + 0.64 place
2011-01-26 18:37:22.867 Reschedule requested for id -1.
2011-01-26 18:37:23.522 Scheduled 217 items in 0.7 = 0.07 match + 0.58 place
2011-01-26 18:43:31.959 Reschedule requested for id -1.
2011-01-26 18:43:32.618 Scheduled 217 items in 0.7 = 0.08 match + 0.58 place
2011-01-26 18:44:04.135 AutoExpire: CalcParams(): Max required Free Space: 3.0 GB w/freq: 14 min
2011-01-26 18:48:10.325 Reschedule requested for id -1.
2011-01-26 18:48:10.994 Scheduled 217 items in 0.7 = 0.06 match + 0.60 place
2011-01-26 18:54:24.442 Reschedule requested for id -1.
2011-01-26 18:54:25.097 Scheduled 217 items in 0.7 = 0.07 match + 0.58 place
2011-01-26 18:58:04.765 AutoExpire: CalcParams(): Max required Free Space: 3.0 GB w/freq: 14 min
2011-01-26 18:59:01.602 Reschedule requested for id -1.
2011-01-26 18:59:02.285 Scheduled 217 items in 0.7 = 0.07 match + 0.61 place
2011-01-26 19:00:00.479 TVRec(7): Changing from RecordingOnly to None
2011-01-26 19:00:00.561 Updating status for "ABC World News With Diane Sawyer" on cardid 7 (Recording => Recorded)
2011-01-26 19:00:00.570 Finished recording ABC World News With Diane Sawyer: channel 2051
2011-01-26 19:00:00.816 Finished recording ABC World News With Diane Sawyer: channel 2051
2011-01-26 19:00:01.386 Reschedule requested for id 0.
2011-01-26 19:00:02.111 Scheduled 216 items in 0.7 = 0.10 match + 0.62 place
2011-01-26 19:00:02.168 MainServer::ANN Monitor
2011-01-26 19:00:02.338 adding: mythife as a client (events: 0)
2011-01-26 19:00:02.395 MainServer::ANN Monitor
2011-01-26 19:00:02.438 adding: mythife as a client (events: 1)
2011-01-26 19:00:42.304 JobQueue: Commercial Detection Starting for "ABC World News With Diane Sawyer" recorded from channel 2051 at 2011-01-26T18:30:00
2011-01-26 19:00:42.781 Using runtime prefix = /usr
2011-01-26 19:00:42.827 Using configuration directory = /home/mythtv/.mythtv
2011-01-26 19:00:42.872 Empty LocalHostName.
2011-01-26 19:00:42.916 Using localhost value of mythife
2011-01-26 19:00:42.990 New DB connection, total: 1
2011-01-26 19:00:43.046 Connected to database 'mythconverg' at host: localhost
2011-01-26 19:00:43.106 Closing DB connection named 'DBManager0'
2011-01-26 19:00:43.163 Connected to database 'mythconverg' at host: localhost
2011-01-26 19:00:43.209 Current locale EN_US
2011-01-26 19:00:43.263 Reading locale defaults from /usr/share/mythtv//locales/en_us.xml
2011-01-26 19:00:43.337 Loading en_us translation for module mythfrontend
2011-01-26 19:00:43.527 MythCoreContext: Connecting to backend server: 127.0.0.1:6543 (try 1 of 1)
2011-01-26 19:00:43.598 Using protocol version 63
2011-01-26 19:00:43.652 MainServer::ANN Monitor
2011-01-26 19:00:43.697 adding: mythife as a client (events: 0)
2011-01-26 19:00:43.753 MainServer::ANN Monitor
2011-01-26 19:00:43.797 adding: mythife as a client (events: 1)
2011-01-26 19:00:44.506 RingBuf(/var/lib/mythtv/recordings/2051_20110126183000.mpg): Waited 0.5 seconds for data 
                        to become available... 20624 < 32768
2011-01-26 19:00:45.064 RingBuf(/var/lib/mythtv/recordings/2051_20110126183000.mpg): Waited 1.0 seconds for data 
                        to become available... 20624 < 32768
2011-01-26 19:00:46.109 RingBuf(/var/lib/mythtv/recordings/2051_20110126183000.mpg): Waited 2.0 seconds for data 
                        to become available... 20624 < 32768
2011-01-26 19:00:46.362 AFD: Opened codec 0x7f7f8800f7d0, id(MPEG2VIDEO) type(Video)
2011-01-26 19:00:46.409 AFD: codec AC3 has 6 channels
2011-01-26 19:00:46.465 AFD: Opened codec 0x7f7f88003000, id(AC3) type(Audio)
2011-01-26 19:00:52.713 RingBuf(/var/lib/mythtv/recordings/2051_20110126183000.mpg): Waited 2.0 seconds for data 
                        to become available... 4508 < 32768
2011-01-26 19:00:52.939 [ac3 @ 0x7f7fa09095e0]incomplete frame
2011-01-26 19:00:55.433 ~MythContext waiting for threads to exit.
2011-01-26 19:00:56.197 MainServer::ANN Monitor
2011-01-26 19:00:56.265 adding: mythife as a client (events: 0)
2011-01-26 19:00:56.321 MainServer::ANN Monitor
2011-01-26 19:00:56.376 adding: mythife as a client (events: 1)
2011-01-26 19:02:06.419 Reschedule requested for id -1.
2011-01-26 19:02:07.124 Scheduled 216 items in 0.7 = 0.08 match + 0.62 place
2011-01-26 19:07:26.590 Reschedule requested for id -1.
2011-01-26 19:07:27.294 Scheduled 216 items in 0.7 = 0.09 match + 0.61 place
2011-01-26 19:12:05.223 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2011-01-26 19:12:08.687 Reschedule requested for id -1.
2011-01-26 19:12:09.387 Scheduled 216 items in 0.7 = 0.06 match + 0.63 place
2011-01-26 19:15:29.726 Reschedule requested for id -1.
2011-01-26 19:15:30.424 Scheduled 216 items in 0.7 = 0.06 match + 0.63 place
2011-01-26 19:17:01.540 MainServer::ANN Monitor
2011-01-26 19:17:01.657 adding: mythife as a client (events: 2)
2011-01-26 19:20:45.843 Reschedule requested for id -1.
2011-01-26 19:20:46.559 Scheduled 216 items in 0.7 = 0.09 match + 0.62 place
2011-01-26 19:22:42.485 Error: offset>181, pes length & current cannot be queried
2011-01-26 19:26:07.742 Reschedule requested for id -1.
2011-01-26 19:26:08.409 Scheduled 216 items in 0.7 = 0.07 match + 0.59 place
2011-01-26 19:27:05.874 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2011-01-26 19:31:50.657 Reschedule requested for id -1.
2011-01-26 19:31:51.325 Scheduled 214 items in 0.7 = 0.08 match + 0.58 place
2011-01-26 19:36:58.717 Reschedule requested for id -1.
2011-01-26 19:36:59.385 Scheduled 214 items in 0.7 = 0.07 match + 0.60 place
2011-01-26 19:42:06.336 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2011-01-26 19:42:17.942 Reschedule requested for id -1.
2011-01-26 19:42:18.624 Scheduled 214 items in 0.7 = 0.07 match + 0.61 place
2011-01-26 19:47:22.204 Reschedule requested for id -1.
2011-01-26 19:47:22.863 Scheduled 214 items in 0.7 = 0.06 match + 0.59 place
2011-01-26 19:52:18.994 Reschedule requested for id -1.
2011-01-26 19:52:19.671 Scheduled 214 items in 0.7 = 0.09 match + 0.58 place
2011-01-26 19:57:06.807 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2011-01-26 19:57:37.180 Reschedule requested for id -1.
2011-01-26 19:57:37.794 Scheduled 214 items in 0.6 = 0.08 match + 0.53 place
2011-01-26 20:01:03.529 ProgramInfo(2021_20110123223000.mpg), Error: GetPlaybackURL: '2021_20110123223000.mpg' should be local, but it can not be found.
2011-01-26 20:01:03.788 ProgramInfo(2021_20110123223000.mpg), Error: GetPlaybackURL: '2021_20110123223000.mpg' should be local, but it can not be found.
2011-01-26 20:01:03.878 ProgramInfo(2021_20110123223000.mpg), Error: GetPlaybackURL: '2021_20110123223000.mpg' should be local, but it can not be found.
2011-01-26 20:01:03.938 ProgramInfo(2021_20110123223000.mpg), Error: GetPlaybackURL: '2021_20110123223000.mpg' should be local, but it can not be found.
2011-01-26 20:01:04.272 MainServer::ANN Monitor
2011-01-26 20:01:04.318 adding: mythife as a client (events: 0)
2011-01-26 20:01:04.408 MainServer::ANN Monitor
2011-01-26 20:01:04.474 adding: mythife as a client (events: 1)
*** glibc detected *** /usr/bin/mythpreviewgen: free(): invalid next size (normal): 0x00007f97342f0f10 ***
======= Backtrace: =========
   (then lots of dump data)

It looks like the commercial flagging runs, gets an error in a ring buffer request and commercial flagging dies.  Sadly that leaves me with a drastically truncated .mpg file (only 45 seconds in this case).

It also appears that later what I presume to be the preview image generator corrupts the memory pool and dies.

Anyone knowledgeable at reading the log file able to tell me if I am I reading that right?

TIA,

      - Bruce

---

### Post by ian dobson on 2011-01-27
Hi,

What tuner are you using? It looks as if the tuner isn't able to lock onto the channel correctly or the signal strength is abit low.

Regards
Ian Dobson

---

### Post by NightStorm on 2011-01-27
> **ian dobson said:**
> What tuner are you using? It looks as if the tuner isn't able to lock onto the channel correctly or the signal strength is abit low.


Ian,

I've both a Hauppauge 2250 (hooked to Comcast cable) and an HDHomerun (OTA).  Both have 2 tuners.  I am not sure which of the 4 tuners this program came in on.

I only this past weekend tore down my 10.04 mythbuntu and replaced it with the 10.10 now on the system and ever since I've been getting recordings that last only one or two minutes.  Perhaps the new s/w is more sensitive to the tuners?

Could you teach me what it is in the log that show a tuner failure?

Thanks for the reply,

       - Bruce

---

### Post by ian dobson on 2011-01-28
Hi,

I use femon (part of the dvb-tools) to monitor thw signal strength from my dvb-c tuners. It a command line tool but the output is easy to understand:-

```

femon
FE: Philips TDA10023 DVB-C (DVBC)
status SCVYL | signal e1e1 | snr f5f5 | ber 00000000 | unc 00000000 | FE_HAS_LOCK
status SCVYL | signal e1e1 | snr f5f5 | ber 00000000 | unc 00000000 | FE_HAS_LOCK
status SCVYL | signal e1e1 | snr f5f5 | ber 00000000 | unc 00000000 | FE_HAS_LOCK
status SCVYL | signal e1e1 | snr f5f5 | ber 00000000 | unc 00000000 | FE_HAS_LOCK

```

signal is signal strength, snr signal to noise ratio, ber bit error rate, unc uncorrectable errors, FR-HAS_LOCK means the tuner is getting a valid signal.

Also look in dmesg to see if you've got any hard/soft errors comming from the tuner.

Regards
Ian Dobson

---

