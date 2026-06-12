---
title: "2 Tuner system keeps losing signal"
date: 2011-12-04
forum: Mythbuntu
---

### Post by rafe101 on 2011-12-04
I have had a single Hauppauge DVB PCI tuner in my backend/frontend for a couple of years. Everything worked fine with the tuner. A couple of weeks ago I added a USB tuner and they seem to fight over the signal. I don't know if that's the problem, but it seems to be an accurate description.
I will occasionally (sometimes frequently) lose the lock on a channel. Regardless of which tuner it was using, switching to the other one usually brings the channel in. Sometimes this happens when tuning to a new channel from another one. 
Does anyone have any suggestions or insight about this?

---

### Post by wyliecoyoteuk on 2011-12-04
How are they connected? 
If they are just connected via a splitter,the signal will be divided between them, and will be poorer and less stable as a result.
You should really have a powered splitter/amplifier.

---

### Post by rafe101 on 2011-12-04
I did think of that. I went to the store and could only find amplifiers that said they were for antennas, not satellite, but I figured a signal was a signal and bought one. It didn't work. So, rather than order an amp or go to a specialty store, I figured I'd ask if there could be any software or component issues causing this.
I'll add another tick (after my original one) to the signal strength tally.

---

### Post by nickrout on 2011-12-04
What do your logs say when the signal is lost (backend log specifically).

---

### Post by rafe101 on 2011-12-04
> **nickrout said:**
> What do your logs say when the signal is lost (backend log specifically).

I think this may include a time I was having some problems.
Thanks for the help.

```
2011-12-04 14:45:42.212 TVRec(4): Changing from None to WatchingLiveTV
2011-12-04 14:45:42.235 TVRec(4): HW Tuner: 4->4
2011-12-04 14:45:42.260 LoadFromScheduler(): Error, called from backend.
2011-12-04 14:45:42.267 AutoExpire: CalcParams(): Max required Free Space: 3.0 GB w/freq: 14 min
2011-12-04 14:45:42.311 DVBChan(4:/dev/dvb/adapter1/frontend0) Warning: Your frequency setting (12246000) is out of range. (min/max:950000/2150000)
2011-12-04 14:45:42.315 DVBSM(/dev/dvb/adapter1/frontend0), Warning: Cannot count Uncorrected Blocks
			eno: Operation not supported (95)
2011-12-04 14:45:42.484 Program #28486 not found in PAT!
Program Association Table
 PSIP tableID(0x0) length(177) extension(0x444)
      version(12) current(1) section(0) last_section(0)
         tsid: 1092
 programCount: 42
  program number     0 has PID 0x  10   data  0x 0 0x 0 0xe0 0x10
  program number 10100 has PID 0x  60   data  0x27 0x74 0xe0 0x60
  program number 10101 has PID 0x  61   data  0x27 0x75 0xe0 0x61
  program number 10102 has PID 0x  62   data  0x27 0x76 0xe0 0x62
  program number 10103 has PID 0x  63   data  0x27 0x77 0xe0 0x63
  program number 10104 has PID 0x  64   data  0x27 0x78 0xe0 0x64
  program number 10105 has PID 0x  65   data  0x27 0x79 0xe0 0x65
  program number 10106 has PID 0x  66   data  0x27 0x7a 0xe0 0x66
  program number 10107 has PID 0x  67   data  0x27 0x7b 0xe0 0x67
  program number 10108 has PID 0x  68   data  0x27 0x7c 0xe0 0x68
  program number 10109 has PID 0x  69   data  0x27 0x7d 0xe0 0x69
  program number 10110 has PID 0x  6a   data  0x27 0x7e 0xe0 0x6a
  program number 10111 has PID 0x  6b   data  0x27 0x7f 0xe0 0x6b
  program number 10112 has PID 0x  6c   data  0x27 0x80 0xe0 0x6c
  program number 10113 has PID 0x  6f   data  0x27 0x81 0xe0 0x6f
  program number 10114 has PID 0x  7f   data  0x27 0x82 0xe0 0x7f
  program number 10115 has PID 0x  70   data  0x27 0x83 0xe0 0x70
  program number 10116 has PID 0x  71   data  0x27 0x84 0xe0 0x71
  program number 10117 has PID 0x  72   data  0x27 0x85 0xe0 0x72
  program number 10118 has PID 0x  73   data  0x27 0x86 0xe0 0x73
  program number 10119 has PID 0x  74   data  0x27 0x87 0xe0 0x74
  program number 10120 has PID 0x  75   data  0x27 0x88 0xe0 0x75
  program number 10121 has PID 0x  76   data  0x27 0x89 0xe0 0x76
  program number 10122 has PID 0x  77   data  0x27 0x8a 0xe0 0x77
  program number 10123 has PID 0x  78   data  0x27 0x8b 0xe0 0x78
  program number 10124 has PID 0x  79   data  0x27 0x8c 0xe0 0x79
  program number 10125 has PID 0x  7a   data  0x27 0x8d 0xe0 0x7a
  program number 10126 has PID 0x  7b   data  0x27 0x8e 0xe0 0x7b
  program number 10142 has PID 0x  82   data  0x27 0x9e 0xe0 0x82
  program number 10150 has PID 0x  a0   data  0x27 0xa6 0xe0 0xa0
  program number 10152 has PID 0x  a2   data  0x27 0xa8 0xe0 0xa2
  program number 10153 has PID 0x  a3   data  0x27 0xa9 0xe0 0xa3
  program number 10154 has PID 0x  a4   data  0x27 0xaa 0xe0 0xa4
  program number 10155 has PID 0x  a5   data  0x27 0xab 0xe0 0xa5
  program number 10160 has PID 0x  aa   data  0x27 0xb0 0xe0 0xaa
  program number 10161 has PID 0x  ab   data  0x27 0xb1 0xe0 0xab
  program number 10164 has PID 0x  ae   data  0x27 0xb4 0xe0 0xae
  program number 10166 has PID 0x  b0   data  0x27 0xb6 0xe0 0xb0
  program number 10167 has PID 0x  b1   data  0x27 0xb7 0xe0 0xb1
  program number 10172 has PID 0x  b6   data  0x27 0xbc 0xe0 0xb6
  program number 10188 has PID 0x  98   data  0x27 0xcc 0xe0 0x98
  program number 10189 has PID 0x  99   data  0x27 0xcd 0xe0 0x99

2011-12-04 14:45:42.929 ProcessPAT: Program not found in PAT. 
			Rescan your transports.
2011-12-04 14:45:42.954 Desired program #28486 not found in PAT.
			Cannot create single program PAT.
2011-12-04 14:45:43.103 Finished recording Mythbusters: Die 25 besten Momente: channel 12101
2011-12-04 14:45:43.136 LoadFromScheduler(): Error, called from backend.
2011-12-04 14:45:43.139 AutoExpire: CalcParams(): Max required Free Space: 3.0 GB w/freq: 14 min
2011-12-04 14:45:43.172 Finished recording Mythbusters: Die 25 besten Momente: channel 12101
2011-12-04 14:45:45.441 RecBase(4:/dev/dvb/adapter1/frontend0): GetKeyframePositions(1,9223372036854775807,#3) out of 4
2011-12-04 14:45:45.534 RecBase(4:/dev/dvb/adapter1/frontend0): GetKeyframePositions(1,9223372036854775807,#3) out of 4
2011-12-04 14:46:02.557 TVRec(4): HW Tuner: 4->4
2011-12-04 14:46:02.591 LoadFromScheduler(): Error, called from backend.
2011-12-04 14:46:02.597 AutoExpire: CalcParams(): Max required Free Space: 3.0 GB w/freq: 14 min
2011-12-04 14:46:02.633 Finished recording Mythbusters: Die 25 besten Momente: channel 12101
2011-12-04 14:46:02.801 DVBChan(4:/dev/dvb/adapter1/frontend0) Warning: Your frequency setting (11953500) is out of range. (min/max:950000/2150000)
2011-12-04 14:46:02.806 DVBSM(/dev/dvb/adapter1/frontend0), Warning: Cannot count Uncorrected Blocks
			eno: Operation not supported (95)
2011-12-04 14:46:02.810 MainServer::ANN Monitor
2011-12-04 14:46:02.877 adding: htpc as a client (events: 0)
2011-12-04 14:46:02.903 MainServer::ANN Monitor
2011-12-04 14:46:02.930 Program #28486 not found in PAT!
Program Association Table
 PSIP tableID(0x0) length(45) extension(0x437)
      version(6) current(1) section(0) last_section(0)
         tsid: 1079
 programCount: 9
  program number 28006 has PID 0x  64   data  0x6d 0x66 0xe0 0x64
  program number 28011 has PID 0x 258   data  0x6d 0x6b 0xe2 0x58
  program number 28014 has PID 0x 28a   data  0x6d 0x6e 0xe2 0x8a
  program number 28016 has PID 0x 44c   data  0x6d 0x70 0xe4 0x4c
  program number 28007 has PID 0x  c8   data  0x6d 0x67 0xe0 0xc8
  program number 28008 has PID 0x 12c   data  0x6d 0x68 0xe1 0x2c
  program number 28017 has PID 0x 19b   data  0x6d 0x71 0xe1 0x9b
  program number 28012 has PID 0x 2bc   data  0x6d 0x6c 0xe2 0xbc
  program number 28013 has PID 0x 320   data  0x6d 0x6d 0xe3 0x20

2011-12-04 14:46:02.936 adding: htpc as a client (events: 1)
2011-12-04 14:46:03.303 DTVSM(/dev/dvb/adapter1/frontend0) Error: Wrong PMT; pmt->pn(28013) desired(28016)
2011-12-04 14:46:03.333 DTVSM(/dev/dvb/adapter1/frontend0) Error: Wrong PMT; pmt->pn(28012) desired(28016)
2011-12-04 14:46:03.358 DTVSM(/dev/dvb/adapter1/frontend0) Error: Wrong PMT; pmt->pn(28017) desired(28016)
2011-12-04 14:46:03.383 DTVSM(/dev/dvb/adapter1/frontend0) Error: Wrong PMT; pmt->pn(28007) desired(28016)
2011-12-04 14:46:03.412 DTVSM(/dev/dvb/adapter1/frontend0) Error: Wrong PMT; pmt->pn(28011) desired(28016)
2011-12-04 14:46:03.433 DTVSM(/dev/dvb/adapter1/frontend0) Error: Wrong PMT; pmt->pn(28006) desired(28016)
2011-12-04 14:46:03.458 DTVSM(/dev/dvb/adapter1/frontend0) Error: Wrong PMT; pmt->pn(28014) desired(28016)
2011-12-04 14:46:03.483 DTVSM(/dev/dvb/adapter1/frontend0) Error: Wrong PMT; pmt->pn(28008) desired(28016)
2011-12-04 14:46:03.775 Finished recording Fleetwood Mac "Live in Boston": channel 30016
2011-12-04 14:46:03.800 LoadFromScheduler(): Error, called from backend.
2011-12-04 14:46:03.806 AutoExpire: CalcParams(): Max required Free Space: 3.0 GB w/freq: 14 min
2011-12-04 14:46:03.853 Finished recording Fleetwood Mac "Live in Boston": channel 30016
2011-12-04 14:46:05.689 RecBase(4:/dev/dvb/adapter1/frontend0): GetKeyframePositions(13,9223372036854775807,#1) out of 2
2011-12-04 14:46:05.813 RecBase(4:/dev/dvb/adapter1/frontend0): GetKeyframePositions(13,9223372036854775807,#2) out of 3
2011-12-04 14:47:47.050 Reschedule requested for id -1.
2011-12-04 14:47:47.156 Scheduled 4 items in 0.1 = 0.04 match + 0.07 place
2011-12-04 14:48:34.479 Expiring 0 MB for 12101 at 2011-12-04T14:45:42 => "Mythbusters: Die 25 besten Momente"
2011-12-04 14:48:34.510 Expiring 3 MB for 12101 at 2011-12-04T14:45:43 => "Mythbusters: Die 25 besten Momente"
2011-12-04 14:48:34.535 Expiring 0 MB for 30016 at 2011-12-04T14:46:02 => "Fleetwood Mac":"Live in Boston"
2011-12-04 14:50:32.779 Reschedule requested for id -1.
2011-12-04 14:50:32.873 Scheduled 4 items in 0.1 = 0.03 match + 0.06 place
2011-12-04 14:50:33.026 DVBSM(/dev/dvb/adapter1/frontend0), Warning: Cannot count Uncorrected Blocks
			eno: Operation not supported (95)
2011-12-04 14:50:33.032 DVBChan(3:/dev/dvb/adapter1/frontend0) Error: SetChannelByString(370): Multiplex is not available
2011-12-04 14:50:33.121 SignalMonitor: channel change failed
2011-12-04 14:50:33.195 SignalMonitor: channel change failed
2011-12-04 14:50:33.270 SignalMonitor: channel change failed
2011-12-04 14:50:33.344 SignalMonitor: channel change failed
2011-12-04 14:50:33.420 SignalMonitor: channel change failed
2011-12-04 14:50:33.493 SignalMonitor: channel change failed
2011-12-04 14:50:33.568 SignalMonitor: channel change failed
2011-12-04 14:50:33.642 SignalMonitor: channel change failed
2011-12-04 14:50:33.719 SignalMonitor: channel change failed
2011-12-04 14:50:33.793 SignalMonitor: channel change failed
2011-12-04 14:50:33.868 SignalMonitor: channel change failed
2011-12-04 14:50:33.942 SignalMonitor: channel change failed
2011-12-04 14:50:34.017 SignalMonitor: channel change failed
2011-12-04 14:50:34.092 SignalMonitor: channel change failed
2011-12-04 14:50:34.574 AutoExpire: CalcParams(): Max required Free Space: 3.0 GB w/freq: 14 min
2011-12-04 14:51:20.458 SignalMonitor: channel change timed-out
2011-12-04 14:51:20.543 SignalMonitor: channel change timed-out
2011-12-04 14:51:20.617 SignalMonitor: channel change timed-out
2011-12-04 14:51:20.691 SignalMonitor: channel change timed-out
2011-12-04 14:51:20.767 SignalMonitor: channel change timed-out
2011-12-04 14:51:20.840 SignalMonitor: channel change timed-out
2011-12-04 14:51:20.915 SignalMonitor: channel change timed-out
2011-12-04 14:51:20.989 SignalMonitor: channel change timed-out
2011-12-04 14:51:21.080 SignalMonitor: channel change timed-out
2011-12-04 14:51:21.155 SignalMonitor: channel change timed-out
2011-12-04 14:51:21.230 SignalMonitor: channel change timed-out
2011-12-04 14:51:21.304 SignalMonitor: channel change timed-out
2011-12-04 14:51:21.379 SignalMonitor: channel change timed-out
2011-12-04 14:51:21.453 SignalMonitor: channel change timed-out
2011-12-04 14:51:21.528 SignalMonitor: channel change timed-out
2011-12-04 15:04:34.682 AutoExpire: CalcParams(): Max required Free Space: 3.0 GB w/freq: 14 min
2011-12-04 15:07:23.467 UPnpMedia: BuildMediaMap VIDEO scan starting in :/home/htpc/Videos/Content:
2011-12-04 15:07:23.963 UPnpMedia: BuildMediaMap Done. Found 1269 objects
2011-12-04 15:17:01.756 MainServer::ANN Monitor
2011-12-04 15:17:01.840 adding: htpc as a client (events: 2)
2011-12-04 15:18:34.804 AutoExpire: CalcParams(): Max required Free Space: 3.0 GB w/freq: 14 min
2011-12-04 15:30:00.008 LoadFromScheduler(): Error, called from backend.
2011-12-04 15:30:00.014 AutoExpire: CalcParams(): Max required Free Space: 3.0 GB w/freq: 14 min
```

---

### Post by wyliecoyoteuk on 2011-12-04
Sorry, did not realise it was a DVB-S card.
They have a 50V line carrier, and are a different frequency to Terrrestrial DVB.
You may still need an amp,satellite signals should be connected in series via paasthroughs, with a terminator at the end.

[http://www.smarthome.com/solution43.html](http://www.smarthome.com/solution43.html)

---

### Post by nickrout on 2011-12-04
> **rafe101 said:**
> I think this may include a time I was having some problems.
Thanks for the help.

```
2011-12-04 14:45:42.212 TVRec(4): Changing from None to WatchingLiveTV
2011-12-04 14:45:42.235 TVRec(4): HW Tuner: 4->4
2011-12-04 14:45:42.260 LoadFromScheduler(): Error, called from backend.
2011-12-04 14:45:42.267 AutoExpire: CalcParams(): Max required Free Space: 3.0 GB w/freq: 14 min
2011-12-04 14:45:42.311 DVBChan(4:/dev/dvb/adapter1/frontend0) Warning: Your frequency setting (12246000) is out of range. (min/max:950000/2150000)
```that one doesn't seem to be serious, i get them regularly and all works for me> ```

2011-12-04 14:45:42.315 DVBSM(/dev/dvb/adapter1/frontend0), Warning: Cannot count Uncorrected Blocks
			eno: Operation not supported (95)
2011-12-04 14:45:42.484 Program #28486 not found in PAT!
```Looks like reception errors. Are you SURE that you have the disecq setting right for BOTH cards? mythtv-setup screws up on this sometimes. Check, double check, triple check.> ```

Program Association Table
 PSIP tableID(0x0) length(177) extension(0x444)
      version(12) current(1) section(0) last_section(0)
         tsid: 1092
 programCount: 42
  program number     0 has PID 0x  10   data  0x 0 0x 0 0xe0 0x10
  program number 10100 has PID 0x  60   data  0x27 0x74 0xe0 0x60
  program number 10101 has PID 0x  61   data  0x27 0x75 0xe0 0x61
  program number 10102 has PID 0x  62   data  0x27 0x76 0xe0 0x62
  program number 10103 has PID 0x  63   data  0x27 0x77 0xe0 0x63
  program number 10104 has PID 0x  64   data  0x27 0x78 0xe0 0x64
  program number 10105 has PID 0x  65   data  0x27 0x79 0xe0 0x65
  program number 10106 has PID 0x  66   data  0x27 0x7a 0xe0 0x66
  program number 10107 has PID 0x  67   data  0x27 0x7b 0xe0 0x67
  program number 10108 has PID 0x  68   data  0x27 0x7c 0xe0 0x68
  program number 10109 has PID 0x  69   data  0x27 0x7d 0xe0 0x69
  program number 10110 has PID 0x  6a   data  0x27 0x7e 0xe0 0x6a
  program number 10111 has PID 0x  6b   data  0x27 0x7f 0xe0 0x6b
  program number 10112 has PID 0x  6c   data  0x27 0x80 0xe0 0x6c
  program number 10113 has PID 0x  6f   data  0x27 0x81 0xe0 0x6f
  program number 10114 has PID 0x  7f   data  0x27 0x82 0xe0 0x7f
  program number 10115 has PID 0x  70   data  0x27 0x83 0xe0 0x70
  program number 10116 has PID 0x  71   data  0x27 0x84 0xe0 0x71
  program number 10117 has PID 0x  72   data  0x27 0x85 0xe0 0x72
  program number 10118 has PID 0x  73   data  0x27 0x86 0xe0 0x73
  program number 10119 has PID 0x  74   data  0x27 0x87 0xe0 0x74
  program number 10120 has PID 0x  75   data  0x27 0x88 0xe0 0x75
  program number 10121 has PID 0x  76   data  0x27 0x89 0xe0 0x76
  program number 10122 has PID 0x  77   data  0x27 0x8a 0xe0 0x77
  program number 10123 has PID 0x  78   data  0x27 0x8b 0xe0 0x78
  program number 10124 has PID 0x  79   data  0x27 0x8c 0xe0 0x79
  program number 10125 has PID 0x  7a   data  0x27 0x8d 0xe0 0x7a
  program number 10126 has PID 0x  7b   data  0x27 0x8e 0xe0 0x7b
  program number 10142 has PID 0x  82   data  0x27 0x9e 0xe0 0x82
  program number 10150 has PID 0x  a0   data  0x27 0xa6 0xe0 0xa0
  program number 10152 has PID 0x  a2   data  0x27 0xa8 0xe0 0xa2
  program number 10153 has PID 0x  a3   data  0x27 0xa9 0xe0 0xa3
  program number 10154 has PID 0x  a4   data  0x27 0xaa 0xe0 0xa4
  program number 10155 has PID 0x  a5   data  0x27 0xab 0xe0 0xa5
  program number 10160 has PID 0x  aa   data  0x27 0xb0 0xe0 0xaa
  program number 10161 has PID 0x  ab   data  0x27 0xb1 0xe0 0xab
  program number 10164 has PID 0x  ae   data  0x27 0xb4 0xe0 0xae
  program number 10166 has PID 0x  b0   data  0x27 0xb6 0xe0 0xb0
  program number 10167 has PID 0x  b1   data  0x27 0xb7 0xe0 0xb1
  program number 10172 has PID 0x  b6   data  0x27 0xbc 0xe0 0xb6
  program number 10188 has PID 0x  98   data  0x27 0xcc 0xe0 0x98
  program number 10189 has PID 0x  99   data  0x27 0xcd 0xe0 0x99

2011-12-04 14:45:42.929 ProcessPAT: Program not found in PAT. 
			Rescan your transports.
2011-12-04 14:45:42.954 Desired program #28486 not found in PAT.
			Cannot create single program PAT.
2011-12-04 14:45:43.103 Finished recording Mythbusters: Die 25 besten Momente: channel 12101
2011-12-04 14:45:43.136 LoadFromScheduler(): Error, called from backend.
2011-12-04 14:45:43.139 AutoExpire: CalcParams(): Max required Free Space: 3.0 GB w/freq: 14 min
2011-12-04 14:45:43.172 Finished recording Mythbusters: Die 25 besten Momente: channel 12101
2011-12-04 14:45:45.441 RecBase(4:/dev/dvb/adapter1/frontend0): GetKeyframePositions(1,9223372036854775807,#3) out of 4
2011-12-04 14:45:45.534 RecBase(4:/dev/dvb/adapter1/frontend0): GetKeyframePositions(1,9223372036854775807,#3) out of 4
2011-12-04 14:46:02.557 TVRec(4): HW Tuner: 4->4
2011-12-04 14:46:02.591 LoadFromScheduler(): Error, called from backend.
2011-12-04 14:46:02.597 AutoExpire: CalcParams(): Max required Free Space: 3.0 GB w/freq: 14 min
2011-12-04 14:46:02.633 Finished recording Mythbusters: Die 25 besten Momente: channel 12101
2011-12-04 14:46:02.801 DVBChan(4:/dev/dvb/adapter1/frontend0) Warning: Your frequency setting (11953500) is out of range. (min/max:950000/2150000)
2011-12-04 14:46:02.806 DVBSM(/dev/dvb/adapter1/frontend0), Warning: Cannot count Uncorrected Blocks
			eno: Operation not supported (95)
2011-12-04 14:46:02.810 MainServer::ANN Monitor
2011-12-04 14:46:02.877 adding: htpc as a client (events: 0)
2011-12-04 14:46:02.903 MainServer::ANN Monitor
2011-12-04 14:46:02.930 Program #28486 not found in PAT!
Program Association Table
 PSIP tableID(0x0) length(45) extension(0x437)
      version(6) current(1) section(0) last_section(0)
         tsid: 1079
 programCount: 9
  program number 28006 has PID 0x  64   data  0x6d 0x66 0xe0 0x64
  program number 28011 has PID 0x 258   data  0x6d 0x6b 0xe2 0x58
  program number 28014 has PID 0x 28a   data  0x6d 0x6e 0xe2 0x8a
  program number 28016 has PID 0x 44c   data  0x6d 0x70 0xe4 0x4c
  program number 28007 has PID 0x  c8   data  0x6d 0x67 0xe0 0xc8
  program number 28008 has PID 0x 12c   data  0x6d 0x68 0xe1 0x2c
  program number 28017 has PID 0x 19b   data  0x6d 0x71 0xe1 0x9b
  program number 28012 has PID 0x 2bc   data  0x6d 0x6c 0xe2 0xbc
  program number 28013 has PID 0x 320   data  0x6d 0x6d 0xe3 0x20

2011-12-04 14:46:02.936 adding: htpc as a client (events: 1)
2011-12-04 14:46:03.303 DTVSM(/dev/dvb/adapter1/frontend0) Error: Wrong PMT; pmt->pn(28013) desired(28016)
2011-12-04 14:46:03.333 DTVSM(/dev/dvb/adapter1/frontend0) Error: Wrong PMT; pmt->pn(28012) desired(28016)
2011-12-04 14:46:03.358 DTVSM(/dev/dvb/adapter1/frontend0) Error: Wrong PMT; pmt->pn(28017) desired(28016)
2011-12-04 14:46:03.383 DTVSM(/dev/dvb/adapter1/frontend0) Error: Wrong PMT; pmt->pn(28007) desired(28016)
2011-12-04 14:46:03.412 DTVSM(/dev/dvb/adapter1/frontend0) Error: Wrong PMT; pmt->pn(28011) desired(28016)
2011-12-04 14:46:03.433 DTVSM(/dev/dvb/adapter1/frontend0) Error: Wrong PMT; pmt->pn(28006) desired(28016)
2011-12-04 14:46:03.458 DTVSM(/dev/dvb/adapter1/frontend0) Error: Wrong PMT; pmt->pn(28014) desired(28016)
2011-12-04 14:46:03.483 DTVSM(/dev/dvb/adapter1/frontend0) Error: Wrong PMT; pmt->pn(28008) desired(28016)
2011-12-04 14:46:03.775 Finished recording Fleetwood Mac "Live in Boston": channel 30016
2011-12-04 14:46:03.800 LoadFromScheduler(): Error, called from backend.
2011-12-04 14:46:03.806 AutoExpire: CalcParams(): Max required Free Space: 3.0 GB w/freq: 14 min
2011-12-04 14:46:03.853 Finished recording Fleetwood Mac "Live in Boston": channel 30016
2011-12-04 14:46:05.689 RecBase(4:/dev/dvb/adapter1/frontend0): GetKeyframePositions(13,9223372036854775807,#1) out of 2
2011-12-04 14:46:05.813 RecBase(4:/dev/dvb/adapter1/frontend0): GetKeyframePositions(13,9223372036854775807,#2) out of 3
2011-12-04 14:47:47.050 Reschedule requested for id -1.
2011-12-04 14:47:47.156 Scheduled 4 items in 0.1 = 0.04 match + 0.07 place
2011-12-04 14:48:34.479 Expiring 0 MB for 12101 at 2011-12-04T14:45:42 => "Mythbusters: Die 25 besten Momente"
2011-12-04 14:48:34.510 Expiring 3 MB for 12101 at 2011-12-04T14:45:43 => "Mythbusters: Die 25 besten Momente"
2011-12-04 14:48:34.535 Expiring 0 MB for 30016 at 2011-12-04T14:46:02 => "Fleetwood Mac":"Live in Boston"
2011-12-04 14:50:32.779 Reschedule requested for id -1.
2011-12-04 14:50:32.873 Scheduled 4 items in 0.1 = 0.03 match + 0.06 place
2011-12-04 14:50:33.026 DVBSM(/dev/dvb/adapter1/frontend0), Warning: Cannot count Uncorrected Blocks
			eno: Operation not supported (95)
2011-12-04 14:50:33.032 DVBChan(3:/dev/dvb/adapter1/frontend0) Error: SetChannelByString(370): Multiplex is not available
2011-12-04 14:50:33.121 SignalMonitor: channel change failed
2011-12-04 14:50:33.195 SignalMonitor: channel change failed
2011-12-04 14:50:33.270 SignalMonitor: channel change failed
2011-12-04 14:50:33.344 SignalMonitor: channel change failed
2011-12-04 14:50:33.420 SignalMonitor: channel change failed
2011-12-04 14:50:33.493 SignalMonitor: channel change failed
2011-12-04 14:50:33.568 SignalMonitor: channel change failed
2011-12-04 14:50:33.642 SignalMonitor: channel change failed
2011-12-04 14:50:33.719 SignalMonitor: channel change failed
2011-12-04 14:50:33.793 SignalMonitor: channel change failed
2011-12-04 14:50:33.868 SignalMonitor: channel change failed
2011-12-04 14:50:33.942 SignalMonitor: channel change failed
2011-12-04 14:50:34.017 SignalMonitor: channel change failed
2011-12-04 14:50:34.092 SignalMonitor: channel change failed
2011-12-04 14:50:34.574 AutoExpire: CalcParams(): Max required Free Space: 3.0 GB w/freq: 14 min
2011-12-04 14:51:20.458 SignalMonitor: channel change timed-out
2011-12-04 14:51:20.543 SignalMonitor: channel change timed-out
2011-12-04 14:51:20.617 SignalMonitor: channel change timed-out
2011-12-04 14:51:20.691 SignalMonitor: channel change timed-out
2011-12-04 14:51:20.767 SignalMonitor: channel change timed-out
2011-12-04 14:51:20.840 SignalMonitor: channel change timed-out
2011-12-04 14:51:20.915 SignalMonitor: channel change timed-out
2011-12-04 14:51:20.989 SignalMonitor: channel change timed-out
2011-12-04 14:51:21.080 SignalMonitor: channel change timed-out
2011-12-04 14:51:21.155 SignalMonitor: channel change timed-out
2011-12-04 14:51:21.230 SignalMonitor: channel change timed-out
2011-12-04 14:51:21.304 SignalMonitor: channel change timed-out
2011-12-04 14:51:21.379 SignalMonitor: channel change timed-out
2011-12-04 14:51:21.453 SignalMonitor: channel change timed-out
2011-12-04 14:51:21.528 SignalMonitor: channel change timed-out
2011-12-04 15:04:34.682 AutoExpire: CalcParams(): Max required Free Space: 3.0 GB w/freq: 14 min
2011-12-04 15:07:23.467 UPnpMedia: BuildMediaMap VIDEO scan starting in :/home/htpc/Videos/Content:
2011-12-04 15:07:23.963 UPnpMedia: BuildMediaMap Done. Found 1269 objects
2011-12-04 15:17:01.756 MainServer::ANN Monitor
2011-12-04 15:17:01.840 adding: htpc as a client (events: 2)
2011-12-04 15:18:34.804 AutoExpire: CalcParams(): Max required Free Space: 3.0 GB w/freq: 14 min
2011-12-04 15:30:00.008 LoadFromScheduler(): Error, called from backend.
2011-12-04 15:30:00.014 AutoExpire: CalcParams(): Max required Free Space: 3.0 GB w/freq: 14 min
```

---

### Post by rafe101 on 2011-12-06
I guess I really can't be sure that I have the right DISEQC settings as I just picked "Universal Western Europe". I'm picking up the normal German stations on the Astra cluster and the dish isn't mine. It's on the rental house. I have no idea about its specifics.

---

### Post by nickrout on 2011-12-06
Have you got it set right for BOTH tuners?

---

### Post by rafe101 on 2011-12-07
Both are set to "Universal (Europe)". However, I don't know anything about the LNB on the dish, so I hope it's the right setting.

---

### Post by rafe101 on 2011-12-09
I am inclined to believe this is due to signal strength, but I just can't confirm it because I can't get an amplifier to work.

I bought an amp that says it is specifically for satellite, plug it all in and get no signal lock at all. I've played with the adjustment screw—up and down—but nothing. While it was trying to tune in a channel, I started to unscrew the the cables and just hook everything up directly through the splitter and as soon as the connector touched the post of the splitter I got a signal lock.

Every time I plug an amplifier into the line it kills the signal completely. I just don't know what to do.

---

### Post by PhilWig on 2012-08-26
I understood that each tuner needed its own LNB and downlead.
Phil

---

