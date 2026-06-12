---
title: "QAM recording error (Program #1 not found in PAT!)"
date: 2009-10-02
forum: Mythbuntu
---

### Post by belly917 on 2009-10-02
Hey everybody, I'm currently using 2 of my tuners to record QAM256 channels from my local cable company (TWC) all of the channels that I set up work great, except for 2, which both broadcast on the same frequency 633000000hz (a.k.a. channel 92)

When I scan using (dvb)scan I get the expected subchannels:
```
using '/dev/dvb/adapter1/frontend0' and '/dev/dvb/adapter1/demux0'
>>> tune to: 633000000:QAM_256
WARNING: filter timeout pid 0x1ffb
dumping lists (4 services)
[0002]:633000000:QAM_256:0:1007:2
[0004]:633000000:QAM_256:1016:1017:4
[0001]:633000000:QAM_256:1001:1002:1
[0003]:633000000:QAM_256:1011:1012:3
```

The channels I'm trying to tune are 92-1 (WNLODT) and 92-2 (Special channel for HD Buffalo Sabres home games).  I have confirmed these are the channels using my tv's digital tuner and this nice resource [http://www.silicondust.com/hdhomerun/lineup_web/US:14072#lineup_899756](http://www.silicondust.com/hdhomerun/lineup_web/US:14072#lineup_899756).  When I try to tune them using azap I get Full locks:
```
$ azap -c ~/channels-cable-trun.conf -a 1 WNLODT
using '/dev/dvb/adapter1/frontend0' and '/dev/dvb/adapter1/demux0'
tuning to 633000000 Hz
video pid 0x03e9, audio pid 0x03ea
status 00 | signal 4b11 | snr 0a43 | ber 00000000 | unc 0000ffff |
status 1f | signal d0d5 | snr 1c8d | ber 00000000 | unc 0000ffff | FE_HAS_LOCK
status 1f | signal d0c4 | snr 1c8a | ber 00000000 | unc 0000ffff | FE_HAS_LOCK
status 1f | signal cd9a | snr 1c6b | ber 00000000 | unc 0000ffff | FE_HAS_LOCK
status 1f | signal ce69 | snr 1c38 | ber 00000000 | unc 0000ffff | FE_HAS_LOCK
```

When I try to tune these channels in mythtv's watchtv mode, I get timeouts due to "partial locks". When I try to record these shows I get the following entries in my mythbackend logs: (please excuse the show, I don't watch that crap.. it was just a test)
```
2009-10-02 16:06:41.536 Started recording: The Tyra Banks Show: channel 3709 on cardid 2, sourceid 3
2009-10-02 16:06:41.663 Program #1 not found in PAT!
Program Association Table
 PSIP tableID(0x0) length(13) extension(0x28)
      version(1) current(1) section(0) last_section(0)
         tsid: 40
 programCount: 1
  program number     0 has PID 0x1ffc   data  0x 0 0x 0 0xff 0xfc

2009-10-02 16:06:41.667 But there is only one program in the PAT, so we'll just use it
2009-10-02 16:06:41.769 Program #0 not found in PAT!
Program Association Table
 PSIP tableID(0x0) length(25) extension(0x2365)
      version(29) current(1) section(0) last_section(0)
         tsid: 9061
 programCount: 4
  program number     2 has PID 0x 3ed   data  0x 0 0x 2 0xe3 0xed
  program number     4 has PID 0x 3f7   data  0x 0 0x 4 0xe3 0xf7
  program number     1 has PID 0x 3e8   data  0x 0 0x 1 0xe3 0xe8
  program number     3 has PID 0x 3f2   data  0x 0 0x 3 0xe3 0xf2

2009-10-02 16:06:41.816 TVRec(3): ASK_RECORDING 3 0 0 0
2009-10-02 16:06:41.877 Program #0 not found in PAT!
Program Association Table
 PSIP tableID(0x0) length(25) extension(0x2365)
      version(29) current(1) section(0) last_section(0)
         tsid: 9061
 programCount: 4
  program number     2 has PID 0x 3ed   data  0x 0 0x 2 0xe3 0xed
  program number     4 has PID 0x 3f7   data  0x 0 0x 4 0xe3 0xf7
  program number     1 has PID 0x 3e8   data  0x 0 0x 1 0xe3 0xe8
  program number     3 has PID 0x 3f2   data  0x 0 0x 3 0xe3 0xf2

2009-10-02 16:06:42.332 ProcessPAT: Program not found in PAT.
                        Rescan your transports.
2009-10-02 16:06:42.333 Desired program #0 not found in PAT.
                        Can Not create single program PAT.
2009-10-02 16:06:42.511 MainServer::HandleAnnounce Monitor
2009-10-02 16:06:42.516 adding: mythbox as a client (events: 0)
2009-10-02 16:06:42.916 ProgramInfo, Error: GetPlaybackURL: '3709_20091002160700.mpg' should be local, but it can not be found.
2009-10-02 16:06:43.022 ProgramInfo, Error: GetPlaybackURL: '3709_20091002160700.mpg' should be local, but it can not be found.
2009-10-02 16:06:43.025 ProgramInfo, Error: GetPlaybackURL: '3709_20091002160700.mpg' should be local, but it can not be found.
2009-10-02 16:06:43.028 ProgramInfo, Error: GetPlaybackURL: '3709_20091002160700.mpg' should be local, but it can not be found.
2009-10-02 16:06:43.030 Preview Error: Run() file not local: '/GetPlaybackURL/UNABLE/TO/FIND/LOCAL/FILE/ON/mythbox/3709_20091002160700.mpg'
2009-10-02 16:06:43.031 MainServer: Failed to make preview image.
2009-10-02 16:06:43.039 ProgramInfo, Error: GetPlaybackURL: '3709_20091002160700.mpg' should be local, but it can not be found.
2009-10-02 16:06:43.047 ProgramInfo, Error: GetPlaybackURL: '3709_20091002160700.mpg' should be local, but it can not be found.
2009-10-02 16:06:43.048 Preview Error: Run() file not local: '3709_20091002160700.mpg'
```

Notice that mythtv shows the first Program Association Table to only contain 1 program number 0, and then when it tries to tune that instead, the PAT shows all four program numbers that are supposed to be there, but by then it has been redirected to program #0 and can't find it.  So it doesn't create a video file (which can't be found later).

Does anyone have a clue what my issue is?  Is this a mythtv bug, is my cable company doing something funky to this frequency?

Finally, I have rescanned my channels recently as TWC changes their channel lineup frequently, and the last time was about a month ago.

---

### Post by belly917 on 2009-11-14
So, the problem just sort of went away.  I am now able to record these stations.

I'm still curious as to why this was a problem.

---

### Post by ian dobson on 2009-11-15
Hi,

MythTV has a table dtv_multiplex that stores the multiplex information for each channel. If there's a difference between the data in this table and the data comming over the cable you'll see this error.

Normally doing a channel scan fixes it. If you haven't done a channel scan then it could be that the cable provider doesn't send this information out all the time or the data way corrupt when you saw this error.

Regards
Ian Dobson

---

