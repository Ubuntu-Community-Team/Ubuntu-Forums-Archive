---
title: "DVB EIT scanner dies during recording"
date: 2008-09-27
forum: Mythbuntu
---

### Post by ian dobson on 2008-09-27
Hi,

I'm running mythtv with 2 DVB-C tuner cards setup with multirec (2 recordings per card). The tuner cards are numbered 3,4 and 5,6. When I record a program from one of the cards is see the following error sometimes:-

2008-09-27 13:27:18.007 EITScanner (5): Added 18 EIT Events
2008-09-27 13:27:18.352 TVRec(5) Error: Failed to set channel to 30417. Reverting to kState_None
2008-09-27 13:27:18.420 EITScanner (5): Now looking for EIT data on multiplex of channel 30417

And the EIT scanner for that card stops scanning for EPG. If the scanners on both cards die I don't get any more EPG and have to restart the backend to restart the process.

Backend is running  0.21.0+fixes18403-0ubuntu0+

Regards
Ian Dobson

---

### Post by ian dobson on 2008-09-28
I also see this sometimes when I watch liveTV

2008-09-28 10:03:24.316 DTVSM(0) Error: Wrong PMT; pmt->pn(31210) desired(30413)
2008-09-28 10:03:24.531 Program #30413 not found in PAT!
Program Association Table
 PSIP tableID(0x0) length(57) extension(0x25f)
      version(4) current(1) section(0) last_section(0)
         tsid: 607
 programCount: 12
  program number     0 has PID 0x  10   data  0x 0 0x 0 0xe0 0x10
  program number 31201 has PID 0x  64   data  0x79 0xe1 0xe0 0x64
  program number 31202 has PID 0x  6e   data  0x79 0xe2 0xe0 0x6e
  program number 31203 has PID 0x  d2   data  0x79 0xe3 0xe0 0xd2
  program number 31204 has PID 0x 506   data  0x79 0xe4 0xe5 0x 6
  program number 31205 has PID 0x 136   data  0x79 0xe5 0xe1 0x36
  program number 31206 has PID 0x 1fe   data  0x79 0xe6 0xe1 0xfe
  program number 31207 has PID 0x 262   data  0x79 0xe7 0xe2 0x62
  program number 31208 has PID 0x  f4   data  0x79 0xe8 0xe0 0xf4
  program number 31210 has PID 0x 258   data  0x79 0xea 0xe2 0x58
  program number 31211 has PID 0x  25   data  0x79 0xeb 0xe0 0x25
  program number 34002 has PID 0x 2fa   data  0x84 0xd2 0xe2 0xfa

2008-09-28 10:03:24.976 EITHelper: Added 1 events
2008-09-28 10:03:25.403 AutoExpire: CalcParams(): Max required Free Space: 52.0 GB w/freq: 15 min
2008-09-28 10:03:25.481 Using runtime prefix = /usr
2008-09-28 10:03:25.488 Empty LocalHostName.
2008-09-28 10:03:25.504 Using localhost value of alpha2
2008-09-28 10:03:25.510 New DB connection, total: 1
2008-09-28 10:03:25.516 Connected to database 'mythconverg' at host: localhost
2008-09-28 10:03:25.517 Closing DB connection named 'DBManager0'
2008-09-28 10:03:25.518 Connected to database 'mythconverg' at host: localhost
2008-09-28 10:03:25.521 New DB connection, total: 2
2008-09-28 10:03:25.522 Connected to database 'mythconverg' at host: localhost
2008-09-28 10:03:25.523 Current Schema Version: 1214
2008-09-28 10:03:25.713 DTVSM(0) Error: Wrong PMT; pmt->pn(31202) desired(31206)
2008-09-28 10:03:25.717 DTVSM(0) Error: Wrong PMT; pmt->pn(34002) desired(31206)
2008-09-28 10:03:25.718 DTVSM(0) Error: Wrong PMT; pmt->pn(31203) desired(31206)
2008-09-28 10:03:25.719 DTVSM(0) Error: Wrong PMT; pmt->pn(31208) desired(31206)
2008-09-28 10:03:25.719 DTVSM(0) Error: Wrong PMT; pmt->pn(31207) desired(31206)
2008-09-28 10:03:25.731 DTVSM(0) Error: Wrong PMT; pmt->pn(31205) desired(31206)
2008-09-28 10:03:25.742 DTVSM(0) Error: Wrong PMT; pmt->pn(31201) desired(31206)
2008-09-28 10:03:25.742 DTVSM(0) Error: Wrong PMT; pmt->pn(31204) desired(31206)

Regards
Ian Dobson

---

### Post by laga on 2008-09-28
This ticket is probably related: [http://svn.mythtv.org/trac/ticket/5739](http://svn.mythtv.org/trac/ticket/5739)

---

### Post by ian dobson on 2008-09-28
Hi laga,

That smells alot like my problem. I'll wait for the update.... any ideas with 21.1 will make it down to us?


Regards
Ian Dobson

---

### Post by ian dobson on 2008-10-02
Hi,

Anyone know when the fix'll be comming down to us?

Both tuners died last night and I missed a recording on one of the channels that just have "this/next" EPG information. My wife will not be happy when she hears this.

Regards
Ian Dobson

---

### Post by laga on 2008-10-02
It's available in the weekly builds. The UK weekly builds mirror should be available again, too.

---

### Post by ian dobson on 2008-10-02
Hi,

Updated to 0.21.0+fixes18528-0ubuntu0+mythbuntu1 about 12 hours ago. 1 hour ago I saw a:-

2008-10-02 18:40:40.679 EITScanner (3): StartActiveScan called with 11 multiplexes
2008-10-02 18:40:41.119 TVRec(3) Error: Failed to set channel to 40401. Reverting to kState_None
2008-10-02 18:40:41.191 EITScanner (3): Now looking for EIT data on multiplex of channel 40401

and the scanner continued, so the problem is solved.

Regards
Ian Dobson

---

### Post by ian dobson on 2008-10-04
Hi,

I spoke too soon, the EIT scanner died again last night. 

It looks as if it just sits there trying to grab the EIT from the last multiplex accessed rather than looping through the multiplexes.

Regards
Ian Dobson

---

### Post by ian dobson on 2008-10-06
Hi,

During a normal scheduled recording I just got this:-

```
2008-10-06 14:24:24.682 DVBChan(5:0) Error: SetChannelByString(30418): Input is not available
2008-10-06 14:24:24.725 TVRec(5) Error: Failed to set channel to 30418. Reverting to kState_None
2008-10-06 14:24:24.802 EITScanner (5): Now looking for EIT data on multiplex of channel 30418
2008-10-06 14:24:24.804 EITCache: Pruning all entries that ended before UTC 2008-10-05T14:25:31
2008-10-06 14:24:24.831 EITCache: Deleting old cache entries from the database
2008-10-06 14:25:03.253 AutoExpire: CalcParams(): Max required Free Space: 52.0 GB w/freq: 15 min
2008-10-06 14:25:35.561 EITScanner (3): Now looking for EIT data on multiplex of channel 30434
2008-10-06 14:25:35.577 EITCache: Pruning all entries that ended before UTC 2008-10-05T14:26:59
2008-10-06 14:25:35.605 EITCache: Deleting old cache entries from the database
2008-10-06 14:25:37.229 EITScanner (3): Started passive scan.
```

So the problem isn't solved grrrr.

Regards
Ian Dobson

---

### Post by laga on 2008-10-07
Hi,

you should post these logs to the ticket in the MythTV bug tracker. Nobody here can help you with that :)

---

### Post by ian dobson on 2008-10-07
OK,

posted the log to thread [http://svn.mythtv.org/trac/ticket/5739](http://svn.mythtv.org/trac/ticket/5739)

Regards
Ian Dobson

---

