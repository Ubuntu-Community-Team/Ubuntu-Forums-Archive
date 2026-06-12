---
title: "Recording Stops - Everything else seems to work..."
date: 2011-09-21
forum: Mythbuntu
---

### Post by iiwii on 2011-09-21
It's been awhile since my last (desperate) posts on here. My Mythbuntu system has been running pretty good.  Lately though I have had a few lockups. 

A quick overview of my situation -- I've been doing a manual schedule for 5 recordings while I am work. And while it has worked pretty good, I still come home and find it has randomly stopped recording.  One of two symptoms are showing:

1. It's locked up entirely.  The screen is dark or is frozen -- the clock stopped updating a long time ago.  The mouse and keyboard do not respond and my only option is to reboot.  My recordings did not finish recording. The log also stops.

-- From my research this sounds like xserver is crashing. I'm not sure how to fix that if true. How would I test this?

2. It looks like it is on standby and working fine.  But, when I go for my daily recordings, I find it has recorded up to a point and then stopped entirely (like today's log excerpts posted below). It continues to log and everything else is okay.  The log shows that SHOW3 finished recording at 6:25am. The actual recording only recorded for about 5 minutes. In essence, it stopped recording at 6:05 am but didn't realize something was wrong with the tuner until the NEXT scheduled recordings began to record.

-- The log errors make me think the video card is locking up or freezing. 

I added a PCIex Intel Gigabit card over the weekend. I was having these lockup issues before I installed the additional NIC. The only issues it has caused is an issue with Samba which I "resolved" by shelving the card for now. I'll leave that for another post...

I'm still a NOOB at Mythbuntu and most of Linux. I hope I've provided enough information.  This board was a great help with my other problems.  Thanks in advance for any help!

System:
 ASUS P5B + Core 2 Duo + 3GB Corsair
 Hauppauge HVR-1250
 640 GB Caviar Black (64MB cache)
 EVGA Geforce GT 520 (Nvidia Chipset)

Log excerpts follow: ------------------------

2011-09-21 02:56:51.702 mythbackend: Running housekeeping thread
 2011-09-21 03:08:01.713 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
 2011-09-21 03:16:28.636 MainServer::ANN Monitor
 2011-09-21 03:16:28.711 adding: htpc as a client (events: 2)
 2011-09-21 03:17:01.562 MainServer::ANN Monitor
 2011-09-21 03:17:01.662 adding: htpc as a client (events: 2)
 2011-09-21 03:23:02.214 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
 2011-09-21 03:38:02.707 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
 2011-09-21 03:53:03.206 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
 2011-09-21 04:08:03.719 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
 2011-09-21 04:17:01.694 MainServer::ANN Monitor
 2011-09-21 04:17:01.786 adding: htpc as a client (events: 2)
 2011-09-21 04:23:04.232 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
 2011-09-21 04:38:04.742 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
 2011-09-21 04:53:05.258 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
 2011-09-21 04:58:00.421 Reschedule requested for id 0.
 2011-09-21 04:58:00.583 Scheduled 54 items in 0.2 = 0.03 match + 0.13 place
 2011-09-21 04:58:00.617 scheduler: Scheduled items: Scheduled 54 items in 0.2 = 0.03 match + 0.13 place
 2011-09-21 04:58:30.288 TVRec(1): ASK_RECORDING 1 29 0 0
 2011-09-21 04:59:01.745 TVRec(1): Changing from None to RecordingOnly
 2011-09-21 04:59:01.812 TVRec(1): HW Tuner: 1->1
 2011-09-21 04:59:01.946 DVBSM(/dev/dvb/adapter0/frontend0), Warning: Cannot measure Signal Strength
 			eno: Invalid argument (22)
 2011-09-21 04:59:01.986 DVBSM(/dev/dvb/adapter0/frontend0), Warning: Cannot measure S/N
 			eno: Invalid argument (22)
 2011-09-21 04:59:02.034 AutoExpire: CalcParams(): Max required Free Space: 3.0 GB w/freq: 14 min
 2011-09-21 04:59:02.079 Started recording: "SHOW1 (Manual Record)":"Wed Sep 21 05:00:00 2011": channel 11791 on cardid 1, sourceid 1
 2011-09-21 04:59:02.124 scheduler: Started recording: "SHOW1 (Manual Record)":"Wed Sep 21 05:00:00 2011": channel 11791 on cardid 1, sourceid 1
 2011-09-21 04:59:03.328 Updating status for "SHOW1 (Manual Record)":"Wed Sep 21 05:00:00 2011" on cardid 1 (Tuning => Recording)
 2011-09-21 04:59:03.571 TVRec(1): rec->GetPathname(): '/var/lib/mythtv/recordings/11791_20110921045900.mpg'
 2011-09-21 05:08:05.765 AutoExpire: CalcParams(): Max required Free Space: 3.0 GB w/freq: 14 min
 2011-09-21 05:17:01.696 MainServer::ANN Monitor
 2011-09-21 05:17:01.845 adding: htpc as a client (events: 2)
 2011-09-21 05:22:06.492 AutoExpire: CalcParams(): Max required Free Space: 3.0 GB w/freq: 14 min
 2011-09-21 05:25:30.415 TVRec(1): Changing from RecordingOnly to None
 2011-09-21 05:25:30.448 Updating status for "SHOW1 (Manual Record)":"Wed Sep 21 05:00:00 2011" on cardid 1 (Recording => Recorded)
 2011-09-21 05:25:30.449 Finished recording SHOW1 (Manual Record) "Wed Sep 21 05:00:00 2011": channel 11791
 2011-09-21 05:25:30.482 Reschedule requested for id 0.
 2011-09-21 05:25:30.639 scheduler: Finished recording: SHOW1 (Manual Record) "Wed Sep 21 05:00:00 2011": channel 11791
 2011-09-21 05:25:30.888 Scheduled 53 items in 0.4 = 0.24 match + 0.16 place
 2011-09-21 05:25:30.929 scheduler: Scheduled items: Scheduled 53 items in 0.4 = 0.24 match + 0.16 place
 2011-09-21 05:25:31.031 Finished recording SHOW1 (Manual Record) "Wed Sep 21 05:00:00 2011": channel 11791
 2011-09-21 05:25:31.072 scheduler: Finished recording: SHOW1 (Manual Record) "Wed Sep 21 05:00:00 2011": channel 11791
 2011-09-21 05:25:31.269 MainServer::ANN Monitor
 2011-09-21 05:25:31.300 adding: htpc as a client (events: 0)
 2011-09-21 05:25:31.375 MainServer::ANN Monitor
 2011-09-21 05:25:31.425 adding: htpc as a client (events: 1)
 Error in my_thread_global_end(): 1 threads didn't exit
 2011-09-21 05:28:00.988 Reschedule requested for id 0.
 2011-09-21 05:28:01.161 Scheduled 53 items in 0.2 = 0.05 match + 0.12 place
 2011-09-21 05:28:01.201 scheduler: Scheduled items: Scheduled 53 items in 0.2 = 0.05 match + 0.12 place
 2011-09-21 05:28:30.144 TVRec(1): ASK_RECORDING 1 29 0 0
 2011-09-21 05:29:01.284 TVRec(1): Changing from None to RecordingOnly
 2011-09-21 05:29:01.346 TVRec(1): HW Tuner: 1->1
 2011-09-21 05:29:01.446 AutoExpire: CalcParams(): Max required Free Space: 3.0 GB w/freq: 14 min
 2011-09-21 05:29:01.496 Started recording: "SHOW2 (Manual Record)":"Wed Sep 21 05:30:00 2011": channel 11791 on cardid 1, sourceid 1
 2011-09-21 05:29:01.542 scheduler: Started recording: "SHOW2 (Manual Record)":"Wed Sep 21 05:30:00 2011": channel 11791 on cardid 1, sourceid 1
 2011-09-21 05:29:02.549 Updating status for "SHOW2 (Manual Record)":"Wed Sep 21 05:30:00 2011" on cardid 1 (Tuning => Recording)
 2011-09-21 05:29:02.763 TVRec(1): rec->GetPathname(): '/var/lib/mythtv/recordings/11791_20110921052900.mpg'
 2011-09-21 05:29:59.773 Error: offset>181, pes length & current cannot be queried
 2011-09-21 05:36:07.191 AutoExpire: CalcParams(): Max required Free Space: 3.0 GB w/freq: 14 min
 2011-09-21 05:50:07.918 AutoExpire: CalcParams(): Max required Free Space: 3.0 GB w/freq: 14 min
 2011-09-21 05:55:30.517 TVRec(1): Changing from RecordingOnly to None
 2011-09-21 05:55:30.574 Updating status for "SHOW2 (Manual Record)":"Wed Sep 21 05:30:00 2011" on cardid 1 (Recording => Recorded)
 2011-09-21 05:55:30.575 Finished recording SHOW2 (Manual Record) "Wed Sep 21 05:30:00 2011": channel 11791
 2011-09-21 05:55:30.661 scheduler: Finished recording: SHOW2 (Manual Record) "Wed Sep 21 05:30:00 2011": channel 11791
 2011-09-21 05:55:30.666 Reschedule requested for id 0.
 2011-09-21 05:55:30.870 Scheduled 52 items in 0.2 = 0.07 match + 0.13 place
 2011-09-21 05:55:30.904 scheduler: Scheduled items: Scheduled 52 items in 0.2 = 0.07 match + 0.13 place
 2011-09-21 05:55:30.992 Finished recording SHOW2 (Manual Record) "Wed Sep 21 05:30:00 2011": channel 11791
 2011-09-21 05:55:31.071 scheduler: Finished recording: SHOW2 (Manual Record) "Wed Sep 21 05:30:00 2011": channel 11791
 2011-09-21 05:55:32.191 MainServer::ANN Monitor
 2011-09-21 05:55:32.251 adding: htpc as a client (events: 0)
 2011-09-21 05:55:32.293 MainServer::ANN Monitor
 2011-09-21 05:55:32.334 adding: htpc as a client (events: 1)
 2011-09-21 05:58:00.023 Reschedule requested for id 0.
 2011-09-21 05:58:00.195 Scheduled 52 items in 0.2 = 0.04 match + 0.13 place
 2011-09-21 05:58:00.238 scheduler: Scheduled items: Scheduled 52 items in 0.2 = 0.04 match + 0.13 place
 2011-09-21 05:58:30.267 TVRec(1): ASK_RECORDING 1 29 0 0
 2011-09-21 05:59:01.319 TVRec(1): Changing from None to RecordingOnly
 2011-09-21 05:59:01.381 TVRec(1): HW Tuner: 1->1
 2011-09-21 05:59:01.486 AutoExpire: CalcParams(): Max required Free Space: 3.0 GB w/freq: 14 min
 2011-09-21 05:59:01.531 Started recording: "SHOW3 (Manual Record)":"Wed Sep 21 06:00:00 2011": channel 11791 on cardid 1, sourceid 1
 2011-09-21 05:59:01.577 scheduler: Started recording: "SHOW3 (Manual Record)":"Wed Sep 21 06:00:00 2011": channel 11791 on cardid 1, sourceid 1
 2011-09-21 05:59:02.785 Updating status for "SHOW3 (Manual Record)":"Wed Sep 21 06:00:00 2011" on cardid 1 (Tuning => Recording)
 2011-09-21 05:59:03.002 TVRec(1): rec->GetPathname(): '/var/lib/mythtv/recordings/11791_20110921055900.mpg'
 2011-09-21 06:04:08.663 AutoExpire: CalcParams(): Max required Free Space: 3.0 GB w/freq: 14 min
 2011-09-21 06:17:02.560 MainServer::ANN Monitor
 2011-09-21 06:17:02.622 adding: htpc as a client (events: 2)
 2011-09-21 06:18:09.387 AutoExpire: CalcParams(): Max required Free Space: 3.0 GB w/freq: 14 min
 2011-09-21 06:25:30.445 TVRec(1): Changing from RecordingOnly to None
 2011-09-21 06:25:30.481 Updating status for "SHOW3 (Manual Record)":"Wed Sep 21 06:00:00 2011" on cardid 1 (Recording => Recorded)
 2011-09-21 06:25:30.489 Finished recording SHOW3 (Manual Record) "Wed Sep 21 06:00:00 2011": channel 11791
 2011-09-21 06:25:30.516 Reschedule requested for id 0.
 2011-09-21 06:25:30.571 scheduler: Finished recording: SHOW3 (Manual Record) "Wed Sep 21 06:00:00 2011": channel 11791
 2011-09-21 06:25:30.761 Finished recording SHOW3 (Manual Record) "Wed Sep 21 06:00:00 2011": channel 11791
 2011-09-21 06:25:30.781 Scheduled 51 items in 0.3 = 0.09 match + 0.17 place
 2011-09-21 06:25:30.837 scheduler: Last message repeated 1 times: Finished recording: SHOW3 (Manual Record) "Wed Sep 21 06:00:00 2011": channel 11791
 2011-09-21 06:25:30.870 scheduler: Scheduled items: Scheduled 51 items in 0.3 = 0.09 match + 0.17 place
 2011-09-21 06:25:30.928 MainServer::ANN Monitor
 2011-09-21 06:25:30.958 adding: htpc as a client (events: 0)
 2011-09-21 06:25:30.992 MainServer::ANN Monitor
 2011-09-21 06:25:31.025 adding: htpc as a client (events: 1)
 2011-09-21 06:28:00.929 Reschedule requested for id 0.
 2011-09-21 06:28:01.116 Scheduled 51 items in 0.2 = 0.05 match + 0.13 place
 2011-09-21 06:28:01.161 scheduler: Scheduled items: Scheduled 51 items in 0.2 = 0.05 match + 0.13 place
 2011-09-21 06:28:29.830 TVRec(1): ASK_RECORDING 1 29 0 0
 2011-09-21 06:29:01.245 TVRec(1): Changing from None to RecordingOnly
 2011-09-21 06:29:01.355 TVRec(1): HW Tuner: 1->1
 2011-09-21 06:29:01.453 AutoExpire: CalcParams(): Max required Free Space: 3.0 GB w/freq: 14 min
 2011-09-21 06:29:01.505 Started recording: "SHOW4 (Manual Record)":"Wed Sep 21 06:30:00 2011": channel 11791 on cardid 1, sourceid 1
 2011-09-21 06:29:01.552 scheduler: Started recording: "SHOW4 (Manual Record)":"Wed Sep 21 06:30:00 2011": channel 11791 on cardid 1, sourceid 1
 2011-09-21 06:29:02.462 DVBSH(/dev/dvb/adapter0/frontend0) Warning: Opening DVR device /dev/dvb/adapter0/dvr0 failed : Device or resource busy
 2011-09-21 06:29:02.554 DVBSH(/dev/dvb/adapter0/frontend0) Warning: Opening DVR device /dev/dvb/adapter0/dvr0 failed : Device or resource busy
 2011-09-21 06:29:02.646 DVBSH(/dev/dvb/adapter0/frontend0) Warning: Opening DVR device /dev/dvb/adapter0/dvr0 failed : Device or resource busy
 2011-09-21 06:29:02.738 DVBSH(/dev/dvb/adapter0/frontend0) Warning: Opening DVR device /dev/dvb/adapter0/dvr0 failed : Device or resource busy
 2011-09-21 06:29:02.830 DVBSH(/dev/dvb/adapter0/frontend0) Warning: Opening DVR device /dev/dvb/adapter0/dvr0 failed : Device or resource busy
 2011-09-21 06:29:02.921 DVBSH(/dev/dvb/adapter0/frontend0) Warning: Opening DVR device /dev/dvb/adapter0/dvr0 failed : Device or resource busy
 2011-09-21 06:29:03.013 DVBSH(/dev/dvb/adapter0/frontend0) Warning: Opening DVR device /dev/dvb/adapter0/dvr0 failed : Device or resource busy
 2011-09-21 06:29:03.105 DVBSH(/dev/dvb/adapter0/frontend0) Warning: Opening DVR device /dev/dvb/adapter0/dvr0 failed : Device or resource busy
 2011-09-21 06:29:03.197 DVBSH(/dev/dvb/adapter0/frontend0) Warning: Opening DVR device /dev/dvb/adapter0/dvr0 failed : Device or resource busy
 2011-09-21 06:29:03.280 DVBSH(/dev/dvb/adapter0/frontend0) Warning: Opening DVR device /dev/dvb/adapter0/dvr0 failed : Device or resource busy
 2011-09-21 06:29:03.363 DVBSH(/dev/dvb/adapter0/frontend0) Warning: Opening DVR device /dev/dvb/adapter0/dvr0 failed : Device or resource busy
 2011-09-21 06:29:03.447 DVBSH(/dev/dvb/adapter0/frontend0) Warning: Opening DVR device /dev/dvb/adapter0/dvr0 failed : Device or resource busy
 2011-09-21 06:29:03.530 DVBSH(/dev/dvb/adapter0/frontend0) Warning: Opening DVR device /dev/dvb/adapter0/dvr0 failed : Device or resource busy
 2011-09-21 06:29:03.614 DVBSH(/dev/dvb/adapter0/frontend0) Warning: Opening DVR device /dev/dvb/adapter0/dvr0 failed : Device or resource busy
 2011-09-21 06:29:03.697 DVBSH(/dev/dvb/adapter0/frontend0) Warning: Opening DVR device /dev/dvb/adapter0/dvr0 failed : Device or resource busy
 2011-09-21 06:29:03.781 DVBSH(/dev/dvb/adapter0/frontend0) Warning: Opening DVR device /dev/dvb/adapter0/dvr0 failed : Device or resource busy
 2011-09-21 06:29:03.864 DVBSH(/dev/dvb/adapter0/frontend0) Warning: Opening DVR device /dev/dvb/adapter0/dvr0 failed : Device or resource busy
 2011-09-21 06:29:03.947 DVBSH(/dev/dvb/adapter0/frontend0) Warning: Opening DVR device /dev/dvb/adapter0/dvr0 failed : Device or resource busy
 2011-09-21 06:29:04.031 DVBSH(/dev/dvb/adapter0/frontend0) Warning: Opening DVR device /dev/dvb/adapter0/dvr0 failed : Device or resource busy
 2011-09-21 06:29:04.114 DVBSH(/dev/dvb/adapter0/frontend0) Warning: Opening DVR device /dev/dvb/adapter0/dvr0 failed : Device or resource busy
 2011-09-21 06:29:04.148 DVBSH(/dev/dvb/adapter0/frontend0): Failed to open DVR device /dev/dvb/adapter0/dvr0 : Device or resource busy
 2011-09-21 06:32:09.902 AutoExpire: CalcParams(): Max required Free Space: 3.0 GB w/freq: 14 min
 2011-09-21 06:46:10.627 AutoExpire: CalcParams(): Max required Free Space: 3.0 GB w/freq: 14 min
 2011-09-21 06:55:30.668 TVRec(1): Changing from RecordingOnly to None
 2011-09-21 06:55:30.722 Updating status for "SHOW4 (Manual Record)":"Wed Sep 21 06:30:00 2011" on cardid 1 (Tuning => Recorder Failed)
 2011-09-21 06:55:30.764 Reschedule requested for id 0.
 2011-09-21 06:55:30.935 Scheduled 50 items in 0.2 = 0.03 match + 0.14 place
 2011-09-21 06:55:30.945 Preview Error: Encountered problems running '/usr/bin/mythpreviewgen --size 0x0 --chanid 11791 --starttime 20110921062900  > /dev/null'
 2011-09-21 06:55:30.969 scheduler: Scheduled items: Scheduled 50 items in 0.2 = 0.03 match + 0.14 place
 2011-09-21 07:00:11.153 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
 2011-09-21 07:15:11.877 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
 2011-09-21 07:17:01.695 MainServer::ANN Monitor
 2011-09-21 07:17:01.778 adding: htpc as a client (events: 2)
 2011-09-21 07:30:12.407 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
 2011-09-21 07:45:12.915 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
 2011-09-21 08:00:13.429 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
 2011-09-21 08:15:13.949 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
 2011-09-21 08:17:01.760 MainServer::ANN Monitor
 2011-09-21 08:17:01.861 adding: htpc as a client (events: 2)
 2011-09-21 08:30:14.453 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
 2011-09-21 08:45:14.965 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
 2011-09-21 09:00:15.477 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
 2011-09-21 09:15:16.001 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
 2011-09-21 09:17:01.778 MainServer::ANN Monitor
 2011-09-21 09:17:01.847 adding: htpc as a client (events: 2)
 2011-09-21 09:30:16.516 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
 2011-09-21 09:45:17.023 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
 2011-09-21 10:00:17.553 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
 2011-09-21 10:15:18.062 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
 2011-09-21 10:17:01.763 MainServer::ANN Monitor
 2011-09-21 10:17:01.851 adding: htpc as a client (events: 2)
 2011-09-21 10:30:18.586 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
 2011-09-21 10:45:19.105 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
 2011-09-21 10:58:00.458 Reschedule requested for id 0.
 2011-09-21 10:58:00.626 Scheduled 50 items in 0.2 = 0.04 match + 0.13 place
 2011-09-21 10:58:00.669 scheduler: Scheduled items: Scheduled 50 items in 0.2 = 0.04 match + 0.13 place
 2011-09-21 10:58:30.293 TVRec(1): ASK_RECORDING 1 29 0 0
 2011-09-21 10:59:01.756 TVRec(1): Changing from None to RecordingOnly
 2011-09-21 10:59:01.811 TVRec(1): HW Tuner: 1->1
 2011-09-21 10:59:01.902 AutoExpire: CalcParams(): Max required Free Space: 3.0 GB w/freq: 14 min
 2011-09-21 10:59:01.962 Started recording: "SHOW5 (Manual Record)":"Wed Sep 21 11:00:00 2011": channel 11791 on cardid 1, sourceid 1
 2011-09-21 10:59:01.999 scheduler: Started recording: "SHOW5 (Manual Record)":"Wed Sep 21 11:00:00 2011": channel 11791 on cardid 1, sourceid 1
 2011-09-21 10:59:02.961 DVBSH(/dev/dvb/adapter0/frontend0) Warning: Opening DVR device /dev/dvb/adapter0/dvr0 failed : Device or resource busy
 2011-09-21 10:59:03.044 DVBSH(/dev/dvb/adapter0/frontend0) Warning: Opening DVR device /dev/dvb/adapter0/dvr0 failed : Device or resource busy
 2011-09-21 10:59:03.128 DVBSH(/dev/dvb/adapter0/frontend0) Warning: Opening DVR device /dev/dvb/adapter0/dvr0 failed : Device or resource busy
 2011-09-21 10:59:03.211 DVBSH(/dev/dvb/adapter0/frontend0) Warning: Opening DVR device /dev/dvb/adapter0/dvr0 failed : Device or resource busy
 2011-09-21 10:59:03.295 DVBSH(/dev/dvb/adapter0/frontend0) Warning: Opening DVR device /dev/dvb/adapter0/dvr0 failed : Device or resource busy
 2011-09-21 10:59:03.378 DVBSH(/dev/dvb/adapter0/frontend0) Warning: Opening DVR device /dev/dvb/adapter0/dvr0 failed : Device or resource busy
 2011-09-21 10:59:03.461 DVBSH(/dev/dvb/adapter0/frontend0) Warning: Opening DVR device /dev/dvb/adapter0/dvr0 failed : Device or resource busy
 2011-09-21 10:59:03.545 DVBSH(/dev/dvb/adapter0/frontend0) Warning: Opening DVR device /dev/dvb/adapter0/dvr0 failed : Device or resource busy
 2011-09-21 10:59:03.628 DVBSH(/dev/dvb/adapter0/frontend0) Warning: Opening DVR device /dev/dvb/adapter0/dvr0 failed : Device or resource busy
 2011-09-21 10:59:03.712 DVBSH(/dev/dvb/adapter0/frontend0) Warning: Opening DVR device /dev/dvb/adapter0/dvr0 failed : Device or resource busy
 2011-09-21 10:59:03.795 DVBSH(/dev/dvb/adapter0/frontend0) Warning: Opening DVR device /dev/dvb/adapter0/dvr0 failed : Device or resource busy
 2011-09-21 10:59:03.879 DVBSH(/dev/dvb/adapter0/frontend0) Warning: Opening DVR device /dev/dvb/adapter0/dvr0 failed : Device or resource busy
 2011-09-21 10:59:03.962 DVBSH(/dev/dvb/adapter0/frontend0) Warning: Opening DVR device /dev/dvb/adapter0/dvr0 failed : Device or resource busy
 2011-09-21 10:59:04.054 DVBSH(/dev/dvb/adapter0/frontend0) Warning: Opening DVR device /dev/dvb/adapter0/dvr0 failed : Device or resource busy
 2011-09-21 10:59:04.137 DVBSH(/dev/dvb/adapter0/frontend0) Warning: Opening DVR device /dev/dvb/adapter0/dvr0 failed : Device or resource busy
 2011-09-21 10:59:04.220 DVBSH(/dev/dvb/adapter0/frontend0) Warning: Opening DVR device /dev/dvb/adapter0/dvr0 failed : Device or resource busy
 2011-09-21 10:59:04.312 DVBSH(/dev/dvb/adapter0/frontend0) Warning: Opening DVR device /dev/dvb/adapter0/dvr0 failed : Device or resource busy
 2011-09-21 10:59:04.404 DVBSH(/dev/dvb/adapter0/frontend0) Warning: Opening DVR device /dev/dvb/adapter0/dvr0 failed : Device or resource busy
 2011-09-21 10:59:04.496 DVBSH(/dev/dvb/adapter0/frontend0) Warning: Opening DVR device /dev/dvb/adapter0/dvr0 failed : Device or resource busy
 2011-09-21 10:59:04.587 DVBSH(/dev/dvb/adapter0/frontend0) Warning: Opening DVR device /dev/dvb/adapter0/dvr0 failed : Device or resource busy
 2011-09-21 10:59:04.629 DVBSH(/dev/dvb/adapter0/frontend0): Failed to open DVR device /dev/dvb/adapter0/dvr0 : Device or resource busy
 2011-09-21 11:00:19.622 AutoExpire: CalcParams(): Max required Free Space: 3.0 GB w/freq: 14 min
 2011-09-21 11:14:20.348 AutoExpire: CalcParams(): Max required Free Space: 3.0 GB w/freq: 14 min
 2011-09-21 11:17:01.730 MainServer::ANN Monitor
 2011-09-21 11:17:01.803 adding: htpc as a client (events: 2)
 2011-09-21 11:28:20.843 AutoExpire: CalcParams(): Max required Free Space: 3.0 GB w/freq: 14 min
 2011-09-21 11:30:30.154 TVRec(1): Changing from RecordingOnly to None
 2011-09-21 11:30:30.224 Updating status for "SHOW5 (Manual Record)":"Wed Sep 21 11:00:00 2011" on cardid 1 (Tuning => Recorder Failed)
 2011-09-21 11:30:30.269 Reschedule requested for id 0.
 2011-09-21 11:30:30.367 Preview Error: Encountered problems running '/usr/bin/mythpreviewgen --size 0x0 --chanid 11791 --starttime 20110921105900  > /dev/null'
 2011-09-21 11:30:30.460 Scheduled 49 items in 0.2 = 0.04 match + 0.15 place
 2011-09-21 11:30:30.508 scheduler: Scheduled items: Scheduled 49 items in 0.2 = 0.04 match + 0.15 place
 2011-09-21 11:42:21.353 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
 2011-09-21 11:57:22.062 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
 2011-09-21 12:12:22.578 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
 2011-09-21 12:17:01.735 MainServer::ANN Monitor
 2011-09-21 12:17:01.810 adding: htpc as a client (events: 2)
 2011-09-21 12:27:23.088 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
 2011-09-21 12:42:23.610 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
 2011-09-21 12:44:01.163 mythbackend: Last message repeated 116 times: Running housekeeping thread
 2011-09-21 12:44:01.211 mythbackend: Running mythfilldatabase
 2011-09-21 12:44:01.254 Running mythfilldatabase
 2011-09-21 12:44:01.406 Using runtime prefix = /usr
 2011-09-21 12:44:01.455 Using configuration directory = /home/mythtv/.mythtv
 2011-09-21 12:44:01.489 Empty LocalHostName.
 2011-09-21 12:44:01.521 Using localhost value of htpc
 2011-09-21 12:44:01.561 New DB connection, total: 1
 2011-09-21 12:44:01.601 Connected to database 'mythconverg' at host: localhost
 2011-09-21 12:44:01.638 Closing DB connection named 'DBManager0'
 2011-09-21 12:44:01.674 Connected to database 'mythconverg' at host: localhost
 2011-09-21 12:44:01.708 Current locale EN_US
 2011-09-21 12:44:01.740 Reading locale defaults from /usr/share/mythtv//locales/en_us.xml
 2011-09-21 12:44:01.778 Loading en_us translation for module mythfrontend
 2011-09-21 12:44:01.808 Current MythTV Schema Version (DBSchemaVer): 1264
 2011-09-21 12:44:01.844 mythfilldatabase: Listings Download Started
 2011-09-21 12:44:01.874 New DB connection, total: 2
 2011-09-21 12:44:01.907 Connected to database 'mythconverg' at host: localhost
 2011-09-21 12:44:01.941 Source 1 configured to use only the broadcasted guide data. Skipping.
 2011-09-21 12:44:01.985 Data fetching complete.
 2011-09-21 12:44:02.016 Adjusting program database end times.
 2011-09-21 12:44:02.084     0 replacements made
 2011-09-21 12:44:02.143 mythfilldatabase: Listings Download Finished
 2011-09-21 12:44:02.174 Marking generic episodes.
 2011-09-21 12:44:02.208     Found 0
 2011-09-21 12:44:02.241 Fudging non-unique programids with multiple parts.
 2011-09-21 12:44:02.275     Found 0
 2011-09-21 12:44:02.308 Marking repeats.
 2011-09-21 12:44:02.343     Found 0
 2011-09-21 12:44:02.375 Unmarking new episode rebroadcast repeats.
 2011-09-21 12:44:02.409     Found 0
 2011-09-21 12:44:02.443 Marking episode first showings.
 2011-09-21 12:44:02.521     Found 54
 2011-09-21 12:44:02.550 Marking episode last showings.
 2011-09-21 12:44:02.629     Found 54
 2011-09-21 12:44:02.668  
 ===============================================================
 | Attempting to contact the master backend for rescheduling.  |
 | If the master is not running, rescheduling will happen when |
 | the master backend is restarted.                            |
 ===============================================================

---

### Post by iiwii on 2011-09-27
Bump. Still need help.  It crashed again today...

Today's log.  
Of 5 recordings - 0 complete. 
Of almost 2 and 1/2 half hours of recording - only the first 15 minutes.

2011-09-27 04:59:02.173 AutoExpire: CalcParams(): Max required Free Space: 3.0 GB w/freq: 14 min
2011-09-27 04:59:02.221 Started recording: "SHOW1 (Manual Record)":"Tue Sep 27 05:00:00 2011": channel 11791 on cardid 1, sourceid 1
2011-09-27 04:59:02.258 scheduler: Started recording: "SHOW1 (Manual Record)":"Tue Sep 27 05:00:00 2011": channel 11791 on cardid 1, sourceid 1
2011-09-27 04:59:03.496 Updating status for "SHOW1 (Manual Record)":"Tue Sep 27 05:00:00 2011" on cardid 1 (Tuning => Recording)
2011-09-27 04:59:03.738 TVRec(1): rec->GetPathname(): '/var/lib/mythtv/recordings/11791_20110927045900.mpg'
2011-09-27 05:08:46.613 AutoExpire: CalcParams(): Max required Free Space: 3.0 GB w/freq: 14 min
2011-09-27 05:17:01.374 MainServer::ANN Monitor
2011-09-27 05:17:01.433 adding: htpc as a client (events: 2)
2011-09-27 05:22:47.421 AutoExpire: CalcParams(): Max required Free Space: 3.0 GB w/freq: 14 min
2011-09-27 05:25:30.681 TVRec(1): Changing from RecordingOnly to None
2011-09-27 05:25:30.735 Updating status for "SHOW1  (Manual Record)":"Tue Sep 27 05:00:00 2011" on cardid 1 (Recording => Recorded)
2011-09-27 05:25:30.740 Finished recording SHOW1 (Manual Record) "Tue Sep 27 05:00:00 2011": channel 11791
2011-09-27 05:25:30.786 Reschedule requested for id 0.
2011-09-27 05:25:30.833 scheduler: Finished recording: SHOW1 (Manual Record) "Tue Sep 27 05:00:00 2011": channel 11791
2011-09-27 05:25:31.037 Scheduled 53 items in 0.2 = 0.08 match + 0.17 place
2011-09-27 05:25:31.081 scheduler: Scheduled items: Scheduled 53 items in 0.2 = 0.08 match + 0.17 place
2011-09-27 05:28:00.159 Reschedule requested for id 0.
2011-09-27 05:28:00.336 Scheduled 53 items in 0.2 = 0.04 match + 0.13 place
2011-09-27 05:28:00.379 scheduler: Scheduled items: Scheduled 53 items in 0.2 = 0.04 match + 0.13 place
2011-09-27 05:36:48.183 AutoExpire: CalcParams(): Max required Free Space: 3.0 GB w/freq: 14 min
2011-09-27 05:50:48.949 AutoExpire: CalcParams(): Max required Free Space: 3.0 GB w/freq: 14 min
2011-09-27 06:04:49.508 AutoExpire: CalcParams(): Max required Free Space: 3.0 GB w/freq: 14 min
2011-09-27 06:17:01.374 MainServer::ANN Monitor
2011-09-27 06:17:01.438 adding: htpc as a client (events: 2)
2011-09-27 06:18:50.060 AutoExpire: CalcParams(): Max required Free Space: 3.0 GB w/freq: 14 min
2011-09-27 06:32:50.623 AutoExpire: CalcParams(): Max required Free Space: 3.0 GB w/freq: 14 min
2011-09-27 06:46:51.176 AutoExpire: CalcParams(): Max required Free Space: 3.0 GB w/freq: 14 min
2011-09-27 07:00:51.743 AutoExpire: CalcParams(): Max required Free Space: 3.0 GB w/freq: 14 min
2011-09-27 07:14:52.293 AutoExpire: CalcParams(): Max required Free Space: 3.0 GB w/freq: 14 min
2011-09-27 07:17:02.024 MainServer::ANN Monitor
2011-09-27 07:17:02.088 adding: htpc as a client (events: 2)
2011-09-27 07:28:52.850 AutoExpire: CalcParams(): Max required Free Space: 3.0 GB w/freq: 14 min
2011-09-27 07:42:53.409 AutoExpire: CalcParams(): Max required Free Space: 3.0 GB w/freq: 14 min
2011-09-27 07:56:53.964 AutoExpire: CalcParams(): Max required Free Space: 3.0 GB w/freq: 14 min
2011-09-27 08:10:54.523 AutoExpire: CalcParams(): Max required Free Space: 3.0 GB w/freq: 14 min
2011-09-27 08:17:01.672 MainServer::ANN Monitor
2011-09-27 08:17:01.752 adding: htpc as a client (events: 2)
2011-09-27 08:24:55.088 AutoExpire: CalcParams(): Max required Free Space: 3.0 GB w/freq: 14 min
2011-09-27 08:38:55.631 AutoExpire: CalcParams(): Max required Free Space: 3.0 GB w/freq: 14 min
2011-09-27 08:52:56.198 AutoExpire: CalcParams(): Max required Free Space: 3.0 GB w/freq: 14 min
2011-09-27 09:06:56.743 AutoExpire: CalcParams(): Max required Free Space: 3.0 GB w/freq: 14 min
2011-09-27 09:17:02.313 MainServer::ANN Monitor
2011-09-27 09:17:02.371 adding: htpc as a client (events: 2)
2011-09-27 09:20:57.288 AutoExpire: CalcParams(): Max required Free Space: 3.0 GB w/freq: 14 min
2011-09-27 09:34:57.854 AutoExpire: CalcParams(): Max required Free Space: 3.0 GB w/freq: 14 min
2011-09-27 09:48:58.408 AutoExpire: CalcParams(): Max required Free Space: 3.0 GB w/freq: 14 min
2011-09-27 10:02:58.957 AutoExpire: CalcParams(): Max required Free Space: 3.0 GB w/freq: 14 min
2011-09-27 10:16:59.516 AutoExpire: CalcParams(): Max required Free Space: 3.0 GB w/freq: 14 min
2011-09-27 10:17:01.935 MainServer::ANN Monitor
2011-09-27 10:17:01.988 adding: htpc as a client (events: 2)
2011-09-27 10:31:00.057 AutoExpire: CalcParams(): Max required Free Space: 3.0 GB w/freq: 14 min
2011-09-27 10:45:00.610 AutoExpire: CalcParams(): Max required Free Space: 3.0 GB w/freq: 14 min
2011-09-27 10:59:01.152 AutoExpire: CalcParams(): Max required Free Space: 3.0 GB w/freq: 14 min
2011-09-27 11:13:01.698 AutoExpire: CalcParams(): Max required Free Space: 3.0 GB w/freq: 14 min
2011-09-27 11:17:01.574 Waiting for a process request thread.. 
2011-09-27 11:17:01.645 Adding a new process request thread
2011-09-27 11:17:01.686 MainServer::ANN Monitor
2011-09-27 11:17:01.727 adding: htpc as a client (events: 2)
2011-09-27 11:27:02.266 AutoExpire: CalcParams(): Max required Free Space: 3.0 GB w/freq: 14 min
2011-09-27 11:41:02.822 AutoExpire: CalcParams(): Max required Free Space: 3.0 GB w/freq: 14 min
2011-09-27 11:55:03.382 AutoExpire: CalcParams(): Max required Free Space: 3.0 GB w/freq: 14 min
2011-09-27 12:09:03.934 AutoExpire: CalcParams(): Max required Free Space: 3.0 GB w/freq: 14 min
2011-09-27 12:17:07.965 mythbackend version: fixes/0.24 [v0.24-243-g9ba3ece] [www.mythtv.org](www.mythtv.org)
2011-09-27 12:17:08.667 Using runtime prefix = /usr
2011-09-27 12:17:08.985 Using configuration directory = /home/mythtv/.mythtv
2011-09-27 12:17:09.188 Empty LocalHostName.
2011-09-27 12:17:09.296 Using localhost value of htpc
2011-09-27 12:17:09.493 New DB connection, total: 1

---

