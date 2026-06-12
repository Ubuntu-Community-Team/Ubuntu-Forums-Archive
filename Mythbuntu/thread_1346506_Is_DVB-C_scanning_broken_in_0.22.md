---
title: "Is DVB-C scanning broken in 0.22?"
date: 2009-12-05
forum: Mythbuntu
---

### Post by ian dobson on 2009-12-05
Hi All,

I've just upgraded to 0.22 about 10 days ago and now my cable provider has added afew digital channels.

My TV found the changes within afew minutes of scanning.

Running mythtv-setup and scanning for new channels the scanner brings up the following "errors" 

Timeout - 5 Possible channels found

So I then tried w_scan to generate a channels.conf file and when I try importing it I get almost the same errors but the channels are added but when I try and record from one of the channels I get a 0 byte file.

Regards
Ian Dobson

---

### Post by ian dobson on 2009-12-05
Hi,

Looks as if it's a problem with the dvb_multiplex table, I'll post more information in a bit.

Regards
Ian Dobson

---

### Post by ian dobson on 2009-12-05
Hi,

OK heres a dump of the dtv_multiplex, the problem I'm having is with multiplex 1103.

```
-+--------------+-------------------+----------------+---------+---------------+-----------+--------------+-----------+---------+------------+----------------+---------------------+-------------------+
| mplexid | sourceid | transportid | networkid | frequency | inversion | symbolrate | fec  | polarity | modulation | bandwidth | lp_code_rate | transmission_mode | guard_interval | visible | constellation | hierarchy | hp_code_rate | mod_sys   | rolloff | sistandard | serviceversion | updatetimestamp     | default_authority |
+---------+----------+-------------+-----------+-----------+-----------+------------+------+----------+------------+-----------+--------------+-------------------+----------------+---------+---------------+-----------+--------------+-----------+---------+------------+----------------+---------------------+-------------------+
|       1 |        2 |         602 |         1 | 698000000 | a         |    6900000 | none | NULL     | qam_256    | NULL      | NULL         | NULL              | NULL           |       0 | NULL          | NULL      | NULL         | 1         | NULL    | dvb        |              8 | 2008-09-13 16:51:14 |                   |
|       3 |        2 |         601 |         1 | 394000000 | a         |    6900000 | none | NULL     | qam_256    | NULL      | NULL         | NULL              | NULL           |       0 | NULL          | NULL      | NULL         | 1         | NULL    | dvb        |              1 | 2008-09-13 16:51:25 |                   |
|       4 |        2 |         603 |         1 | 794000000 | a         |    6900000 | none | NULL     | qam_256    | NULL      | NULL         | NULL              | NULL           |       0 | NULL          | NULL      | NULL         | 1         | NULL    | dvb        |              1 | 2008-09-13 16:51:32 |                   |
|       6 |        2 |         607 |         1 | 762000000 | a         |    6900000 | none | NULL     | qam_256    | NULL      | NULL         | NULL              | NULL           |       0 | NULL          | NULL      | NULL         | 1         | NULL    | dvb        |             12 | 2009-08-16 21:10:47 |                   |
|       9 |        2 |         619 |         1 | 594000000 | a         |    6900000 | none | NULL     | qam_256    | NULL      | NULL         | NULL              | NULL           |       0 | NULL          | NULL      | NULL         | 1         | NULL    | dvb        |              2 | 2008-09-13 16:52:04 |                   |
|      10 |        2 |         608 |         1 | 570000000 | a         |    6900000 | none | NULL     | qam_256    | NULL      | NULL         | NULL              | NULL           |       0 | NULL          | NULL      | NULL         | 1         | NULL    | dvb        |              2 | 2009-02-08 08:14:41 |                   |
|      11 |        2 |         609 |         1 | 818000000 | a         |    6900000 | none | NULL     | qam_256    | NULL      | NULL         | NULL              | NULL           |       0 | NULL          | NULL      | NULL         | 1         | NULL    | dvb        |             11 | 2009-08-16 21:11:42 |                   |
|      12 |        2 |         610 |         1 | 842000000 | a         |    6900000 | none | NULL     | qam_256    | NULL      | NULL         | NULL              | NULL           |       0 | NULL          | NULL      | NULL         | 1         | NULL    | dvb        |              1 | 2008-09-13 16:52:27 |                   |
|      13 |        2 |         611 |         1 | 826000000 | a         |    6900000 | none | NULL     | qam_256    | NULL      | NULL         | NULL              | NULL           |       0 | NULL          | NULL      | NULL         | 1         | NULL    | dvb        |              9 | 2009-08-16 21:11:52 |                   |
|      14 |        2 |         612 |         1 | 834000000 | a         |    6900000 | none | NULL     | qam_256    | NULL      | NULL         | NULL              | NULL           |       0 | NULL          | NULL      | NULL         | 1         | NULL    | dvb        |              8 | 2009-08-16 21:12:02 |                   |
|      15 |        2 |         613 |         1 | 770000000 | a         |    6900000 | none | NULL     | qam_256    | NULL      | NULL         | NULL              | NULL           |       0 | NULL          | NULL      | NULL         | 1         | NULL    | dvb        |              3 | 2009-08-16 21:10:52 |                   |
|      16 |        2 |         614 |         1 | 802000000 | a         |    6900000 | none | NULL     | qam_256    | NULL      | NULL         | NULL              | NULL           |       0 | NULL          | NULL      | NULL         | 1         | NULL    | dvb        |              1 | 2008-09-13 16:53:00 |                   |
|      17 |        2 |         615 |         1 | 810000000 | a         |    6900000 | none | NULL     | qam_256    | NULL      | NULL         | NULL              | NULL           |       0 | NULL          | NULL      | NULL         | 1         | NULL    | dvb        |              1 | 2008-09-13 16:53:04 |                   |
|      18 |        2 |         617 |         1 | 706000000 | a         |    6900000 | none | NULL     | qam_256    | NULL      | NULL         | NULL              | NULL           |       0 | NULL          | NULL      | NULL         | 1         | NULL    | dvb        |              1 | 2009-08-16 21:10:28 |                   |
|    1078 |        2 |         620 |         1 | 714000000 | a         |    6900000 | none | NULL     | qam_256    | NULL      | NULL         | NULL              | NULL           |       0 | NULL          | NULL      | NULL         | 1         | NULL    | dvb        |              2 | 2009-01-25 10:08:49 |                   |
|    1104 |        2 |         604 |         1 | 786000000 | a         |    6900000 | none | v        | qam_256    | a         | auto         | a                 | auto           |       0 | qam_256       | a         | auto         | UNDEFINED | 0.35    | dvb        |             33 | 2009-12-05 12:47:22 |                   |
|    1105 |        2 |         605 |         1 | 722000000 | a         |    6900000 | none | v        | qam_256    | a         | auto         | a                 | auto           |       0 | qam_256       | a         | auto         | UNDEFINED | 0.35    | dvb        |             33 | 2009-12-05 12:47:22 |                   |
|    1103 |        2 |         625 |         1 | 746000000 | a         |    6900000 | none | NULL     | qam_256    | NULL      | NULL         | NULL              | NULL           |       0 | NULL          | NULL      | NULL         | 1         | NULL    | dvb        |             33 | 2009-12-05 12:06:47 |                   |
+---------+----------+-------------+-----------+-----------+-----------+------------+------+----------+------------+-----------+--------------+-------------------+----------------+---------+---------------+-----------+--------------+-----------+---------+------------+----------------+---------------------+-------------------+
```

And heres part of the channels.conf


```
3+(3+):746000000:INVERSION_AUTO:6900000:FEC_AUTO:QAM_256:2002:2003:30014
SSF(SSF):746000000:INVERSION_AUTO:6900000:FEC_AUTO:QAM_256:39:40:30015
Schweiz 5((null)):746000000:INVERSION_AUTO:6900000:FEC_AUTO:QAM_256:52:53:30016
Star TV((null)):746000000:INVERSION_AUTO:6900000:FEC_AUTO:QAM_256:46:47:30017
Telebasel(IBC):746000000:INVERSION_AUTO:6900000:FEC_AUTO:QAM_256:8000:8001:30201
TeleM1((null)):746000000:INVERSION_AUTO:6900000:FEC_AUTO:QAM_256:68:0:30202
Infokanal(Provider):746000000:INVERSION_AUTO:6900000:FEC_AUTO:QAM_256:38:0:30301
Viva CH/Nick((null)):746000000:INVERSION_AUTO:6900000:FEC_AUTO:QAM_256:43:44:30447
MTV(MTV Schweiz):746000000:INVERSION_AUTO:6900000:FEC_AUTO:QAM_256:49:50:30448
RAI1(RAI):746000000:INVERSION_AUTO:6900000:FEC_AUTO:QAM_256:1001:1002:32201
```

and here's a dump of one of the channels
```
+--------+---------+--------+----------+----------+------+------+----------+--------------+---------+-------------+----------+------------+--------+-------+----------+---------+---------------+---------------+---------+-----------+----------+-----------------+-----------------+---------------------+-------------------+------------+
| chanid | channum | freqid | sourceid | callsign | name | icon | finetune | videofilters | xmltvid | recpriority | contrast | brightness | colour | hue   | tvformat | visible | outputfilters | useonairguide | mplexid | serviceid | tmoffset | atsc_major_chan | atsc_minor_chan | last_record         | default_authority | commmethod |
+--------+---------+--------+----------+----------+------+------+----------+--------------+---------+-------------+----------+------------+--------+-------+----------+---------+---------------+---------------+---------+-----------+----------+-----------------+-----------------+---------------------+-------------------+------------+
|  42000 | 4       |        |        2 | 3+       | 3+   |      |        0 |              |         |           0 |    32768 |      32768 |  32768 | 32768 | Default  |       1 |               |             1 |    1103 |     30014 |        0 |               0 |               0 | 0000-00-00 00:00:00 |                   |         -1 |
+--------+---------+--------+----------+----------+------+------+----------+--------------+---------+-------------+----------+------------+--------+-------+----------+---------+---------------+---------------+---------+-----------+----------+-----------------+-----------------+---------------------+-------------------+------------+
```
Can anyone see whats wrong?

Regards
Ian Dobson

---

### Post by ian dobson on 2009-12-06
Hi All,

Someone please have a look at this/help me get the new channels up and running. My wife is not too happy that 3+ and her CSI are gone (We had this channel as Analog before the switch over).

Note afew other channels/multiplex's that got added at the same time seem to come through OK, I haven't tried recording anything from them but the EPG seems to be OK.

I've attached a picture of the scan process.

[IMG]http://mail.planet-ian.com/scan.jpg[/IMG]

and here's a new dump to the dtv_multiplex
```
 mysql -u root -pquango -e "select * from mythconverg.dtv_multiplex;"
+---------+----------+-------------+-----------+-----------+-----------+------------+------+----------+------------+-----------+--------------+-------------------+----------------+---------+---------------+-----------+--------------+-----------+---------+------------+----------------+---------------------+-------------------+
| mplexid | sourceid | transportid | networkid | frequency | inversion | symbolrate | fec  | polarity | modulation | bandwidth | lp_code_rate | transmission_mode | guard_interval | visible | constellation | hierarchy | hp_code_rate | mod_sys   | rolloff | sistandard | serviceversion | updatetimestamp     | default_authority |
+---------+----------+-------------+-----------+-----------+-----------+------------+------+----------+------------+-----------+--------------+-------------------+----------------+---------+---------------+-----------+--------------+-----------+---------+------------+----------------+---------------------+-------------------+
|       1 |        2 |         602 |         1 | 698000000 | a         |    6900000 | none | NULL     | qam_256    | NULL      | NULL         | NULL              | NULL           |       0 | NULL          | NULL      | NULL         | 1         | NULL    | dvb        |              8 | 2008-09-13 16:51:14 |                   |
|       3 |        2 |         601 |         1 | 394000000 | a         |    6900000 | none | NULL     | qam_256    | NULL      | NULL         | NULL              | NULL           |       0 | NULL          | NULL      | NULL         | 1         | NULL    | dvb        |              1 | 2008-09-13 16:51:25 |                   |
|       4 |        2 |         603 |         1 | 794000000 | a         |    6900000 | none | NULL     | qam_256    | NULL      | NULL         | NULL              | NULL           |       0 | NULL          | NULL      | NULL         | 1         | NULL    | dvb        |              1 | 2008-09-13 16:51:32 |                   |
|       6 |        2 |         607 |         1 | 762000000 | a         |    6900000 | none | NULL     | qam_256    | NULL      | NULL         | NULL              | NULL           |       0 | NULL          | NULL      | NULL         | 1         | NULL    | dvb        |             12 | 2009-08-16 21:10:47 |                   |
|       9 |        2 |         619 |         1 | 594000000 | a         |    6900000 | none | NULL     | qam_256    | NULL      | NULL         | NULL              | NULL           |       0 | NULL          | NULL      | NULL         | 1         | NULL    | dvb        |              2 | 2008-09-13 16:52:04 |                   |
|      10 |        2 |         608 |         1 | 570000000 | a         |    6900000 | none | NULL     | qam_256    | NULL      | NULL         | NULL              | NULL           |       0 | NULL          | NULL      | NULL         | 1         | NULL    | dvb        |              2 | 2009-02-08 08:14:41 |                   |
|      11 |        2 |         609 |         1 | 818000000 | a         |    6900000 | none | NULL     | qam_256    | NULL      | NULL         | NULL              | NULL           |       0 | NULL          | NULL      | NULL         | 1         | NULL    | dvb        |             11 | 2009-08-16 21:11:42 |                   |
|      12 |        2 |         610 |         1 | 842000000 | a         |    6900000 | none | NULL     | qam_256    | NULL      | NULL         | NULL              | NULL           |       0 | NULL          | NULL      | NULL         | 1         | NULL    | dvb        |              1 | 2008-09-13 16:52:27 |                   |
|      13 |        2 |         611 |         1 | 826000000 | a         |    6900000 | none | NULL     | qam_256    | NULL      | NULL         | NULL              | NULL           |       0 | NULL          | NULL      | NULL         | 1         | NULL    | dvb        |              9 | 2009-08-16 21:11:52 | 
|      14 |        2 |         612 |         1 | 834000000 | a         |    6900000 | none | NULL     | qam_256    | NULL      | NULL         | NULL              | NULL           |       0 | NULL          | NULL      | NULL         | 1         | NULL    | dvb        |              8 | 2009-08-16 21:12:02 |                   |
|      15 |        2 |         613 |         1 | 770000000 | a         |    6900000 | none | NULL     | qam_256    | NULL      | NULL         | NULL              | NULL           |       0 | NULL          | NULL      | NULL         | 1         | NULL    | dvb        |              3 | 2009-08-16 21:10:52 |                   |
|      16 |        2 |         614 |         1 | 802000000 | a         |    6900000 | none | NULL     | qam_256    | NULL      | NULL         | NULL              | NULL           |       0 | NULL          | NULL      | NULL         | 1         | NULL    | dvb        |              1 | 2008-09-13 16:53:00 |                   |
|      17 |        2 |         615 |         1 | 810000000 | a         |    6900000 | none | NULL     | qam_256    | NULL      | NULL         | NULL              | NULL           |       0 | NULL          | NULL      | NULL         | 1         | NULL    | dvb        |              1 | 2008-09-13 16:53:04 |                   |
|      18 |        2 |         617 |         1 | 706000000 | a         |    6900000 | none | NULL     | qam_256    | NULL      | NULL         | NULL              | NULL           |       0 | NULL          | NULL      | NULL         | 1         | NULL    | dvb        |              1 | 2009-08-16 21:10:28 |                   |
|    1078 |        2 |         620 |         1 | 714000000 | a         |    6900000 | none | NULL     | qam_256    | NULL      | NULL         | NULL              | NULL           |       0 | NULL          | NULL      | NULL         | 1         | NULL    | dvb        |              2 | 2009-01-25 10:08:49 |                   |
|    1107 |        2 |         605 |         1 | 722000000 | a         |    6900000 | none | v        | qam_256    | a         | auto         | a                 | auto           |       0 | qam_256       | a         | auto         | UNDEFINED | 0.35    | dvb        |             33 | 2009-12-05 20:45:28 |                   |
|    1108 |        2 |         625 |         1 | 746000000 | a         |    6900000 | auto | v        | qam_256    | a         | auto         | a                 | auto           |       0 | qam_256       | a         | auto         | UNDEFINED | 0.35    | dvb        |             33 | 2009-12-05 20:45:38 |                   |
|    1106 |        2 |         604 |         1 | 786000000 | a         |    6900000 | none | v        | qam_256    | a         | auto         | a                 | auto           |       0 | qam_256       | a         | auto         | UNDEFINED | 0.35    | dvb        |             33 | 2009-12-05 20:45:03 |                   |
+---------+----------+-------------+-----------+-----------+-----------+------------+------+----------+------------+-----------+--------------+-------------------+----------------+---------+---------------+-----------+--------------+-----------+---------+------------+----------------+---------------------+-------------------+
```Regards
Ian Dobson

---

### Post by ian dobson on 2009-12-06
Hi,

OK I've added extra logging information to mythtvbackend and am getting this:-

```
2009-12-06 11:08:02.452 EITScanner (1): Now looking for EIT data on multiplex of channel 30301
2009-12-06 11:08:02.453 EITCache: Pruning all entries that ended before UTC 2009-12-05T11:12:24
2009-12-06 11:08:02.455 DVBSH(/dev/dvb/adapter0/frontend0): AddListener(0x2a53748) -- begin
2009-12-06 11:08:02.457 DVBSH(/dev/dvb/adapter0/frontend0): AddListener(0x2a53748) -- locked
2009-12-06 11:08:02.460 DVBSH(/dev/dvb/adapter0/frontend0): RunTS(): begin
2009-12-06 11:08:02.481 PIDInfo(/dev/dvb/adapter0/frontend0): Opening filter for pid 0x0
2009-12-06 11:08:02.492 PIDInfo(/dev/dvb/adapter0/frontend0): Opening filter for pid 0x10
2009-12-06 11:08:02.503 PIDInfo(/dev/dvb/adapter0/frontend0): Opening filter for pid 0x11
2009-12-06 11:08:02.503 PIDInfo(/dev/dvb/adapter0/frontend0): Opening filter for pid 0x14
2009-12-06 11:08:02.477 EITCache: Deleting old cache entries from the database
2009-12-06 11:08:02.477 DVBSH(/dev/dvb/adapter0/frontend0): AddListener(0x2a53748) -- end
2009-12-06 11:08:02.805 CreatePATSingleProgram()
2009-12-06 11:08:02.816 PAT in input stream
2009-12-06 11:08:02.817 Program Association Table
 PSIP tableID(0x0) length(53) extension(0x271)
      version(5) current(1) section(0) last_section(0)
         tsid: 625
 programCount: 11
  program number     0 has PID 0x  10   data  0x 0 0x 0 0xe0 0x10
  program number 30014 has PID 0x  23   data  0x75 0x3e 0xe0 0x23
  program number 30015 has PID 0x  24   data  0x75 0x3f 0xe0 0x24
  program number 30016 has PID 0x  22   data  0x75 0x40 0xe0 0x22
  program number 30017 has PID 0x 7d0   data  0x75 0x41 0xe7 0xd0
  program number 30201 has PID 0x1f54   data  0x75 0xf9 0xff 0x54
  program number 30202 has PID 0x  42   data  0x75 0xfa 0xe0 0x42
  program number 30301 has PID 0x  21   data  0x76 0x5d 0xe0 0x21
  program number 30447 has PID 0x  25   data  0x76 0xef 0xe0 0x25
  program number 30448 has PID 0x  20   data  0x76 0xf0 0xe0 0x20
  program number 32201 has PID 0x 3e8   data  0x7d 0xc9 0xe3 0xe8

2009-12-06 11:08:02.817 desired_program(30301) pid(0x21)
2009-12-06 11:08:02.818 pmt_pid(0x21)
2009-12-06 11:08:02.818 PAT for output stream
2009-12-06 11:08:02.819 Program Association Table
 PSIP tableID(0x0) length(13) extension(0x271)
      version(5) current(1) section(0) last_section(0)
         tsid: 625
 programCount: 1
  program number     1 has PID 0x  21   data  0x 0 0x 1 0xe0 0x21

2009-12-06 11:08:02.819 PIDInfo(/dev/dvb/adapter0/frontend0): Opening filter for pid 0x21
2009-12-06 11:08:03.272 CreatePMTSingleProgram()
2009-12-06 11:08:03.283 PMT in input stream
2009-12-06 11:08:03.283 Program Map Table ver(2) pid(0x21) pnum(30301) len(18)

 Stream #0 pid(0x26) type(video-mpeg2  0x2)

2009-12-06 11:08:03.284 Created PMT
Program Map Table ver(2) pid(0x21) pnum(1) len(18)

 Stream #0 pid(0x26) type(video-mpeg2  0x2)

2009-12-06 11:08:03.284 PMT for output stream
2009-12-06 11:08:03.285 Program Map Table ver(2) pid(0x21) pnum(1) len(18)

 Stream #0 pid(0x26) type(video-mpeg2  0x2)

2009-12-06 11:08:03.284 Created PMT
Program Map Table ver(2) pid(0x21) pnum(1) len(18)

 Stream #0 pid(0x26) type(video-mpeg2  0x2)

2009-12-06 11:08:03.284 PMT for output stream
2009-12-06 11:08:03.285 Program Map Table ver(2) pid(0x21) pnum(1) len(18)

 Stream #0 pid(0x26) type(video-mpeg2  0x2)

2009-12-06 11:08:03.285 PIDInfo(/dev/dvb/adapter0/frontend0): Opening filter for pid 0x26
2009-12-06 11:08:03.358 TVRec(1): Got good signal
 
```

The PMT table looks correct and corresponds to the info for the channels in the database so I'm totally lost as what the problem could be.

Regards
Ian Dobson

---

### Post by ian dobson on 2009-12-06
Hi All,

OK after manually correcting the dtv_multiplex I seem to be able to record from 3+ which it a major step forward.

The problem seems to be if I stop then restart the backend it doesn't seem to attach to the tuners again/can't grab any data from the tuners.

Regards
Ian Dobson

---

### Post by ian dobson on 2009-12-06
Hi,

Ok problem solved, and christmas saved. Manually editing the multiplex in dtv_multiplex seems to have solved all the problems.

The screwed up dtv_multiplex seemed to cause mythtbackend to blow a fuse when ever it tried to tune to any channel in the multiplex even the EIT/EPG scanner killed the backend.

Regards
Ian Dobson

---

