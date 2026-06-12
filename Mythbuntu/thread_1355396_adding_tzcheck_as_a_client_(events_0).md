---
title: "adding: tzcheck as a client (events: 0)"
date: 2009-12-14
forum: Mythbuntu
---

### Post by larsolav on 2009-12-14
Had a weird situation just now. My recording of "2 1/2 Men" did not work this evening. when I selected it to play I got a message about it not being available yet or something. Checked backend log:

> 2009-12-14 06:27:54.055 MainServer::ANN Monitor
2009-12-14 06:27:54.102 adding: tzcheck as a client (events: 0)
2009-12-14 06:27:54.785 MainServer::ANN Monitor
2009-12-14 06:27:54.845 adding: tzcheck as a client (events: 0)
2009-12-14 06:27:55.547 MainServer::ANN Monitor
2009-12-14 06:27:55.588 adding: tzcheck as a client (events: 0)
2009-12-14 06:27:56.261 MainServer::ANN Monitor
2009-12-14 06:27:56.322 adding: tzcheck as a client (events: 0)
2009-12-14 06:27:56.988 MainServer::ANN Monitor
2009-12-14 06:27:57.034 adding: tzcheck as a client (events: 0)
2009-12-14 06:27:57.729 MainServer::ANN Monitor
....
009-12-14 20:55:25.074 adding: tzcheck as a client (events: 0)
2009-12-14 20:55:25.770 MainServer::ANN Monitor
2009-12-14 20:55:25.827 adding: tzcheck as a client (events: 0)
2009-12-14 20:55:26.548 MainServer::ANN Monitor
2009-12-14 20:55:26.599 adding: tzcheck as a client (events: 0)
2009-12-14 20:55:27.296 MainServer::ANN Monitor
2009-12-14 20:55:27.352 adding: tzcheck as a client (events: 0)
2009-12-14 20:55:27.904 MainServer::ANN Monitor

(this repeated basically filling up my backend....
Repaired the tables, and checked the log again, same text was still appearing after restart...
Rebooted. Set to record another program. That program records and I can play it just fine, but the weird message is still there:
> 2009-12-14 20:55:45.951 MainServer::ANN Monitor
2009-12-14 20:55:46.001 adding: tzcheck as a client (events: 0)
2009-12-14 20:55:46.748 MainServer::ANN Monitor
2009-12-14 20:55:46.805 adding: tzcheck as a client (events: 0)
2009-12-14 20:55:47.033 Reschedule requested for id 29.
2009-12-14 20:55:47.647 MainServer::ANN Monitor
2009-12-14 20:55:47.698 adding: tzcheck as a client (events: 0)
2009-12-14 20:55:47.889 Scheduled 147 items in 0.9 = 0.07 match + 0.78 place
2009-12-14 20:55:47.928 TVRec(1): ASK_RECORDING 1 0 0 0
2009-12-14 20:55:48.082 TVRec(1): Changing from None to Watching RecordingOnly
2009-12-14 20:55:48.218 TVRec(4): ASK_RECORDING 4 0 0 0
2009-12-14 20:55:48.223 TVRec(1): HW Tuner: 1->1
2009-12-14 20:55:48.374 MainServer::ANN Monitor
2009-12-14 20:55:48.446 adding: tzcheck as a client (events: 0)
2009-12-14 20:55:48.502 AutoExpire: CalcParams(): Max required Free Space: 3.0 GB w/freq: 15 min
2009-12-14 20:55:48.640 Started recording: The Big Bang Theory "The Maternal Congruence": channel 1111 on cardid 1, sourceid 1
2009-12-14 20:55:49.161 MainServer::ANN Monitor
2009-12-14 20:55:49.210 adding: tzcheck as a client (events: 0)
2009-12-14 20:55:49.915 MainServer::ANN Monitor
2009-12-14 20:55:49.974 adding: tzcheck as a client (events: 0)
2009-12-14 20:55:50.696 MainServer::ANN Monitor


Anyone got a clue. The mighty google did not me help really.
Thanks!

---

### Post by larsolav on 2009-12-15
I found the first instance of this in the log archives:
> 2009-12-07 13:00:22.838 Connected to database 'mythconverg' at host: localhost
2009-12-07 13:00:22.910 MythContext: Connecting to backend server: 192.168.1.71:6543 (try 1 of 1)
2009-12-07 13:00:22.973 Using protocol version 50
2009-12-07 13:00:23.023 MainServer::ANN Monitor
2009-12-07 13:00:23.084 adding: mythbox as a client (events: 0)
2009-12-07 13:00:23.135 MainServer::ANN Monitor
2009-12-07 13:00:23.196 adding: mythbox as a client (events: 1)
2009-12-07 13:00:24.281 RingBuf(/var/lib/mythtv/recordings/1021_20091207120000.mpg): Waited 1.0 seconds for data to become available...
2009-12-07 13:00:25.357 RingBuf(/var/lib/mythtv/recordings/1021_20091207120000.mpg): Waited 2.0 seconds for data to become available...
2009-12-07 13:00:25.801 AFD: Opened codec 0x18d3c30, id(MPEG2VIDEO) type(Video)
2009-12-07 13:00:25.852 AFD: codec AC3 has 6 channels
2009-12-07 13:00:25.904 AFD: Opened codec 0x18f8f20, id(AC3) type(Audio)
2009-12-07 13:00:25.975 AFD: codec AC3 has 2 channels
2009-12-07 13:00:26.036 AFD: Opened codec 0x18f9350, id(AC3) type(Audio)
CC length(19) seq_num(3) 0xca 0x31 0x98 0x3b 0xe3 0x0 0x62 0x1f 0x10 0x90 0x5 0x3 0x91 0x3f 0x0 0x3f 0x92 0x2 
CC length(19) seq_num(2) 0x8a 0x31 0x98 0x3b 0xe3 0x0 0x62 0x1f 0x10 0x90 0x5 0x3 0x91 0x3f 0x0 0x3f 0x92 0x2 
CC length(19) seq_num(2) 0x8a 0x31 0x98 0x3b 0xe3 0x0 0x62 0x1f 0x10 0x90 0x5 0x3 0x91 0x3f 0x0 0x3f 0x92 0x2 
CC length(19) seq_num(1) 0x4a 0x31 0x98 0x3b 0xe3 0x0 0x62 0x1f 0x10 0x90 0x5 0x3 0x91 0x3f 0x0 0x3f 0x92 0x2 
CC length(19) seq_num(2) 0x8a 0x31 0x98 0x3b 0xe3 0x0 0x62 0x1f 0x10 0x90 0x5 0x3 0x91 0x3f 0x0 0x3f 0x92 0x2 
2009-12-07 13:10:11.624 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2009-12-07 13:10:11.737 UPnpMedia: BuildMediaMap Done. Found 94 objects
2009-12-07 13:17:03.042 MainServer::ANN Monitor
2009-12-07 13:17:03.092 adding: mythbox as a client (events: 0)
2009-12-07 13:20:15.849 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
[B]2009-12-07 13:20:16.484 MainServer::ANN Monitor
2009-12-07 13:20:16.523 adding: tzcheck as a client (events: 0)[/B]

---

