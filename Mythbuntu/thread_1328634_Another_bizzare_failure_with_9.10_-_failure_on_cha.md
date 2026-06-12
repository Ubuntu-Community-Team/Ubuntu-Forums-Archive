---
title: "Another bizzare failure with 9.10 - failure on channel 2500?"
date: 2009-11-16
forum: Mythbuntu
---

### Post by MonsterMaxx on 2009-11-16
What the heck is going on with this thing?  I have had more problems with the 9.10 upgrade than I can shake a stick at.

Now the tuner that's connected to the cable box is failing to record.

What the heck are these channel 25xx channels?  I don't have any channels that high.  These are all 5xx channels.  When I check the channels in setup or mythweb info they are correct, but clearly myth is freaking out and putting a 2 in front of the 5xx.  Like Yes Man should be on channel 523, but it seems myth is trying to record on 2523. 

???????????????????????????????

6  	13215  	scheduler  	6  	0  	2009-11-16 15:50:13  	MythTV-SRV  	Scheduled items  	Scheduled 399 items in 2.1 = 0.00 match + 2.13 place
7 	13214 	scheduler 	6 	0 	2009-11-16 15:50:05 	MythTV-SRV 	Scheduled items 	Scheduled 399 items in 2.3 = 0.01 match + 2.26 place
8 	13213 	scheduler 	5 	0 	2009-11-16 15:50:02 	MythTV-SRV 	Canceled recording (Recorder Failed) 	Yes Man: channel 2523 on cardid 3, sourceid 2
9 	13212 	scheduler 	6 	0 	2009-11-16 15:49:02 	MythTV-SRV 	Scheduled items 	Scheduled 399 items in 2.1 = 0.00 match + 2.11 place
10 	13211 	scheduler 	6 	0 	2009-11-16 15:00:14 	MythTV-SRV 	Scheduled items 	Scheduled 399 items in 2.1 = 0.00 match + 2.09 place
11 	13210 	scheduler 	6 	0 	2009-11-16 15:00:06 	MythTV-SRV 	Scheduled items 	Scheduled 399 items in 2.1 = 0.00 match + 2.11 place
12 	13209 	scheduler 	5 	0 	2009-11-16 15:00:02 	MythTV-SRV 	Canceled recording (Recorder Failed) 	Flash of Genius: channel 2507 on cardid 3, sourceid 2
13 	13208 	scheduler 	6 	0 	2009-11-16 14:59:02 	MythTV-SRV 	Scheduled items 	Scheduled 399 items in 2.1 = 0.00 match + 2.08 place
14 	13207 	scheduler 	6 	0 	2009-11-16 12:50:13 	MythTV-SRV 	Scheduled items 	Scheduled 404 items in 2.1 = 0.00 match + 2.10 place
15 	13206 	scheduler 	6 	0 	2009-11-16 12:50:05 	MythTV-SRV 	Scheduled items 	Scheduled 404 items in 2.3 = 0.00 match + 2.27 place
16 	13205 	scheduler 	5 	0 	2009-11-16 12:50:02 	MythTV-SRV 	Canceled recording (Recorder Failed) 	Yes Man: channel 2515 on cardid 3, sourceid 2
17 	13204 	scheduler 	6 	0 	2009-11-16 12:49:02 	MythTV-SRV 	Scheduled items 	Scheduled 404 items in 2.1 = 0.00 match + 2.07 place
18 	13203 	scheduler 	6 	0 	2009-11-16 12:00:14 	MythTV-SRV 	Scheduled items 	Scheduled 404 items in 2.1 = 0.00 match + 2.09 place
19 	13202 	scheduler 	6 	0 	2009-11-16 12:00:06 	MythTV-SRV 	Scheduled items 	Scheduled 404 items in 2.1 = 0.01 match + 2.07 place
20 	13201 	scheduler 	5 	0 	2009-11-16 12:00:02 	MythTV-SRV 	Canceled recording (Recorder Failed) 	Flash of Genius: channel 2500 on cardid 3, sourceid 2
21 	13200 	scheduler 	6 	0 	2009-11-16 11:59:02 	MythTV-SRV 	Scheduled items 	Scheduled 404 items in 2.1 = 0.00 match + 2.09 place
22 	13199 	scheduler 	6 	0 	2009-11-16 09:15:13 	MythTV-SRV 	Scheduled items 	Scheduled 405 items in 2.1 = 0.00 match + 2.10 place
23 	13198 	scheduler 	6 	0 	2009-11-16 09:15:05 	MythTV-SRV 	Scheduled items 	Scheduled 405 items in 2.2 = 0.02 match + 2.14 place
24 	13197 	scheduler 	5 	0 	2009-11-16 09:15:02 	MythTV-SRV 	Canceled recording (Recorder Failed) 	Lady in the Water: channel 2521 on cardid 3, sourceid 2
25 	13196 	scheduler 	6 	0 	2009-11-16 09:14:04 	MythTV-SRV 	Scheduled items 	Scheduled 406 items in 3.4 = 0.00 match + 3.44 place
26 	13195 	scheduler 	6 	0 	2009-11-16 07:30:14 	MythTV-SRV 	Scheduled items 	Scheduled 406 items in 2.3 = 0.00 match + 2.27 place
27 	13194 	scheduler 	6 	0 	2009-11-16 07:30:06 	MythTV-SRV 	Scheduled items 	Scheduled 406 items in 2.2 = 0.02 match + 2.23 place
28 	13193 	scheduler 	5 	0 	2009-11-16 07:30:02 	MythTV-SRV 	Canceled recording (Recorder Failed) 	Black Knight: channel 2521 on cardid 3, sourceid 2
29 	13192 	scheduler 	6 	0 	2009-11-16 07:29:02 	MythTV-SRV 	Scheduled items 	Scheduled 406 items in 2.2 = 0.00 match + 2.23 place
30 	13191 	scheduler 	6 	0 	2009-11-16 00:45:18 	MythTV-SRV 	Scheduled items 	Scheduled 410 items in 2.5 = 0.00 match + 2.51 place
31 	13190 	scheduler 	6 	0 	2009-11-16 00:44:25 	MythTV-SRV 	Scheduled items 	Scheduled 410 items in 2.3 = 0.01 match + 2.31 place
32 	13189 	scheduler 	6 	0 	2009-11-16 00:44:18 	MythTV-SRV 	Scheduled items 	Scheduled 410 items in 2.3 = 0.00 match + 2.34 place
33 	13188 	scheduler 	6 	0 	2009-11-16 00:43:58 	MythTV-SRV 	Scheduled items 	Scheduled 410 items in 2.7 = 0.01 match + 2.73 place
34 	13187 	scheduler 	6 	0 	2009-11-16 00:43:21 	MythTV-SRV 	Scheduled items 	Scheduled 410 items in 2.4 = 0.00 match + 2.35 place
35 	13186 	scheduler 	6 	0 	2009-11-16 00:40:01 	MythTV-SRV 	Scheduled items 	Scheduled 410 items in 2.3 = 0.00 match + 2.28 place
36 	13185 	scheduler 	6 	0 	2009-11-15 23:15:13 	MythTV-SRV 	Scheduled items 	Scheduled 412 items in 2.3 = 0.00 match + 2.31 place
37 	13184 	scheduler 	6 	0 	2009-11-15 23:15:05 	MythTV-SRV 	Scheduled items 	Scheduled 412 items in 2.3 = 0.01 match + 2.29 place
38 	13183 	scheduler 	5 	0 	2009-11-15 23:15:02 	MythTV-SRV 	Canceled recording (Recorder Failed) 	Yes Man: channel 2523 on cardid 3, sourceid 2


I tell you one thing, this 'upgrade' has been a disaster.  Nothing but problems on several fronts.  I'd advise anyone else thinking of going from 9.04 up to 9.10 to wait a while.

---

### Post by MonsterMaxx on 2009-11-16
It seems this tuner is completely down.  When I change to it in live TV mode the frontend will never respond again.

Even with the cable box on a low channel like 7 it's totally dead.

This is a cable box connected to my pvr350 thru s-vid port and channel changing is done via firewire.  Worked just fine in 9.04.
Is the 350 no longer supported?

---

