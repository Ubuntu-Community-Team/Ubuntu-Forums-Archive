---
title: "SA8300 HD Help"
date: 2008-04-12
forum: Mythbuntu
---

### Post by Robby23 on 2008-04-12
Alright well I followed this tutorial to the best of my ability:
[https://help.ubuntu.com/community/MythTV_Firewire](https://help.ubuntu.com/community/MythTV_Firewire)

Plugreport outputs this:
```
Host Adapter 0
==============

Node 0 GUID 0x324fc0000f314d01
------------------------------
libiec61883 error: error reading oMPR
libiec61883 error: error reading iMPR

Node 1 GUID 0x001cea152f780000
------------------------------
oMPR n_plugs=1, data_rate=2, bcast_channel=63
oPCR[0] online=1, bcast_connection=0, n_p2p_connections=1
        channel=1, data_rate=1, overhead_id=0, payload=146
iMPR n_plugs=0, data_rate=2

```

The command "sudo ./firewire_tester -p -P 0 -n 1 -r 5" outputs this

```
Action: Test P2P connection 5 times, node 1, channel 1
P2P: Testing...Success, 317 packets received
P2P: Testing...Success, 303 packets received
P2P: Testing...Success, 335 packets received
P2P: Testing...Success, 302 packets received
P2P: Testing...Success, 343 packets received

```

I'm having problems setting up mythbuntu.  I'm pretty new to this so I'm not even sure how to record but I ran MythTV Backend Setup with the following settings:

Card Type: Firewire
Cable box model: other (wasnt sure since I have the SA8300)
IEEE-1394 Port:0
Node:1
Speed:400mbps

When I go to channel editor to scan for channels it says failed to open card.

Any help would be appreciated.  Thanks.

On a side note, I am able to record in Windows with the program TSReader.  The only thing I'm able to record on Windows is already recorded programs while playing it back.  The reason why I'm trying to switch to linux is because I was told the firewire support is much better and would prevent less lost packets

---

### Post by grytpype on 2008-04-12
If I understand what you did correctly... you don't need to "scan for channels" using a Firewire input, in fact it won't work.  All you need to do is Fetch Lineup, and set the channel to a known-good one (i.e., one that is not encrypted or otherwise blocked).

---

### Post by Robby23 on 2008-04-12
> **grytpype said:**
> If I understand what you did correctly... you don't need to "scan for channels" using a Firewire input, in fact it won't work.  All you need to do is Fetch Lineup, and set the channel to a known-good one (i.e., one that is not encrypted or otherwise blocked).

Thanks for responding.

Is there a way to just view live tv?  When I do fetch channels nothing seems to happen.  The only thing that I'm able to record on windows at least was stuff already recorded on the dvr.  Thats fine with me I'm just not sure how to record that with mythtv

---

### Post by grytpype on 2008-04-12
Did you set up a lineup in Schedules Direct, and all that stuff?  You should have some channels!

---

### Post by Robby23 on 2008-04-16
Good news I got it working!

I just had to add channels with the Schedules Direct thing which I wasnt aware of before.

---

### Post by Robby23 on 2008-04-17
Alright well I got the recording down.  I can only record things played back from the dvr that were previously recorded so I have to just record live tv which isnt a problem for me.  My problem is that it will only record a maximum of 15 mins then it will stop recording all on its own.  I even tried scheduling a manual recording on channel 1000 (which is the channel previously recorded things play on) and I make it so its supposed to record for an hour but instead it still only records 15 mins then cuts off.  Anyone have any idea why?

---

### Post by majoridiot on 2008-04-17
> **Robby23 said:**
> Alright well I got the recording down.  I can only record things played back from the dvr that were previously recorded so I have to just record live tv which isnt a problem for me.  My problem is that it will only record a maximum of 15 mins then it will stop recording all on its own.  I even tried scheduling a manual recording on channel 1000 (which is the channel previously recorded things play on) and I make it so its supposed to record for an hour but instead it still only records 15 mins then cuts off.  Anyone have any idea why?

check your backend log and see if it gives you any clues as to what is happening. 

you can find it in /var/log/mythtv/mythbackend.log

---

### Post by Robby23 on 2008-04-17
> **majoridiot said:**
> check your backend log and see if it gives you any clues as to what is happening. 

you can find it in /var/log/mythtv/mythbackend.log

Thanks for the help so far.  For some reason now the command

$ sudo ./firewire_tester -p -P 0 -n 1 -r 5

outputs:

Action: Test P2P connection 5 times, node 1, channel 1
P2P: Testing...Failed
P2P: Testing...Failed
P2P: Testing...Failed
P2P: Testing...Failed
P2P: Testing...Failed

Now I'm unable to record at all.  I can't think of anything I did differently.  I'm able to record on windows still so it must be a problem with mythtv.

Here are the contents of /var/log/mythtv/mythbackend.log if it helps.

```
2008-04-17 00:35:50.481 TVRec(1): Changing from WatchingLiveTV to None
2008-04-17 00:35:50.624 Finished recording Unknown: channel 1849
2008-04-17 00:36:47.357 Reschedule requested for id 0.
2008-04-17 00:36:47.372 Scheduled 0 items in 0.0 = 0.01 match + 0.01 place
2008-04-17 00:38:42.780 Expiring Unknown from Thu Apr 17 00:35:27 2008, 0 MBytes, forced expire (LiveTV recording)
2008-04-17 00:38:42.783 Expiring Unknown from Thu Apr 17 00:35:36 2008, 3 MBytes, forced expire (LiveTV recording)
2008-04-17 00:40:00.614 MainServer::HandleAnnounce Playback
2008-04-17 00:40:00.614 adding: robby-laptop as a client (events: 0)
2008-04-17 00:40:00.616 TVRec(1): Changing from None to WatchingLiveTV
2008-04-17 00:40:00.617 TVRec(1): HW Tuner: 1->1
libiec61883 warning: Overlayed connection on channel 0.
You may need to manually set the channel on the receiving node.
2008-04-17 00:40:00.815 FireRec: Buffered packets 2000 (8000 KB)
2008-04-17 00:40:18.185 TVRec(1): Changing from WatchingLiveTV to None
2008-04-17 00:40:18.271 Finished recording Unknown: channel 1849
2008-04-17 00:41:40.023 MainServer::HandleAnnounce Monitor
2008-04-17 00:41:40.023 adding: robby-laptop as a client (events: 0)
2008-04-17 00:41:40.024 MainServer::HandleAnnounce Monitor
2008-04-17 00:41:40.025 adding: robby-laptop as a client (events: 1)
2008-04-17 00:41:40.028 MainServer::HandleAnnounce Playback
2008-04-17 00:41:40.028 adding: robby-laptop as a client (events: 0)
2008-04-17 00:41:40.031 TVRec(1): Changing from None to WatchingLiveTV
2008-04-17 00:41:40.032 TVRec(1): HW Tuner: 1->1
libiec61883 warning: Overlayed connection on channel 0.
You may need to manually set the channel on the receiving node.
2008-04-17 00:41:40.176 FireRec: Buffered packets 2000 (8000 KB)
2008-04-17 00:41:46.700 TVRec(1): Changing from WatchingLiveTV to None
2008-04-17 00:41:46.734 Finished recording Unknown: channel 1849
2008-04-17 00:42:08.215 MainServer::HandleAnnounce Playback
2008-04-17 00:42:08.216 adding: robby-laptop as a client (events: 0)
2008-04-17 00:42:08.218 TVRec(1): Changing from None to WatchingLiveTV
2008-04-17 00:42:08.219 TVRec(1): HW Tuner: 1->1
libiec61883 warning: Overlayed connection on channel 0.
You may need to manually set the channel on the receiving node.
2008-04-17 00:42:08.362 FireRec: Buffered packets 2000 (8000 KB)
2008-04-17 00:42:24.762 TVRec(1): SetLiveRecording(1)
2008-04-17 00:42:24.769 TVRec(1): SetLiveRecording() -- record
2008-04-17 00:42:24.815 Scheduler: AddRecording() recid: 4
2008-04-17 00:42:24.849 Reschedule requested for id 4.
2008-04-17 00:42:25.287 Scheduled 1 items in 0.4 = 0.41 match + 0.02 place
2008-04-17 00:42:42.798 Expiring Unknown from Thu Apr 17 00:40:00 2008, 3 MBytes, forced expire (LiveTV recording)
2008-04-17 00:44:42.814 Expiring Unknown from Thu Apr 17 00:41:40 2008, 0 MBytes, forced expire (LiveTV recording)
2008-04-17 01:00:00.895 TVRec(1): Enabling Full LiveTV UI.
2008-04-17 01:00:02.009 Finished recording Unknown: channel 1849
2008-04-17 01:00:02.105 TVRec(1): Enabling Full LiveTV UI.
0: start_time: 116.863 duration: 94.923
1: start_time: 116.822 duration: 94.913
stream: start_time: 1298.024 duration: 1055.153 bitrate=3254 kb/s
2008-04-17 01:00:02.137 AFD: Opened codec 0x82aba10, id(MPEG2VIDEO) type(Video)
2008-04-17 01:00:02.138 AFD: Opened codec 0x82abd50, id(AC3) type(Audio)
[mpeg2video @ 0xb7305ce8]ac-tex damaged at 9 6
[mpeg2video @ 0xb7305ce8]00 motion_type at 3 7
[mpeg2video @ 0xb7305ce8]00 motion_type at 11 8
[mpeg2video @ 0xb7305ce8]00 motion_type at 12 9
[mpeg2video @ 0xb7305ce8]mb incr damaged
[mpeg2video @ 0xb7305ce8]00 motion_type at 27 11
[mpeg2video @ 0xb7305ce8]invalid mb type in P Frame at 8 12
[mpeg2video @ 0xb7305ce8]ac-tex damaged at 4 13
[mpeg2video @ 0xb7305ce8]00 motion_type at 7 14
[mpeg2video @ 0xb7305ce8]ac-tex damaged at 0 15
[mpeg2video @ 0xb7305ce8]00 motion_type at 12 16
[mpeg2video @ 0xb7305ce8]invalid mb type in P Frame at 12 17
[mpeg2video @ 0xb7305ce8]00 motion_type at 27 18
[mpeg2video @ 0xb7305ce8]ac-tex damaged at 1 19
[mpeg2video @ 0xb7305ce8]ac-tex damaged at 2 20
[mpeg2video @ 0xb7305ce8]ac-tex damaged at 3 21
[mpeg2video @ 0xb7305ce8]00 motion_type at 8 22
[mpeg2video @ 0xb7305ce8]invalid mb type in P Frame at 18 23
[mpeg2video @ 0xb7305ce8]00 motion_type at 9 24
[mpeg2video @ 0xb7305ce8]00 motion_type at 5 25
[mpeg2video @ 0xb7305ce8]00 motion_type at 5 26
[mpeg2video @ 0xb7305ce8]slice mismatch
[mpeg2video @ 0xb7305ce8]00 motion_type at 7 28
[mpeg2video @ 0xb7305ce8]00 motion_type at 4 29
2008-04-17 01:00:02.854 TVRec(1): RingBufferChanged()
2008-04-17 01:00:02.864 Finished recording Unknown: channel 1849
2008-04-17 01:00:02.872 Reschedule requested for id 0.
2008-04-17 01:00:02.883 Scheduled 0 items in 0.0 = 0.00 match + 0.01 place
2008-04-17 01:12:32.362 TVRec(1): SetLiveRecording(1)
2008-04-17 01:12:32.364 TVRec(1): SetLiveRecording() -- record
2008-04-17 01:12:32.403 Scheduler: AddRecording() recid: 5
2008-04-17 01:12:32.440 Reschedule requested for id 5.
2008-04-17 01:12:32.731 Scheduled 1 items in 0.3 = 0.29 match + 0.01 place
2008-04-17 01:12:33.846 TVRec(1): SetLiveRecording(0)
2008-04-17 01:12:33.848 TVRec(1): SetLiveRecording() -- cancel
2008-04-17 01:12:33.850 Reschedule requested for id 0.
2008-04-17 01:12:33.858 Scheduled 1 items in 0.0 = 0.00 match + 0.01 place
2008-04-17 01:12:37.143 TVRec(1): Changing from WatchingLiveTV to None
2008-04-17 01:12:37.191 Finished recording Unknown: channel 1849
2008-04-17 01:13:57.091 MainServer::HandleAnnounce Playback
2008-04-17 01:13:57.092 adding: robby-laptop as a client (events: 0)
2008-04-17 01:13:57.094 TVRec(1): Changing from None to WatchingLiveTV
2008-04-17 01:13:57.094 TVRec(1): HW Tuner: 1->1
libiec61883 warning: Overlayed connection on channel 0.
You may need to manually set the channel on the receiving node.
2008-04-17 01:13:57.218 FireRec: Buffered packets 2000 (8000 KB)
2008-04-17 01:14:02.592 TVRec(1): SetLiveRecording(1)
2008-04-17 01:14:02.595 TVRec(1): SetLiveRecording() -- record
2008-04-17 01:14:02.635 Scheduler: AddRecording() recid: 6
2008-04-17 01:14:02.661 Reschedule requested for id 6.
2008-04-17 01:14:02.998 Scheduled 2 items in 0.3 = 0.33 match + 0.01 place
2008-04-17 01:30:00.423 TVRec(1): Enabling Full LiveTV UI.
2008-04-17 01:30:01.542 Finished recording Unknown: channel 1849
0: start_time: 191.655 duration: 86.674
1: start_time: 191.604 duration: 86.674
stream: start_time: 2128.936 duration: 963.613 bitrate=3179 kb/s
2008-04-17 01:30:01.598 AFD: Opened codec 0x838c0e0, id(MPEG2VIDEO) type(Video)
2008-04-17 01:30:01.600 AFD: Opened codec 0x838c6e0, id(AC3) type(Audio)
2008-04-17 01:30:01.606 TVRec(1): Enabling Full LiveTV UI.
[mpeg2video @ 0xb7305ce8]00 motion_type at 1 26
[mpeg2video @ 0xb7305ce8]ac-tex damaged at 13 27
[mpeg2video @ 0xb7305ce8]00 motion_type at 3 28
[mpeg2video @ 0xb7305ce8]00 motion_type at 16 29
2008-04-17 01:30:01.832 TVRec(1): RingBufferChanged()
2008-04-17 01:30:01.839 Finished recording Unknown: channel 1849
2008-04-17 01:30:01.848 Reschedule requested for id 0.
2008-04-17 01:30:01.862 Scheduled 0 items in 0.0 = 0.00 match + 0.01 place
2008-04-17 01:30:26.666 TVRec(1): SetLiveRecording(1)
2008-04-17 01:30:26.669 TVRec(1): SetLiveRecording() -- record
2008-04-17 01:30:26.725 Scheduler: AddRecording() recid: 7
2008-04-17 01:30:26.750 Reschedule requested for id 7.
2008-04-17 01:30:27.176 Scheduled 1 items in 0.4 = 0.42 match + 0.01 place
2008-04-17 01:30:28.726 TVRec(1): Changing from WatchingLiveTV to RecordingOnly
2008-04-17 01:30:40.394 MainServer::HandleAnnounce Playback
2008-04-17 01:30:40.394 adding: robby-laptop as a client (events: 0)
2008-04-17 01:31:48.714 Reschedule requested for id 0.
2008-04-17 01:31:48.723 Scheduled 1 items in 0.0 = 0.00 match + 0.01 place
2008-04-17 01:33:00.155 MainServer::HandleAnnounce Monitor
2008-04-17 01:33:00.155 adding: robby-laptop as a client (events: 0)
2008-04-17 01:33:00.156 MainServer::HandleAnnounce Monitor
2008-04-17 01:33:00.157 adding: robby-laptop as a client (events: 1)
2008-04-17 01:36:19.314 MainServer::HandleAnnounce Monitor
2008-04-17 01:36:19.315 adding: robby-laptop as a client (events: 0)
2008-04-17 01:36:19.316 MainServer::HandleAnnounce Monitor
2008-04-17 01:36:19.316 adding: robby-laptop as a client (events: 1)
2008-04-17 01:36:47.984 MainServer::HandleAnnounce Playback
2008-04-17 01:36:47.984 adding: robby-laptop as a client (events: 0)
2008-04-17 01:37:13.487 TVRec(1): Changing from RecordingOnly to None
2008-04-17 01:37:13.639 Finished recording Unknown: channel 1849
2008-04-17 01:37:13.650 Reschedule requested for id 0.
2008-04-17 01:37:13.659 Scheduled 1 items in 0.0 = 0.00 match + 0.01 place
0: start_time: 278.537 duration: 8580.197
1: start_time: 278.479 duration: 8580.200
stream: start_time: 3094.216 duration: 95336.162 bitrate=6 kb/s
2008-04-17 01:37:13.676 AFD: Opened codec 0x838a8d0, id(MPEG2VIDEO) type(Video)
2008-04-17 01:37:13.678 AFD: Opened codec 0x824da90, id(AC3) type(Audio)
[mpeg2video @ 0xb7305ce8]invalid cbp at 8 28
[mpeg2video @ 0xb7305ce8]ac-tex damaged at 5 28
[mpeg2video @ 0xb7305ce8]end mismatch left=297 3123B0
2008-04-17 01:37:20.078 Reschedule requested for id 0.
2008-04-17 01:37:20.085 Scheduled 1 items in 0.0 = 0.00 match + 0.01 place
2008-04-17 01:37:26.110 Reschedule requested for id 0.
2008-04-17 01:37:26.119 Scheduled 1 items in 0.0 = 0.00 match + 0.01 place
2008-04-17 01:38:45.682 MainServer::HandleAnnounce Playback
2008-04-17 01:38:45.683 adding: robby-laptop as a client (events: 0)
2008-04-17 01:38:45.685 TVRec(1): Changing from None to WatchingLiveTV
2008-04-17 01:38:45.686 TVRec(1): HW Tuner: 1->1
libiec61883 warning: Overlayed connection on channel 0.
You may need to manually set the channel on the receiving node.
2008-04-17 01:38:45.858 FireRec: Buffered packets 2000 (8000 KB)
2008-04-17 01:39:09.686 TVRec(1): SetLiveRecording(1)
2008-04-17 01:39:09.689 TVRec(1): SetLiveRecording() -- record
2008-04-17 01:39:09.731 Scheduler: AddRecording() recid: 8
2008-04-17 01:39:09.766 Reschedule requested for id 8.
2008-04-17 01:39:10.164 Scheduled 2 items in 0.4 = 0.38 match + 0.02 place
2008-04-17 02:00:00.003 TVRec(1): Enabling Full LiveTV UI.
2008-04-17 02:00:01.072 Finished recording Unknown: channel 1849
2008-04-17 02:00:01.192 TVRec(1): Enabling Full LiveTV UI.
0: start_time: 268.862 duration: 760.900
1: start_time: 268.803 duration: 760.903
stream: start_time: 2986.696 duration: 8455.113 bitrate=480 kb/s
2008-04-17 02:00:01.195 AFD: Opened codec 0x8336770, id(MPEG2VIDEO) type(Video)
2008-04-17 02:00:01.198 AFD: Opened codec 0x83357b0, id(AC3) type(Audio)
[mpeg2video @ 0xb7305ce8]invalid mb type in P Frame at 3 27
[mpeg2video @ 0xb7305ce8]ac-tex damaged at 7 29
[mpeg2video @ 0xb7305ce8]ac-tex damaged at 3 29
2008-04-17 02:00:01.552 TVRec(1): RingBufferChanged()
2008-04-17 02:00:01.560 Finished recording Unknown: channel 1849
2008-04-17 02:00:01.571 Reschedule requested for id 0.
2008-04-17 02:00:01.582 Scheduled 0 items in 0.0 = 0.00 match + 0.01 place
2008-04-17 02:30:00.492 Finished recording Unknown: channel 1849
0: start_time: 1029.943 duration: 161.719
1: start_time: 1029.892 duration: 161.715
stream: start_time: 11443.250 duration: 1797.440 bitrate=3188 kb/s
2008-04-17 02:30:00.590 AFD: Opened codec 0x82c33d0, id(MPEG2VIDEO) type(Video)
2008-04-17 02:30:00.608 TVRec(1): Enabling Full LiveTV UI.
2008-04-17 02:30:00.612 AFD: Opened codec 0x82d3580, id(AC3) type(Audio)
[mpeg2video @ 0xb7305ce8]ac-tex damaged at 9 20
[mpeg2video @ 0xb7305ce8]ac-tex damaged at 14 22
[mpeg2video @ 0xb7305ce8]ac-tex damaged at 27 22
[mpeg2video @ 0xb7305ce8]ac-tex damaged at 19 24
[mpeg2video @ 0xb7305ce8]invalid mb type in P Frame at 21 24
[mpeg2video @ 0xb7305ce8]ac-tex damaged at 5 25
[mpeg2video @ 0xb7305ce8]ac-tex damaged at 1 26
[mpeg2video @ 0xb7305ce8]ac-tex damaged at 3 28
[mpeg2video @ 0xb7305ce8]ac-tex damaged at 12 28
[mpeg2video @ 0xb7305ce8]end mismatch left=54 642854
2008-04-17 02:30:00.882 TVRec(1): RingBufferChanged()
2008-04-17 02:30:00.899 Finished recording Unknown: channel 1849
2008-04-17 02:41:17.340 TVRec(1): SetLiveRecording(1)
2008-04-17 02:41:17.343 TVRec(1): SetLiveRecording() -- record
2008-04-17 02:41:17.512 Scheduler: AddRecording() recid: 9
2008-04-17 02:41:17.543 Reschedule requested for id 9.
2008-04-17 02:41:18.516 TVRec(1): SetLiveRecording(0)
2008-04-17 02:41:18.525 TVRec(1): SetLiveRecording() -- cancel
2008-04-17 02:41:19.680 Reschedule requested for id 0.
2008-04-17 02:41:19.713 Scheduled 1 items in 2.2 = 2.14 match + 0.03 place
2008-04-17 02:41:23.692 TVRec(1): Changing from WatchingLiveTV to None
2008-04-17 02:41:23.750 Finished recording Unknown: channel 1849
2008-04-17 02:42:21.202 Reschedule requested for id 0.
2008-04-17 02:42:21.211 Scheduled 1 items in 0.0 = 0.00 match + 0.01 place
2008-04-17 02:43:44.215 Reschedule requested for id 10.
2008-04-17 02:43:44.704 Scheduled 2 items in 0.5 = 0.47 match + 0.02 place
2008-04-17 02:44:09.642 MainServer::HandleAnnounce Playback
2008-04-17 02:44:09.642 adding: robby-laptop as a client (events: 0)
2008-04-17 02:44:09.644 TVRec(1): Changing from None to WatchingLiveTV
2008-04-17 02:44:09.645 TVRec(1): HW Tuner: 1->1
libiec61883 warning: Overlayed connection on channel 0.
You may need to manually set the channel on the receiving node.
2008-04-17 02:44:09.771 FireRec: Buffered packets 2000 (8000 KB)
2008-04-17 02:44:18.471 TVRec(1): Changing from WatchingLiveTV to None
2008-04-17 02:44:18.521 Finished recording Unknown: channel 1849
2008-04-17 02:45:02.827 TVRec(1): Changing from None to RecordingOnly
2008-04-17 02:45:02.831 TVRec(1): HW Tuner: 1->1
libiec61883 warning: Overlayed connection on channel 0.
You may need to manually set the channel on the receiving node.
2008-04-17 02:45:02.927 FireRec: Buffered packets 2000 (8000 KB)
2008-04-17 02:45:02.940 Started recording: Whose Line (Manual Record) "Thu Apr 17 02:45:00 2008": channel 1849 on cardid 1, sourceid 1
2008-04-17 02:46:43.670 Expiring Unknown from Thu Apr 17 02:44:09 2008, 2 MBytes, forced expire (LiveTV recording)
2008-04-17 03:01:24.401 FireRec: No Input in 15 seconds [P:0 N:1] (select)
2008-04-17 03:50:00.958 TVRec(1): Changing from RecordingOnly to None
2008-04-17 03:50:00.963 Finished recording Whose Line (Manual Record) "Thu Apr 17 02:45:00 2008": channel 1849
2008-04-17 03:50:00.966 Reschedule requested for id 0.
2008-04-17 03:50:00.975 Scheduled 0 items in 0.0 = 0.00 match + 0.01 place
0: start_time: 918.002 duration: 85.931
1: start_time: 917.944 duration: 85.928
stream: start_time: 10199.377 duration: 955.428 bitrate=3208 kb/s
2008-04-17 03:50:01.436 AFD: Opened codec 0x8304410, id(MPEG2VIDEO) type(Video)
2008-04-17 03:50:01.451 Finished recording Whose Line (Manual Record) "Thu Apr 17 02:45:00 2008": channel 1849
2008-04-17 03:50:01.454 AFD: Opened codec 0x83049d0, id(AC3) type(Audio)
2008-04-17 10:39:23.556 MainServer::HandleAnnounce Monitor
2008-04-17 10:39:23.557 adding: robby-laptop as a client (events: 0)
2008-04-17 10:39:23.558 MainServer::HandleAnnounce Monitor
2008-04-17 10:39:23.558 adding: robby-laptop as a client (events: 1)
2008-04-17 10:39:23.561 MainServer::HandleAnnounce Playback
2008-04-17 10:39:23.562 adding: robby-laptop as a client (events: 0)
2008-04-17 10:39:23.563 TVRec(1): Changing from None to WatchingLiveTV
2008-04-17 10:39:23.564 TVRec(1): HW Tuner: 1->1
libiec61883 warning: Established connection on channel 0.
You may need to manually set the channel on the receiving node.
2008-04-17 10:39:24.196 FireRec: Buffered packets 2000 (8000 KB)
2008-04-17 10:39:30.589 TVRec(1): Changing from WatchingLiveTV to None
2008-04-17 10:39:39.205 FireRec: No Input in 15 seconds [P:0 N:1] (select)
2008-04-17 10:39:39.216 Finished recording Unknown: channel 1849
2008-04-17 10:39:39.220 MythSocket(8203320:-1): writeStringList: Error, socket went unconnected.
2008-04-17 10:42:44.620 Expiring Unknown from Thu Apr 17 10:39:23 2008, 0 MBytes, forced expire (LiveTV recording)
2008-04-17 10:45:13.616 MainServer::HandleAnnounce Playback
2008-04-17 10:45:13.617 adding: robby-laptop as a client (events: 0)
2008-04-17 10:45:13.619 TVRec(1): Changing from None to WatchingLiveTV
2008-04-17 10:45:13.620 TVRec(1): HW Tuner: 1->1
libiec61883 warning: Overlayed connection on channel 0.
You may need to manually set the channel on the receiving node.
2008-04-17 10:45:13.747 FireRec: Buffered packets 2000 (8000 KB)
2008-04-17 10:45:20.256 TVRec(1): SetLiveRecording(1)
2008-04-17 10:45:20.261 TVRec(1): SetLiveRecording() -- record
2008-04-17 10:45:20.341 Scheduler: AddRecording() recid: 11
2008-04-17 10:45:20.396 Reschedule requested for id 11.
2008-04-17 10:45:21.099 Scheduled 1 items in 0.7 = 0.70 match + 0.01 place
2008-04-17 10:47:57.988 TVRec(1): SetLiveRecording(0)
2008-04-17 10:47:57.991 TVRec(1): SetLiveRecording() -- cancel
2008-04-17 10:47:57.994 Reschedule requested for id 0.
2008-04-17 10:47:58.002 Scheduled 1 items in 0.0 = 0.00 match + 0.01 place
2008-04-17 10:48:35.867 TVRec(1): Changing from WatchingLiveTV to None
2008-04-17 10:48:35.899 Finished recording Unknown: channel 1849
2008-04-17 10:49:11.174 MainServer::HandleAnnounce Playback
2008-04-17 10:49:11.175 adding: robby-laptop as a client (events: 0)
2008-04-17 10:49:11.177 TVRec(1): Changing from None to WatchingLiveTV
2008-04-17 10:49:11.178 TVRec(1): HW Tuner: 1->1
libiec61883 warning: Overlayed connection on channel 0.
You may need to manually set the channel on the receiving node.
2008-04-17 10:49:11.304 FireRec: Buffered packets 2000 (8000 KB)
2008-04-17 10:49:17.813 TVRec(1): Changing from WatchingLiveTV to None
2008-04-17 10:49:17.826 Finished recording Unknown: channel 1849
2008-04-17 10:49:34.860 Reschedule requested for id 0.
2008-04-17 10:49:34.868 Scheduled 1 items in 0.0 = 0.00 match + 0.01 place
2008-04-17 10:50:44.696 Expiring Unknown from Thu Apr 17 10:49:11 2008, 0 MBytes, forced expire (LiveTV recording)
2008-04-17 11:00:58.817 MainServer::HandleAnnounce Monitor
2008-04-17 11:00:58.817 adding: robby-laptop as a client (events: 0)
2008-04-17 11:00:58.818 MainServer::HandleAnnounce Monitor
2008-04-17 11:00:58.819 adding: robby-laptop as a client (events: 1)
2008-04-17 11:00:58.822 MainServer::HandleAnnounce Playback
2008-04-17 11:00:58.822 adding: robby-laptop as a client (events: 0)
2008-04-17 11:00:58.824 TVRec(1): Changing from None to WatchingLiveTV
2008-04-17 11:00:58.825 TVRec(1): HW Tuner: 1->1
libiec61883 warning: Overlayed connection on channel 0.
You may need to manually set the channel on the receiving node.
2008-04-17 11:00:58.957 FireRec: Buffered packets 2000 (8000 KB)
2008-04-17 11:01:05.470 TVRec(1): Changing from WatchingLiveTV to None
2008-04-17 11:01:13.587 MainServer::HandleAnnounce Playback
2008-04-17 11:01:13.588 adding: robby-laptop as a client (events: 0)
2008-04-17 11:01:13.969 FireRec: No Input in 15 seconds [P:0 N:1] (select)
2008-04-17 11:01:13.979 Finished recording Unknown: channel 1849
2008-04-17 11:01:13.982 TVRec(1): Changing from None to WatchingLiveTV
2008-04-17 11:01:13.984 TVRec(1): HW Tuner: 1->1
2008-04-17 11:01:14.098 MythSocket(82d5bd8:-1): writeStringList: Error, socket went unconnected.
libiec61883 warning: Overlayed connection on channel 0.
You may need to manually set the channel on the receiving node.
2008-04-17 11:01:14.108 FireRec: Buffered packets 2000 (8000 KB)
2008-04-17 11:01:20.608 TVRec(1): Changing from WatchingLiveTV to None
2008-04-17 11:01:29.129 FireRec: No Input in 15 seconds [P:0 N:1] (select)
2008-04-17 11:01:29.139 Finished recording Unknown: channel 1849
2008-04-17 11:01:29.145 MythSocket(825d610:-1): writeStringList: Error, socket went unconnected.
2008-04-17 11:01:41.659 MainServer::HandleAnnounce Playback
2008-04-17 11:01:41.660 adding: robby-laptop as a client (events: 0)
2008-04-17 11:01:41.662 TVRec(1): Changing from None to WatchingLiveTV
2008-04-17 11:01:41.663 TVRec(1): HW Tuner: 1->1
libiec61883 warning: Overlayed connection on channel 0.
You may need to manually set the channel on the receiving node.
2008-04-17 11:01:41.783 FireRec: Buffered packets 2000 (8000 KB)
2008-04-17 11:01:48.282 TVRec(1): Changing from WatchingLiveTV to None
2008-04-17 11:01:56.793 FireRec: No Input in 15 seconds [P:0 N:1] (select)
2008-04-17 11:01:56.803 Finished recording Unknown: channel 1849
2008-04-17 11:01:56.807 MythSocket(8318e80:-1): writeStringList: Error, socket went unconnected.
2008-04-17 11:02:44.728 Expiring Unknown from Thu Apr 17 11:00:58 2008, 0 MBytes, forced expire (LiveTV recording)
2008-04-17 11:02:44.730 Expiring Unknown from Thu Apr 17 11:01:14 2008, 0 MBytes, forced expire (LiveTV recording)
2008-04-17 11:04:44.738 Expiring Unknown from Thu Apr 17 11:01:41 2008, 0 MBytes, forced expire (LiveTV recording)
2008-04-17 11:13:53.867 MainServer::HandleAnnounce Monitor
2008-04-17 11:13:53.868 adding: robby-laptop as a client (events: 0)
2008-04-17 11:13:53.869 MainServer::HandleAnnounce Monitor
2008-04-17 11:13:53.870 adding: robby-laptop as a client (events: 1)
2008-04-17 11:13:53.873 MainServer::HandleAnnounce Playback
2008-04-17 11:13:53.873 adding: robby-laptop as a client (events: 0)
2008-04-17 11:13:53.875 TVRec(1): Changing from None to WatchingLiveTV
2008-04-17 11:13:53.876 TVRec(1): HW Tuner: 1->1
libiec61883 warning: Overlayed connection on channel 0.
You may need to manually set the channel on the receiving node.
2008-04-17 11:13:53.998 FireRec: Buffered packets 2000 (8000 KB)
2008-04-17 11:14:00.511 TVRec(1): Changing from WatchingLiveTV to None
2008-04-17 11:14:09.009 FireRec: No Input in 15 seconds [P:0 N:1] (select)
2008-04-17 11:14:09.018 Finished recording Unknown: channel 1849
2008-04-17 11:14:09.023 MythSocket(83546f0:-1): writeStringList: Error, socket went unconnected.
2008-04-17 11:16:20     firewire ownership released
2008-04-17 12:32:33     firewire ownership acquired
2008-04-17 12:32:33     priming firewire...
2008-04-17 12:32:33     BAD ERROR RETURNED? -- FIXME!!
2008-04-17 12:32:37.274 Using runtime prefix = /usr
2008-04-17 12:32:37.503 New DB connection, total: 1
2008-04-17 12:32:37.642 Connected to database 'mythconverg' at host: localhost
2008-04-17 12:32:37.821 Current Schema Version: 1160
Starting up as the master server.
2008-04-17 12:32:37.979 New DB connection, total: 2
2008-04-17 12:32:38.062 Connected to database 'mythconverg' at host: localhost
2008-04-17 12:32:38.162 EITHelper: localtime offset -4:00:00 
2008-04-17 12:32:38.518 New DB connection, total: 3
2008-04-17 12:32:38.534 Connected to database 'mythconverg' at host: localhost
2008-04-17 12:32:38.658 New DB scheduler connection
2008-04-17 12:32:38.659 Connected to database 'mythconverg' at host: localhost
2008-04-17 12:32:38.684 QMulticastSocket: setsockopt - IP_ADD_MEMBERSHIP Error
2008-04-17 12:32:38.750 QMulticastSocket: setsockopt - IP_ADD_MEMBERSHIP Error
2008-04-17 12:32:40.054 Main::Registering HttpStatus Extension
2008-04-17 12:32:40.064 mythbackend version: 0.20.20070821-1 www.mythtv.org
2008-04-17 12:32:40.162 Enabled verbose msgs:  important general
2008-04-17 12:32:40.084 QMulticastSocket: setsockopt - IP_ADD_MEMBERSHIP Error
2008-04-17 12:32:40.431 AutoExpire: Found 1 recorders w/max rate of 138 MiB/min
2008-04-17 12:32:40.432 AutoExpire: Required Free Space: 3.0 GB w/freq: 10 min
2008-04-17 12:32:40.946 Reschedule requested for id -1.
2008-04-17 12:32:45.369 Scheduled 0 items in 4.4 = 4.38 match + 0.04 place
2008-04-17 12:32:45.372 Seem to be woken up by USER
2008-04-17 15:14:05.804 MainServer::HandleAnnounce Monitor
2008-04-17 15:14:05.810 adding: robby-laptop as a client (events: 0)
2008-04-17 15:14:05.811 MainServer::HandleAnnounce Monitor
2008-04-17 15:14:05.811 adding: robby-laptop as a client (events: 1)
2008-04-17 15:14:05.812 Reloading backend settings
2008-04-17 15:15:54.923 Reschedule requested for id 0.
2008-04-17 15:15:54.952 Scheduled 0 items in 0.0 = 0.00 match + 0.03 place
2008-04-17 15:16:02.263 Reschedule requested for id 0.
2008-04-17 15:16:02.308 Scheduled 0 items in 0.0 = 0.00 match + 0.04 place
2008-04-17 15:16:46.581 MainServer::HandleAnnounce Playback
2008-04-17 15:16:46.582 adding: robby-laptop as a client (events: 0)
2008-04-17 15:16:46.602 TVRec(1): Changing from None to WatchingLiveTV
2008-04-17 15:16:46.602 TVRec(1): HW Tuner: 1->1
libiec61883 warning: Established connection on channel 0.
You may need to manually set the channel on the receiving node.
2008-04-17 15:16:47.077 FireRec: Buffered packets 2000 (8000 KB)
2008-04-17 15:16:53.654 TVRec(1): Changing from WatchingLiveTV to None
2008-04-17 15:17:02.090 FireRec: No Input in 15 seconds [P:0 N:1] (select)
2008-04-17 15:17:02.102 Finished recording Unknown: channel 1849
2008-04-17 15:17:02.106 MythSocket(8178790:-1): writeStringList: Error, socket went unconnected.
2008-04-17 15:17:03.445 MainServer::HandleAnnounce Playback
2008-04-17 15:17:03.446 adding: robby-laptop as a client (events: 0)
2008-04-17 15:17:03.448 TVRec(1): Changing from None to WatchingLiveTV
2008-04-17 15:17:03.449 TVRec(1): HW Tuner: 1->1
libiec61883 warning: Overlayed connection on channel 0.
You may need to manually set the channel on the receiving node.
2008-04-17 15:17:03.575 FireRec: Buffered packets 2000 (8000 KB)
2008-04-17 15:17:10.075 TVRec(1): Changing from WatchingLiveTV to None
2008-04-17 15:17:18.586 FireRec: No Input in 15 seconds [P:0 N:1] (select)
2008-04-17 15:17:18.595 Finished recording Unknown: channel 1849
2008-04-17 15:17:18.599 MythSocket(81a6090:-1): writeStringList: Error, socket went unconnected.
2008-04-17 15:17:31     firewire ownership released
2008-04-17 15:20:58     firewire ownership acquired
2008-04-17 15:20:58     priming firewire...
2008-04-17 15:20:58     BAD ERROR RETURNED? -- FIXME!!
2008-04-17 15:21:02.013 Using runtime prefix = /usr
2008-04-17 15:21:02.026 New DB connection, total: 1
2008-04-17 15:21:02.032 Connected to database 'mythconverg' at host: localhost
2008-04-17 15:21:02.034 Current Schema Version: 1160
Starting up as the master server.
2008-04-17 15:21:02.043 New DB connection, total: 2
2008-04-17 15:21:02.043 Connected to database 'mythconverg' at host: localhost
2008-04-17 15:21:02.045 EITHelper: localtime offset -4:00:00 
2008-04-17 15:21:02.050 New DB connection, total: 3
2008-04-17 15:21:02.051 Connected to database 'mythconverg' at host: localhost
2008-04-17 15:21:02.144 New DB scheduler connection
2008-04-17 15:21:02.145 Connected to database 'mythconverg' at host: localhost
2008-04-17 15:21:03.470 Main::Registering HttpStatus Extension
2008-04-17 15:21:03.471 mythbackend version: 0.20.20070821-1 www.mythtv.org
2008-04-17 15:21:03.471 Enabled verbose msgs:  important general
2008-04-17 15:21:03.471 AutoExpire: Found 1 recorders w/max rate of 138 MiB/min
2008-04-17 15:21:03.473 AutoExpire: Required Free Space: 3.0 GB w/freq: 10 min
2008-04-17 15:21:04.149 Reschedule requested for id -1.
2008-04-17 15:21:04.466 Scheduled 0 items in 0.3 = 0.30 match + 0.01 place
2008-04-17 15:21:04.469 Seem to be woken up by USER
2008-04-17 15:22:22.152 Expiring Unknown from Thu Apr 17 15:16:46 2008, 0 MBytes, forced expire (LiveTV recording)
2008-04-17 15:22:22.155 Expiring Unknown from Thu Apr 17 15:17:03 2008, 0 MBytes, forced expire (LiveTV recording)
2008-04-17 15:25:29     firewire ownership released
2008-04-17 15:26:41     firewire ownership acquired
2008-04-17 15:26:41     priming firewire...
2008-04-17 15:26:41     BAD ERROR RETURNED? -- FIXME!!
2008-04-17 15:26:45.168 Using runtime prefix = /usr
2008-04-17 15:26:45.385 New DB connection, total: 1
2008-04-17 15:26:45.404 Connected to database 'mythconverg' at host: localhost
2008-04-17 15:26:45.587 Current Schema Version: 1160
Starting up as the master server.
2008-04-17 15:26:45.784 New DB connection, total: 2
2008-04-17 15:26:45.955 Connected to database 'mythconverg' at host: localhost
2008-04-17 15:26:46.012 EITHelper: localtime offset -4:00:00 
2008-04-17 15:26:46.111 New DB connection, total: 3
2008-04-17 15:26:46.243 Connected to database 'mythconverg' at host: localhost
2008-04-17 15:26:46.463 New DB scheduler connection
2008-04-17 15:26:46.467 Connected to database 'mythconverg' at host: localhost
2008-04-17 15:26:46.518 QMulticastSocket: setsockopt - IP_ADD_MEMBERSHIP Error
2008-04-17 15:26:46.667 QMulticastSocket: setsockopt - IP_ADD_MEMBERSHIP Error
2008-04-17 15:26:47.970 Main::Registering HttpStatus Extension
2008-04-17 15:26:48.026 mythbackend version: 0.20.20070821-1 www.mythtv.org
2008-04-17 15:26:48.134 Enabled verbose msgs:  important general
2008-04-17 15:26:48.019 QMulticastSocket: setsockopt - IP_ADD_MEMBERSHIP Error
2008-04-17 15:26:48.433 AutoExpire: Found 1 recorders w/max rate of 138 MiB/min
2008-04-17 15:26:48.434 AutoExpire: Required Free Space: 3.0 GB w/freq: 10 min
2008-04-17 15:26:49.015 Reschedule requested for id -1.
2008-04-17 15:26:54.132 Scheduled 0 items in 5.1 = 5.07 match + 0.04 place
2008-04-17 15:26:54.135 Seem to be woken up by USER
2008-04-17 15:32:24     firewire ownership released
2008-04-17 15:32:47     firewire ownership acquired
2008-04-17 15:32:47     priming firewire...
2008-04-17 15:32:47     BAD ERROR RETURNED? -- FIXME!!
2008-04-17 15:32:50.488 Using runtime prefix = /usr
2008-04-17 15:32:50.498 New DB connection, total: 1
2008-04-17 15:32:50.507 Connected to database 'mythconverg' at host: localhost
2008-04-17 15:32:50.509 Current Schema Version: 1160
Starting up as the master server.
2008-04-17 15:32:50.524 New DB connection, total: 2
2008-04-17 15:32:50.525 Connected to database 'mythconverg' at host: localhost
2008-04-17 15:32:50.526 EITHelper: localtime offset -4:00:00 
2008-04-17 15:32:50.531 New DB connection, total: 3
2008-04-17 15:32:50.532 Connected to database 'mythconverg' at host: localhost
2008-04-17 15:32:50.616 New DB scheduler connection
2008-04-17 15:32:50.617 Connected to database 'mythconverg' at host: localhost
2008-04-17 15:32:51.934 Main::Registering HttpStatus Extension
2008-04-17 15:32:51.934 mythbackend version: 0.20.20070821-1 www.mythtv.org
2008-04-17 15:32:51.935 Enabled verbose msgs:  important general
2008-04-17 15:32:51.935 AutoExpire: Found 1 recorders w/max rate of 138 MiB/min
2008-04-17 15:32:51.936 AutoExpire: Required Free Space: 3.0 GB w/freq: 10 min
2008-04-17 15:32:52.620 Reschedule requested for id -1.
2008-04-17 15:32:52.934 Scheduled 0 items in 0.3 = 0.30 match + 0.01 place
2008-04-17 15:32:52.936 Seem to be woken up by USER
2008-04-17 15:36:24     firewire ownership acquired
2008-04-17 15:36:24     priming firewire...
2008-04-17 15:36:24     BAD ERROR RETURNED? -- FIXME!!
2008-04-17 15:36:27.924 Using runtime prefix = /usr
2008-04-17 15:36:27.934 New DB connection, total: 1
2008-04-17 15:36:27.943 Connected to database 'mythconverg' at host: localhost
2008-04-17 15:36:27.945 Current Schema Version: 1160
Starting up as the master server.
2008-04-17 15:36:27.961 New DB connection, total: 2
2008-04-17 15:36:27.962 Connected to database 'mythconverg' at host: localhost
2008-04-17 15:36:27.964 EITHelper: localtime offset -4:00:00 
2008-04-17 15:36:27.968 New DB connection, total: 3
2008-04-17 15:36:27.969 Connected to database 'mythconverg' at host: localhost
2008-04-17 15:36:28.053 New DB scheduler connection
2008-04-17 15:36:28.054 Connected to database 'mythconverg' at host: localhost
2008-04-17 15:36:29.370 Main::Registering HttpStatus Extension
2008-04-17 15:36:29.371 mythbackend version: 0.20.20070821-1 www.mythtv.org
2008-04-17 15:36:29.372 Enabled verbose msgs:  important general
2008-04-17 15:36:29.372 AutoExpire: Found 1 recorders w/max rate of 138 MiB/min
2008-04-17 15:36:29.373 AutoExpire: Required Free Space: 3.0 GB w/freq: 10 min
2008-04-17 15:36:30.056 Reschedule requested for id -1.
2008-04-17 15:36:30.370 Scheduled 0 items in 0.3 = 0.30 match + 0.01 place
2008-04-17 15:36:30.372 Seem to be woken up by USER
2008-04-17 15:37:23     firewire ownership acquired
2008-04-17 15:37:23     priming firewire...
2008-04-17 15:37:23     BAD ERROR RETURNED? -- FIXME!!
2008-04-17 15:37:26.401 Using runtime prefix = /usr
2008-04-17 15:37:26.412 New DB connection, total: 1
2008-04-17 15:37:26.421 Connected to database 'mythconverg' at host: localhost
2008-04-17 15:37:26.425 Current Schema Version: 1160
Starting up as the master server.
2008-04-17 15:37:26.442 New DB connection, total: 2
2008-04-17 15:37:26.443 Connected to database 'mythconverg' at host: localhost
2008-04-17 15:37:26.444 EITHelper: localtime offset -4:00:00 
2008-04-17 15:37:26.449 New DB connection, total: 3
2008-04-17 15:37:26.450 Connected to database 'mythconverg' at host: localhost
2008-04-17 15:37:26.536 New DB scheduler connection
2008-04-17 15:37:26.537 Connected to database 'mythconverg' at host: localhost
2008-04-17 15:37:27.860 Main::Registering HttpStatus Extension
2008-04-17 15:37:27.861 mythbackend version: 0.20.20070821-1 www.mythtv.org
2008-04-17 15:37:27.862 Enabled verbose msgs:  important general
2008-04-17 15:37:27.862 AutoExpire: Found 1 recorders w/max rate of 138 MiB/min
2008-04-17 15:37:27.864 AutoExpire: Required Free Space: 3.0 GB w/freq: 10 min
2008-04-17 15:37:28.540 Reschedule requested for id -1.
2008-04-17 15:37:28.859 Scheduled 0 items in 0.3 = 0.31 match + 0.01 place
2008-04-17 15:37:28.861 Seem to be woken up by USER
2008-04-17 16:33:18     firewire ownership released
2008-04-17 23:02:48     firewire ownership acquired
2008-04-17 23:02:48     priming firewire...
2008-04-17 23:02:48     BAD ERROR RETURNED? -- FIXME!!
2008-04-17 23:02:52.173 Using runtime prefix = /usr
2008-04-17 23:02:52.407 New DB connection, total: 1
2008-04-17 23:02:52.411 Connected to database 'mythconverg' at host: localhost
2008-04-17 23:02:52.648 Current Schema Version: 1160
Starting up as the master server.
2008-04-17 23:02:52.733 New DB connection, total: 2
2008-04-17 23:02:52.823 Connected to database 'mythconverg' at host: localhost
2008-04-17 23:02:52.905 EITHelper: localtime offset -4:00:00 
2008-04-17 23:02:53.028 New DB connection, total: 3
2008-04-17 23:02:53.159 Connected to database 'mythconverg' at host: localhost
2008-04-17 23:02:53.401 New DB scheduler connection
2008-04-17 23:02:53.403 Connected to database 'mythconverg' at host: localhost
2008-04-17 23:02:53.524 QMulticastSocket: setsockopt - IP_ADD_MEMBERSHIP Error
2008-04-17 23:02:53.594 QMulticastSocket: setsockopt - IP_ADD_MEMBERSHIP Error
2008-04-17 23:02:54.898 Main::Registering HttpStatus Extension
2008-04-17 23:02:55.031 mythbackend version: 0.20.20070821-1 www.mythtv.org
2008-04-17 23:02:55.107 Enabled verbose msgs:  important general
2008-04-17 23:02:54.924 QMulticastSocket: setsockopt - IP_ADD_MEMBERSHIP Error
2008-04-17 23:02:55.360 AutoExpire: Found 1 recorders w/max rate of 138 MiB/min
2008-04-17 23:02:55.361 AutoExpire: Required Free Space: 3.0 GB w/freq: 10 min
2008-04-17 23:02:55.603 Reschedule requested for id -1.
2008-04-17 23:03:00.925 Scheduled 0 items in 5.3 = 5.28 match + 0.04 place
2008-04-17 23:03:00.928 Seem to be woken up by USER
```

I also tried running the command sudo ./firewire_tester -B -P 0 -n 1 and all the tests fail

If nothing works out I may just completely try starting from scratch again.  Hopefully it doesn't come to that.

I appreciate the help so far

thanks

---

### Post by majoridiot on 2008-04-18
> **Robby23 said:**
> Thanks for the help so far.  For some reason now the command

$ sudo ./firewire_tester -p -P 0 -n 1 -r 5

outputs:

Action: Test P2P connection 5 times, node 1, channel 1
P2P: Testing...Failed
P2P: Testing...Failed
P2P: Testing...Failed
P2P: Testing...Failed
P2P: Testing...Failed...

the FIX ME! error in the backend log indicates to me that you are possibly trying to test/prime/record 
from an encrypted channel... which you can not do.

for starters, go into mythtv-setup, 4 input connections.  then select your firewire tuner.  change the "starting
 channel" to a **known good** channel, such as a local or any other channel you know is not encrypted.

next, go to the firewire guide and download the latest mythprime binary:

[https://help.ubuntu.com/community/MythTV_Firewire#head-6fd45c2d5332aceb72ef680383438997abae7d1e](https://help.ubuntu.com/community/MythTV_Firewire#head-6fd45c2d5332aceb72ef680383438997abae7d1e)

this is a much-improved primer/tester and requires no port or node options.  open a terminal and cd to the
directory containing the new mythprime.  run it in verbose mode with:
```
$ ./mythprime -v
```

it will go looking for your stb and try to prime it.  a final priming summary will tell you the results. it
will make multiple attempts at stabilizing the connection, so do not give up and interrupt it until the final
summary has printed.

if it fails repeatedly, then there is either an issue with tthe channel (change it and try mythrprime again)
or something's run afoul in your firewire setup and more troubleshooting is needed.

in case of failure, paste sample failed output from mythprime here, to help troubleshoot it.

if it tests well, you can use it as your default primer by putting it in /usr/bin:

```
$ sudo cp mythprime /usr/bin
```

and changing the call to it in **/etc/init.d/mythtv-backend**'s prime_firewire() function-
from:
```
  su - $USER -c "myth_prime"
```

to:

```
  su - $USER -c "mythprime"
```

the mythprime binaries are fully-compatible with mythtv .20 if those changes are made.

also, if you have not already, be sure to read the "tips on Priming" and "General Firewire Notes" for
more good troubleshooting info.

---

### Post by Robby23 on 2008-04-18
mythprime -v output

```
Priming errors encountered, trying again...
Acquiring handle on port 0.
1 devices detected.  checking avc subtypes...
ERROR reading oPCR0: Invalid argument
Skipping ghost node 0

Attempting to prime device on port 0 node 1.
Powering device on port 0 node 1...successful.
Establishing P2P connection on node 1, channel 1... P2P: connection established.
P2P: receiving packets... FAILED.
Disconnecting P2P connection on node 1, channel 1
Establishing P2P connection on node 1, channel 1... P2P: connection established.
P2P: receiving packets... FAILED.
Disconnecting P2P connection on node 1, channel 1
Establishing P2P connection on node 1, channel 1... P2P: connection established.
P2P: receiving packets... FAILED.
Disconnecting P2P connection on node 1, channel 1
Establishing P2P connection on node 1, channel 1... P2P: connection established.
P2P: receiving packets... FAILED.
Disconnecting P2P connection on node 1, channel 1
Establishing P2P connection on node 1, channel 1... P2P: connection established.
P2P: receiving packets... FAILED.
Disconnecting P2P connection on node 1, channel 1

successful connections: 0
Establishing P2P connection on node 1, channel 1... P2P: connection established.
P2P: receiving packets... FAILED.
Disconnecting P2P connection on node 1, channel 1
Establishing P2P connection on node 1, channel 1... P2P: connection established.
P2P: receiving packets... FAILED.
Disconnecting P2P connection on node 1, channel 1
Establishing P2P connection on node 1, channel 1... P2P: connection established.
P2P: receiving packets... FAILED.
Disconnecting P2P connection on node 1, channel 1
Establishing P2P connection on node 1, channel 1... P2P: connection established.
P2P: receiving packets... FAILED.
Disconnecting P2P connection on node 1, channel 1
Establishing P2P connection on node 1, channel 1... P2P: connection established.
P2P: receiving packets... FAILED.
Disconnecting P2P connection on node 1, channel 1

successful connections: 0

P2P priming failed... attempting broadcast priming.
Establishing P2P connection on node 1, channel 1... P2P: connection established.
P2P: receiving packets... FAILED.
Disconnecting P2P connection on node 1, channel 1
Establishing P2P connection on node 1, channel 1... P2P: connection established.
P2P: receiving packets... FAILED.
Disconnecting P2P connection on node 1, channel 1
Establishing P2P connection on node 1, channel 1... P2P: connection established.
P2P: receiving packets... FAILED.
Disconnecting P2P connection on node 1, channel 1
Establishing P2P connection on node 1, channel 1... P2P: connection established.
P2P: receiving packets... FAILED.
Disconnecting P2P connection on node 1, channel 1
Establishing P2P connection on node 1, channel 1... P2P: connection established.
P2P: receiving packets... FAILED.
Disconnecting P2P connection on node 1, channel 1
Establishing P2P connection on node 1, channel 1... P2P: connection established.
P2P: receiving packets... FAILED.
Disconnecting P2P connection on node 1, channel 1
Establishing P2P connection on node 1, channel 1... P2P: connection established.
P2P: receiving packets... FAILED.
Disconnecting P2P connection on node 1, channel 1
Establishing P2P connection on node 1, channel 1... P2P: connection established.
P2P: receiving packets... FAILED.
Disconnecting P2P connection on node 1, channel 1
Establishing P2P connection on node 1, channel 1... P2P: connection established.
P2P: receiving packets... FAILED.
Disconnecting P2P connection on node 1, channel 1
Establishing P2P connection on node 1, channel 1... P2P: connection established.
P2P: receiving packets... FAILED.
Disconnecting P2P connection on node 1, channel 1
Establishing P2P connection on node 1, channel 1... P2P: connection established.
P2P: receiving packets... FAILED.
Disconnecting P2P connection on node 1, channel 1
Establishing P2P connection on node 1, channel 1... P2P: connection established.
P2P: receiving packets... FAILED.
Disconnecting P2P connection on node 1, channel 1
Establishing P2P connection on node 1, channel 1... P2P: connection established.
P2P: receiving packets... FAILED.
Disconnecting P2P connection on node 1, channel 1
Establishing P2P connection on node 1, channel 1... P2P: connection established.
P2P: receiving packets... FAILED.
Disconnecting P2P connection on node 1, channel 1
Establishing P2P connection on node 1, channel 1... P2P: connection established.
P2P: receiving packets... FAILED.
Disconnecting P2P connection on node 1, channel 1
Establishing P2P connection on node 1, channel 1... P2P: connection established.
P2P: receiving packets... FAILED.
Disconnecting P2P connection on node 1, channel 1
Establishing P2P connection on node 1, channel 1... P2P: connection established.
P2P: receiving packets... FAILED.
Disconnecting P2P connection on node 1, channel 1
Establishing P2P connection on node 1, channel 1... P2P: connection established.
P2P: receiving packets... FAILED.
Disconnecting P2P connection on node 1, channel 1
Establishing P2P connection on node 1, channel 1... P2P: connection established.
P2P: receiving packets... FAILED.
Disconnecting P2P connection on node 1, channel 1
Establishing P2P connection on node 1, channel 1... P2P: connection established.
P2P: receiving packets... FAILED.
Disconnecting P2P connection on node 1, channel 1
Establishing P2P connection on node 1, channel 1... P2P: connection established.
P2P: receiving packets... FAILED.
Disconnecting P2P connection on node 1, channel 1
Establishing P2P connection on node 1, channel 1... P2P: connection established.
P2P: receiving packets... FAILED.
Disconnecting P2P connection on node 1, channel 1
Establishing P2P connection on node 1, channel 1... P2P: connection established.
P2P: receiving packets... FAILED.
Disconnecting P2P connection on node 1, channel 1
Establishing P2P connection on node 1, channel 1... P2P: connection established.
P2P: receiving packets... FAILED.
Disconnecting P2P connection on node 1, channel 1
Establishing P2P connection on node 1, channel 1... P2P: connection established.
P2P: receiving packets... FAILED.
Disconnecting P2P connection on node 1, channel 1
Establishing P2P connection on node 1, channel 1... P2P: connection established.
P2P: receiving packets... FAILED.
Disconnecting P2P connection on node 1, channel 1
Establishing P2P connection on node 1, channel 1... P2P: connection established.
P2P: receiving packets... FAILED.
Disconnecting P2P connection on node 1, channel 1
Establishing P2P connection on node 1, channel 1... P2P: connection established.
P2P: receiving packets... FAILED.
Disconnecting P2P connection on node 1, channel 1
Establishing P2P connection on node 1, channel 1... P2P: connection established.
P2P: receiving packets... FAILED.
Disconnecting P2P connection on node 1, channel 1
Establishing P2P connection on node 1, channel 1... P2P: connection established.
P2P: receiving packets... FAILED.
Disconnecting P2P connection on node 1, channel 1
Failed to prime stb on port 0 node 1.

Priming errors encountered, trying again...
Priming Errors encountered: 0 stbs primed, 0 stbs failed to prime, 0 non-stbs ignored and 0 ghost nodes skipped on 1 ports in 3 runs.

```

It can't be a problem with my firewire setup because when I log on windows I'm able to record.  It's strange because just yesterday this was working fine :(.

Again thank you for replying so quickly

---

### Post by majoridiot on 2008-04-18
> **Robby23 said:**
> mythprime -v output...

It can't be a problem with my firewire setup because when I log on windows I'm able to record.  It's strange because just yesterday this was working fine :(.

Again thank you for replying so quickly

that log shows a total failure- not a single good connection.  definitely not good.

you say it works fine in windows... does that mean that after failing to prime with mythprime, if you reboot 
into windows having made no changes at all (channel changes, connection switch, etc.), that it will
record the same channel mythprime is failing to stabilize?

also, did you run mythprime with the stb initially powered off?  it would be helpful to know if it actually powers
on or not... to see if any transactions are making it to the stb.

the hacked-together windows drivers and capdvhs, etc. use (or at least used to use) a different method of 
recording from the stb.  however, any channel recordable by windoze should be fine in any OS.

also, apparently the SA stbs like (or need) to occasionally be reset, to bring the house back in order.
you might give this a try and see if it makes any difference.  you can find info on SA stb tips, etc. here:

[http://www.digitalhome.ca/forum/showthread.php?t=17719](http://www.digitalhome.ca/forum/showthread.php?t=17719)

---

### Post by Robby23 on 2008-04-18
> **majoridiot said:**
> that log shows a total failure- not a single good connection.  definitely not good.

you say it works fine in windows... does that mean that after failing to prime with mythprime, if you reboot 
into windows having made no changes at all (channel changes, connection switch, etc.), that it will
record the same channel mythprime is failing to stabilize?

also, did you run mythprime with the stb initially powered off?  it would be helpful to know if it actually powers
on or not... to see if any transactions are making it to the stb.

the hacked-together windows drivers and capdvhs, etc. use (or at least used to use) a different method of 
recording from the stb.  however, any channel recordable by windoze should be fine in any OS.

also, apparently the SA stbs like (or need) to occasionally be reset, to bring the house back in order.
you might give this a try and see if it makes any difference.  you can find info on SA stb tips, etc. here:

[http://www.digitalhome.ca/forum/showthread.php?t=17719](http://www.digitalhome.ca/forum/showthread.php?t=17719)

When I first login to ubuntu the channel on my stb changes to the starting channel that I set mythtv to.  When I load mythprime with the stb off it does infact turn it on, but the rest of everything fails. 

I did follow that guide for SA tips and stuff.  I rebooted it etc but I still get the same results.  At least we know that data is being transfered to my stb because it is changing channels and powering on.

As for your windows question, yeah thats exactly what I did.

```
Checking for available firewire ports:
Acquiring firewire handle... OK.
1 ports found
Bus reset succeeded

Acquiring handle on port 0.
1 devices detected.  checking avc subtypes...
ERROR reading oPCR0: Invalid argument
Skipping ghost node 0

Attempting to prime device on port 0 node 1.
Powering device on port 0 node 1...successful.
Establishing P2P connection on node 1, channel 1... P2P: connection established.
P2P: receiving packets... FAILED.
Disconnecting P2P connection on node 1, channel 1
Establishing P2P connection on node 1, channel 1... P2P: connection established.
P2P: receiving packets... FAILED.

and so on
```

If it helps any which I doubt it would but I was recording a program and on the box it paused because it was the end of the recording and mythtv froze up for about 5 mins then went back to the main frontend menu.  After that I was unable to get it working again.

---

### Post by majoridiot on 2008-04-18
> **Robby23 said:**
> When I first login to ubuntu the channel on my stb changes to the starting channel that I set mythtv to.  When I load mythprime with the stb off it does infact turn it on, but the rest of everything fails. 

I did follow that guide for SA tips and stuff.  I rebooted it etc but I still get the same results.  At least we know that data is being transfered to my stb because it is changing channels and powering on.

As for your windows question, yeah thats exactly what I did.

```
Checking for available firewire ports:
Acquiring firewire handle... OK.
1 ports found
Bus reset succeeded

Acquiring handle on port 0.
1 devices detected.  checking avc subtypes...
ERROR reading oPCR0: Invalid argument
Skipping ghost node 0

Attempting to prime device on port 0 node 1.
Powering device on port 0 node 1...successful.
Establishing P2P connection on node 1, channel 1... P2P: connection established.
P2P: receiving packets... FAILED.
Disconnecting P2P connection on node 1, channel 1
Establishing P2P connection on node 1, channel 1... P2P: connection established.
P2P: receiving packets... FAILED.

and so on
```

If it helps any which I doubt it would but I was recording a program and on the box it paused because it was the end of the recording and mythtv froze up for about 5 mins then went back to the main frontend menu.  After that I was unable to get it working again.

hm.  this is really odd.

for the sake of covering all variables, try this:

edit /etc/init.d/mythtv-backend and put:

```
exit 0
```

immediately after the comment block at the beginning, to keep the backend server from launching on reboot.

then, power down your mythbox and switch the firewire cable to the other port on the stb.  change the stb 
to a known-unecrypted channel and boot the backend.

when it's back up and running, try running mythprime again and see if the results are any different. if not, power
down the mythbox again, switch back to the other port on the stb, power it up and try mythprime again.

if it's still a no-go, then go back and remove the exit 0 command, so that the backend server will restart.

then, cold-boot the stb.  unplug the power and let it sit for a couple of minutes... then plug it back in and
let it boot.  do this with the mythbox powered down.  give it 20-30 minutes to reload from the network, 
(from my understanding, the SA boxes are slow booting) then boot up the mythbox and try again.

---

### Post by Robby23 on 2008-04-19
> **majoridiot said:**
> hm.  this is really odd.

for the sake of covering all variables, try this:

edit /etc/init.d/mythtv-backend and put:

```
exit 0
```

immediately after the comment block at the beginning, to keep the backend server from launching on reboot.

then, power down your mythbox and switch the firewire cable to the other port on the stb.  change the stb 
to a known-unecrypted channel and boot the backend.

when it's back up and running, try running mythprime again and see if the results are any different. if not, power
down the mythbox again, switch back to the other port on the stb, power it up and try mythprime again.

if it's still a no-go, then go back and remove the exit 0 command, so that the backend server will restart.

then, cold-boot the stb.  unplug the power and let it sit for a couple of minutes... then plug it back in and
let it boot.  do this with the mythbox powered down.  give it 20-30 minutes to reload from the network, 
(from my understanding, the SA boxes are slow booting) then boot up the mythbox and try again.

Dang this is frustrating still no luck.  Would it be a good idea to just do a clean reinstall or something?  I can't figure out why I can't recieve any data from the stb but the stb powers on when mythprime is loaded.  Could it be a problem with firewire on ubuntu or something?  It was working fine a few days ago so this is really strange

---

### Post by majoridiot on 2008-04-19
> **Robby23 said:**
> Dang this is frustrating still no luck.  Would it be a good idea to just do a clean reinstall or something?  I can't figure out why I can't recieve any data from the stb but the stb powers on when mythprime is loaded.  Could it be a problem with firewire on ubuntu or something?  It was working fine a few days ago so this is really strange

you can try checking for the latest updates and applying them, to see if it helps, but i doubt it will.

what you are describing makes no sense.  if you can record a channel in windoze, there is no reason the same channel
would not prime/record with mythtv.

you're *SURE* the windoze side is still working?  it sounds to me like something went wonky with the stb... either connection
or encryption-wise.

---

### Post by kandarp728 on 2008-04-20
It seems that the problem develops when your watching the channels/programs with the CC01 flags which dont stream out via the firewire port of the STB.  My experience has been that watching one of those channels for more than 5 minutes results in the firewire connection being severed/out of sync.  The only fix I have seen is unplugging firewire on both sides, hard powering down all devices, replugging in everything, running the firewire tester, doing a test recording with test-mpeg2 and then restarting mythtv-backend.  It seems a very low level issue either with linux firewire and/or the STB firewire firmware. 

This is just happened to me now, and it seems every week or so I have to do the above process, I dont mind, but providing stability in firewire would be a great improvement.  I just tried using mythprime with the STB off and it powers up the STB but never gets a good connection.

---

### Post by dsbw on 2008-04-20
Boy, this sure looks familiar. 

I've had the exact same issue: Here today, gone tomorrow. 

If I can get some predictability on what causes it to fail, that'd be great. 

It seems that the problem develops when your watching the channels/programs with the CC01 flags which dont stream out via the firewire port of the STB.

Do you mean that anytime you watch a CC01 channel/program, or only when you try to watch the channel/program using the firewire?:confused: 'cause if it's the former, the firewire is essentially worse than useless.

---

### Post by kandarp728 on 2008-04-21
Sorry, I should have clarified, I dont use Myth to watch live TV, just my recordings, so I guess its when I watch using the STB and TV only channels with the CC01 flag.  This is has been the one consistent factor in the firewire crapping out.  At this point, its equally possible that Linux and or the STB firewire firmware are at fault.  If its the latter, I wont hold my breath that the cable companies will do anything about it.

---

### Post by majoridiot on 2008-04-21
> **kandarp728 said:**
> Sorry, I should have clarified, I dont use Myth to watch live TV, just my recordings, so I guess its when I watch using the STB and TV only channels with the CC01 flag.  This is has been the one consistent factor in the firewire crapping out.  At this point, its equally possible that Linux and or the STB firewire firmware are at fault.  If its the latter, I wont hold my breath that the cable companies will do anything about it.

you can not record or stream any channel with a CCI flag of 0x01, 0x02 or 0x03, as they are encrypted.  this is true
for **all** operating systems and applications.  some windoze apps will record the stream, but it is unwatchable.

you can only watch, record and *prime* with channels that are CCI 0x00, or "record freely".  unfortunately, it 
seems some SA boxes suffer encrypted channels more than others and become unstable from priming or trying to
recorded them.

right now, the best way to ensure a stable connection is to identify all of the encrypted channels and disable them 
in your SD profile, so myth can not tune them.  further reliability can be gained from adding a channel change command
to the backend init script, to make sure the stb  is on a good channel before priming.

i am working to make firewire more friendly out-of-the-box.  this includes the new mythprime primer and a channel
scanner for firewire, that will automatically identify encrypted channels and remove them from the mythtv lineup.

however, in the process of working on the scanner, i think i have found potential bugs in some of the firewire APIs
that are causing some of these issues... so the problem could be at system-level and not with mythtv.  it will take
some time to hopefully debug and identify the problems, so please bear with us... it is being actively addressed
by the mythbuntu team.

---

### Post by dsbw on 2008-04-21
*right now, the best way to ensure a stable connection is to identify all of the encrypted channels and disable themin your SD profile, so myth can not tune them. further reliability can be gained from adding a channel change commandto the backend init script, to make sure the stb is on a good channel before priming.*

I'm blanking on what "SD profile" means. Also, we are talking just about streaming through firewire, right? I've been able to get everything through the analog hole. What I'm concerned with is whether using those other channels breaks the firewire connection. It can't in most folks' cases, right? Otherwise the channel changing would essentially be a joke?

---

### Post by majoridiot on 2008-04-21
> **dsbw said:**
> I'm blanking on what "SD profile" means. Also, we are talking just about streaming through firewire, right? I've been able to get everything through the analog hole. What I'm concerned with is whether using those other channels breaks the firewire connection. It can't in most folks' cases, right? Otherwise the channel changing would essentially be a joke?

by SD profile, i meant schedulesdirect... e.g. your channel line-up.

and yes, i am talking about streaming via firewire only.

channel changing on a firewire connection that has encrypted channels in the line-up will break firewire every time you try
to tune an encrypted channel.  this is why i recommended identifying the bad channels and removing them from the channel
list... so you are guaranteed not to break it just by changing channels.

most people who have issues with this set up two schedules direct line-ups... one for firewire only and the other with
a full list of desired channels.  you can then set up rules for tuner preference, etc. for recording and switch between
tuners as needed when watching livetv.

yes, it is a pain... but the real culprits are the cable companies who are violating FCC regs by encrypting channels they
have no right to.

---

### Post by kandarp728 on 2008-04-21
Does anyone have any idea, how firewire has changed on the system level in the upcoming Hardy Heron release?

---

### Post by dsbw on 2008-04-21
OK, so, wait, we have to have two systems for changing the channels? Via the firewall and via the IR blaster?

Is changing via the firewire, for the 10-15 (and shrinking) channels that it's allowed, worth trouble? Why not just use the IR blaster for everything, and feed from the firewire only when on a non-CC1+ channel?

What am I missing? I guess some people get more channels through the FW? :frown:

---

### Post by majoridiot on 2008-04-22
> **dsbw said:**
> OK, so, wait, we have to have two systems for changing the channels? Via the firewall and via the IR blaster?

Is changing via the firewire, for the 10-15 (and shrinking) channels that it's allowed, worth trouble? Why not just use the IR blaster for everything, and feed from the firewire only when on a non-CC1+ channel?

What am I missing? I guess some people get more channels through the FW? :frown:

i think you misunderstood.

for changing channels *only*- i.e. to use a capture card to get the analog output from the box, you
can use *either* an ir blaster *or* a firewire connection to do the channel change.

if you are using firewire anyway- to capture whatever channels are still clear on your cable system-
then you could use a firewire channel-changer for your analog capture, instead of a blaster.

it was just a *choice* i was pointing out to you... since it would be one less wire, you wouldn't
need to worry about the ir blaster, etc.  if you already have the blaster working and are satisfied,
there is no reason you have to change it.

---

### Post by Robby23 on 2008-04-23
Alright well this is strange.  I reinstalled ubuntu from scratch and I tried it again and now its working.  When I went to intall codecs to play wmv files it stopped working.  Strange?  I uninstalled them and now it works again lol

Right now though I'm getting an error on the frontend when I try to watch live tv.  If I can't figure out my problem I'll post the error.

Output of mythprime:

```
mythprime .55b beta

Checking for available firewire ports:
Acquiring firewire handle... OK.
1 ports found
Bus reset succeeded

Acquiring handle on port 0.
1 devices detected.  checking avc subtypes...
ERROR reading oPCR0: Invalid argument
Skipping ghost node 0

Attempting to prime device on port 0 node 1.
Powering device on port 0 node 1...successful.
Establishing P2P connection on node 1, channel 1... P2P: connection established.
P2P: receiving packets... 60 packets received
Disconnecting P2P connection on node 1, channel 1
Establishing P2P connection on node 1, channel 1... P2P: connection established.
P2P: receiving packets... 57 packets received
Disconnecting P2P connection on node 1, channel 1
Establishing P2P connection on node 1, channel 1... P2P: connection established.
P2P: receiving packets... 102 packets received
Disconnecting P2P connection on node 1, channel 1
Establishing P2P connection on node 1, channel 1... P2P: connection established.
P2P: receiving packets... 100 packets received
Disconnecting P2P connection on node 1, channel 1
Establishing P2P connection on node 1, channel 1... P2P: connection established.
P2P: receiving packets... 107 packets received
Disconnecting P2P connection on node 1, channel 1

successful connections: 5
Successfully primed stb on port 0 node 1.

1 stbs primed, 0 non-stbs ignored and 1 ghost nodes skipped on 1 ports.

```

---

### Post by majoridiot on 2008-04-23
> **Robby23 said:**
> Alright well this is strange.  I reinstalled ubuntu from scratch and I tried it again and now its working.  When I went to intall codecs to play wmv files it stopped working.  Strange?  I uninstalled them and now it works again lol

ok... that is *beyond* strange.

have you tried this more than once to verify it is reproducible?

i will test this on my 8.04 devbox when i get home and see what happens. i'm fairly sure 
that i do not have restricted codecs installed on it.

**EDIT:** ok... i installed all of the restricted codecs and there was no change in 
mythprime's behavior for me- it primed the stb.  this also holds true for my main
production backend, which is still running 7.10.

if this bug is reproducible for you, then a bugreport should be filed so the problem can 
be tracked down.  if this is the case, please post a link to the bugreport here with all
of your system specs, mytbuntu (or ubuntu) version, etc.

two things i noticed- you are 2 versions behind on mythprime, so be sure to get the latest 
version from the firewire guide page.  also, in your original post you said you have the 
firewire configured in mythv @ 400Mbps.  it shoud be 200.

---

### Post by Robby23 on 2008-04-23
According to this I'm using the current mythprime version.

[https://help.ubuntu.com/community/MythTV_Firewire](https://help.ubuntu.com/community/MythTV_Firewire)

I haven't done anything new but restart my computer and mythprime now outputs:

```
Checking for available firewire ports:
Acquiring firewire handle... FAILED!
```

./firewire_tester -p -P 0 -n 1 -r 5 outputs:

```
Action: Test P2P connection 5 times, node 1, channel 1
P2P: Testing...Success, 186 packets received
P2P: Testing...Success, 34 packets received
P2P: Testing...Success, 118 packets received
P2P: Testing...Success, 34 packets received
P2P: Testing...Success, 101 packets received

```

When I try and watch live tv I get the error:

"MythTv is already using all available inputs for the channel you selected.  If you watch an in-progress recording, select one from the playback menu.  If you want to watch live TV cancel one of the in-progress recordings from the delete menu."

Nothing is recording right now, so I'm not sure why I'm getting this error.

/var/log/mythtv/mythbackend.log contains the following:

```
2008-04-23 17:42:11.606 Using runtime prefix = /usr
2008-04-23 17:42:11.627 New DB connection, total: 1
2008-04-23 17:42:11.633 Connected to database 'mythconverg' at host: localhost
2008-04-23 17:42:11.636 Current Schema Version: 1160
Starting up as the master server.
2008-04-23 17:42:11.646 New DB connection, total: 2
2008-04-23 17:42:11.647 Connected to database 'mythconverg' at host: localhost
2008-04-23 17:42:11.650 EITHelper: localtime offset -4:00:00 
2008-04-23 17:42:11.654 New DB connection, total: 3
2008-04-23 17:42:11.655 Connected to database 'mythconverg' at host: localhost
2008-04-23 17:42:11.736 FireChan, Error: Model: 'Other' is not supported by internal channel changer.
ERROR: no valid capture cards are defined in the database.
Perhaps you should read the installation instructions?
2008-04-23 17:42:12.962 Main::Registering HttpStatus Extension
2008-04-23 17:42:12.963 mythbackend version: 0.20.20070821-1 www.mythtv.org
2008-04-23 17:42:12.964 Enabled verbose msgs:  important general
2008-04-23 17:42:12.966 AutoExpire: Found 0 recorders w/max rate of 0 MiB/min
2008-04-23 17:42:12.967 AutoExpire: Required Free Space: 1.0 GB w/freq: 10 min
2008-04-23 17:49:17.875 MainServer::HandleAnnounce Monitor

```

"ERROR: no valid capture cards are defined in the database." stuck out to me.  I did setup everything as I have done before in the backend.  I also changed 400Mbps to 200 as you suggested.

I reinstalled the restricted codecs and now 
```
./firewire_tester -p -P 0 -n 1 -r 5
```
outputs:

```
Action: Test P2P connection 5 times, node 1, channel 1
P2P: Testing...Failed
P2P: Testing...Failed
P2P: Testing...Failed
P2P: Testing...Failed
P2P: Testing...Failed
```

After removing the restricted codecs firwire_tester outputs the same as before with failed everything.

---

### Post by majoridiot on 2008-04-24
> **Robby23 said:**
> According to this I'm using the current mythprime version.

sorry... my mistake.  that is the latest public version.

what stuck out in your logs is this:

```
2008-04-23 17:42:11.736 FireChan, Error: Model: 'Other' is not supported by internal channel changer.
ERROR: no valid capture cards are defined in the database.
```

configuring your 8300 is obviously causing problems with myth- as it is not supported for channel changing.
you should try setting it up as another SA model, or do some research to see how others have theirs
configured.  it is possible that "other" is the proper configuration and you need a different
channel changer.

in any event, i recommend completely deleting the firewire tuner and setting up a new one- since the 
current config is not properly defined in the database.  if you try more than one stb setting, etc.,
i recommend deleting the tuner each time and setting up a new one, just to be sure.

of course, be sure to do steps 3 and 4 after each delete/config to bind the tuner to your lineup,
load the channels and fill the database.

---

### Post by Robby23 on 2008-04-25
I've tried installing Mythbuntu 8.04 and I'm able to configure the stb properly.  I'm back to where I was earlier where mythprime would power on the drive and mythbuntu changes the channel to my starting channel. 

The thing that bugs me is the channels could be changed, the stb could be powered on and even the backend detects the firewire device as seen in this pic.

[http://i30.tinypic.com/212cwhs.png](http://i30.tinypic.com/212cwhs.png)

I do however get a new error when restarting the backend.

```
 * Priming Firewire                                                             1 devices detected.  checking avc subtypes...

Priming errors encountered, trying again...
1 devices detected.  checking avc subtypes...

Priming errors encountered, trying again...
1 devices detected.  checking avc subtypes...

Priming errors encountered, trying again...
Priming Errors encountered: 0 stbs primed, 0 stbs failed to prime, 0 non-stbs ignored and 0 ghost nodes skipped on 1 ports in 3 runs.
                                                                         [fail]
 * Starting MythTV server: mythbackend                                   [ OK ] 


```


What do you guys suggest I do from here?

---

### Post by majoridiot on 2008-04-26
> **Robby23 said:**
> I've tried installing Mythbuntu 8.04 and I'm able to configure the stb properly.  I'm back to where I was earlier where mythprime would power on the drive and mythbuntu changes the channel to my starting channel. 

The thing that bugs me is the channels could be changed, the stb could be powered on and even the backend detects the firewire device as seen in this pic.

[http://i30.tinypic.com/212cwhs.png](http://i30.tinypic.com/212cwhs.png)

I do however get a new error when restarting the backend.

```
 * Priming Firewire                                                             1 devices detected.  checking avc subtypes...

Priming errors encountered, trying again...
1 devices detected.  checking avc subtypes...

Priming errors encountered, trying again...
1 devices detected.  checking avc subtypes...

Priming errors encountered, trying again...
Priming Errors encountered: 0 stbs primed, 0 stbs failed to prime, 0 non-stbs ignored and 0 ghost nodes skipped on 1 ports in 3 runs.
                                                                         [fail]
 * Starting MythTV server: mythbackend                                   [ OK ] 


```


What do you guys suggest I do from here?

well, you have gotten over the major hurdles, if mythtv will 
change channel on your 8300...

the error being returned *appears* to be because you are attempting 
to prime an encrypted channel.  this may or may not be the case- it is 
impossible to tell from the short log.

at this stage, i suggest finding an unencrypted channel and get 
mythprime to prime it manually from a terminal before going any further 
with this.  once you have a good, known-prime-able channel, make that
channel the *starting* channel for the **input connection** for the firewire tuner 
in backend setup. 

this way, you do not get caught in a loop of the backend automatically
tuning to a bad channel on restart, which will cause both mythprime 
and mythtv to fail.

the easiest way to find an unencrypted channel is to start with the 
SD *analog* channels, as the digital and HD ones are most likely to
be encrypted. you can tune the stb by hand and then run mythprime 
from a terminal in verbose mode (-v option).  the output will show 
you what is going on.  

if you are trying to prime an encrypted channel, somewhere in the 
verbose log you should see one or more warnings that  the "synch byte" 
could not be found and a mention of a possibly encrypted channel.

i will be in the mythbuntu irc channel most of today, so feel free to 
ping me in there if you are still having difficulties and we can discuss 
your progress and troubleshoot.

otherwise, if you are still having problems, please post the *entire* verbose 
output from a typical run and we'll see what's there.

---

### Post by majoridiot on 2008-05-01
following up...

Robby23 caught up with me in the mythbuntu irc channel last night and the problem was resolved via remote troubleshooting.

there were two main issues causing problems with his ubuntu 7.10/mythtv .20 installation:

1. the restart section of his /etc/init.d/mythtv-backend was missing the call to the *own_firewire* function, so the
permissions for /dev/raw1394 were not being set correctly once he ran mythtv-setup and the backend server restarted.

2. his SA8300 stb was incorrectly configured as "other" in tuner setup.  testing revealed that it functions properly and
changes channels when configured as an SA4250.

Robby23 also noted that he went back to ubuntu 7.10 after mythbuntu 8.04 borked his setup.  this *may* have something
to do with his frontend/backend running on a laptop... or not.

---

### Post by kandarp728 on 2008-05-11
Well I think I managed to figure out how to keep firewire stable while still being able to watch CC01 flaged channels.  This is what worked for me on my SA4250.  Prior to watching CC01 channel, I removed the firewire modules (raw1394, ohci1394,iee1394,sbp2,dv1394), stopped mythtv-backend, then after I was done watching the show on onthe CC01 flagged channel, I tuned to a known good channel and readded the modules, ran the firewire_tester, captures a sample with test-mpeg2 and restarted mythtb-backend, and it worked like a charm.  Now to just write a script to do this automatically, it would be something that would try a test-mpeg2 and if it was a zero size file, it would remove the modules, stop mythtv-backend, then sleep for a set period of time and repeat until you get a valid file size then readd the modules, run the firewire_tester, test_mpeg2 and start mythtvbackend....stay tuned

---

### Post by majoridiot on 2008-05-11
> **kandarp728 said:**
> Well I think I managed to figure out how to keep firewire stable while still being able to watch CC01 flaged channels.  This is what worked for me on my SA4250.  Prior to watching CC01 channel, I removed the firewire modules (raw1394, ohci1394,iee1394,sbp2,dv1394), stopped mythtv-backend, then after I was done watching the show on onthe CC01 flagged channel, I tuned to a known good channel and readded the modules, ran the firewire_tester, captures a sample with test-mpeg2 and restarted mythtb-backend, and it worked like a charm.  Now to just write a script to do this automatically, it would be something that would try a test-mpeg2 and if it was a zero size file, it would remove the modules, stop mythtv-backend, then sleep for a set period of time and repeat until you get a valid file size then readd the modules, run the firewire_tester, test_mpeg2 and start mythtvbackend....stay tuned

you should **not** need to remove/reload the firewire modules.  simply stopping the backend before you tune the stb to an 
encrypted channel you want to watch should be sufficient.  although i have not reviewed the code in-depth, from experience it
seems that the .21 backend does a fair amount of monitoring. etc. of firewire tuners, even when the tuner is not in use
by mythtv.  once the backend is stopped, there is nothing system-wise that would cause firewire to become unstable while watching
and encrypted channel on the stb- because nothing is using it.

an alternate method that may work for you (without stopping the backend) would simply be to take the permissions away from
mythtv, so it can't interact with the firewire when you do not want it to.  it may be worth playing with, as a simpler fix.
try removing all read/write persmissions:

```
$ sudo chmod a-rw /dev/raw1394
```

you'll probably find complaints in the backend log, but i'm guessing they will go away as soon as it can read/write to firewire
again.

to restore:

```
 sudo chmod a+rw /dev/raw1394
```

unfortunately, mythtv considers the firewire stb to be totally its own, which imo is not a sane situation to force upon the
user... there should be a config option to allow/stop stb access when the tuner itself is not in use, to allow casual viewing
without wrecking the stability of firewire.  this setting may exist somewhere- you might post to the mythtv-users mailing
list to ask.

in the meantime, a scanner to help identify encrypted channels is in development.  a motorola-only version is working very
well and is about to go into wider testing.  a SA version will be coming soon... dependent entirely upon SA owners being willing
to help test.

---

### Post by kandarp728 on 2008-05-11
> **majoridiot said:**
> you should **not** need to remove/reload the firewire modules.  simply stopping the backend before you tune the stb to an 
encrypted channel you want to watch should be sufficient.  although i have not reviewed the code in-depth, from experience it
seems that the .21 backend does a fair amount of monitoring. etc. of firewire tuners, even when the tuner is not in use
by mythtv.  once the backend is stopped, there is nothing system-wise that would cause firewire to become unstable while watching
and encrypted channel on the stb- because nothing is using it.

an alternate method that may work for you (without stopping the backend) would simply be to take the permissions away from
mythtv, so it can't interact with the firewire when you do not want it to.  it may be worth playing with, as a simpler fix.
try removing all read/write persmissions:

```
$ sudo chmod a-rw /dev/raw1394
```

you'll probably find complaints in the backend log, but i'm guessing they will go away as soon as it can read/write to firewire
again.

to restore:

```
 sudo chmod a+rw /dev/raw1394
```

unfortunately, mythtv considers the firewire stb to be totally its own, which imo is not a sane situation to force upon the
user... there should be a config option to allow/stop stb access when the tuner itself is not in use, to allow casual viewing
without wrecking the stability of firewire.  this setting may exist somewhere- you might post to the mythtv-users mailing
list to ask.

in the meantime, a scanner to help identify encrypted channels is in development.  a motorola-only version is working very
well and is about to go into wider testing.  a SA version will be coming soon... dependent entirely upon SA owners being willing
to help test.

Thanks for the insights, I think the permissions fix is probably a better fix, can we use the channel changer script to get the current channel from the STB and then determine whether the channel is encrypted based on a list and then change the permissions accordingly?

---

### Post by majoridiot on 2008-05-11
> **kandarp728 said:**
> Thanks for the insights, I think the permissions fix is probably a better fix, can we use the channel changer script to get the current channel from the STB and then determine whether the channel is encrypted based on a list and then change the permissions accordingly?

unfortunately, there is no way to get an stb to report the channel it is tuned to.  until a "fix" is incorporated into mythtv, 
it will be a manual operation only and as-needed.

i just took a quick look around the some of the firewire code and it looks like my suspicions are confirmed.  it appears the backend 
periodically checks the status of the tuner and attempts to correct any issues.  a great idea for a mythtv-dedicated stb, but not
so hot when you use it for non-mythtv viewing as well.

---

### Post by majoridiot on 2008-05-22
a final follow-up concerning the SA8300:

at this time, it appears that the 8300 is useless for use with mythtv.  this is due 
entirely to the stb and not to mythtv or the linux firewire libraries.

when watching live tv, the 8300 outputs a malformed mpeg stream.  the only time it appears 
to output a valid stream is when playing back pre-recorded material from the DVR on 
channel 1000.

researching this has shown that this is a widely-reported complaint.  claims are 
that SA has firmware fixes, but the cable MSOs are not applying them.  

if you are having these problems with your 8300, you are well within your rights to 
complain to your cable company and demand a firewire-enabled stb or firmware update.  
By law, if firewire ports exist, they must be enabled.  whether they abide by their 
obligation is another matter entirely.

---

### Post by notadog on 2008-06-11
> **majoridiot said:**
> following up...

Robby23 caught up with me in the mythbuntu irc channel last night and the problem was resolved via remote troubleshooting.

there were two main issues causing problems with his ubuntu 7.10/mythtv .20 installation:

1. the restart section of his /etc/init.d/mythtv-backend was missing the call to the *own_firewire* function, so the
permissions for /dev/raw1394 were not being set correctly once he ran mythtv-setup and the backend server restarted.



Hi,  I'm having a similar problem in that mythprime fails entirely (running Mythtv .21 and V55 of mythprime.  The STB is a Motorola 6200).  

I looked at /etc/init.d/mythtv-backen and could not locate a call to own_firewire in it.  What are the permissions supposed to be?  On my box they are currently:
crw-rw---- 1 root mythtv 171, 0 2008-06-10 21:40 /dev/raw1394

Thanks.

---

### Post by majoridiot on 2008-06-11
> **notadog said:**
> Hi,  I'm having a similar problem in that mythprime fails entirely (running Mythtv .21 and V55 of mythprime.  The STB is a Motorola 6200).  

I looked at /etc/init.d/mythtv-backen and could not locate a call to own_firewire in it.  What are the permissions supposed to be?  On my box they are currently:
crw-rw---- 1 root mythtv 171, 0 2008-06-10 21:40 /dev/raw1394

Thanks.

those permissions are correct... any member of the mythtv group has read and write access.  make
sure that the user you are running mythtv with is a member of the mythtv group.

have you tried running mythprime manually to see what is happening?  stop the backend server for best results:

```
$ sudo /etc/init.d/mythtv-backend stop
$ mythprime -v
```

the -v is verbose output, which will show you everything mytprime is doing, to help troubleshoot.

a better and more robust version of mythprime should hopefully be released this weekend along with a
beta of scanfw.

---

### Post by notadog on 2008-06-11
> **majoridiot said:**
> those permissions are correct... any member of the mythtv group has read and write access.  make
sure that the user you are running mythtv with is a member of the mythtv group.

have you tried running mythprime manually to see what is happening?  stop the backend server for best results:

```
$ sudo /etc/init.d/mythtv-backend stop
$ mythprime -v
```

the -v is verbose output, which will show you everything mytprime is doing, to help troubleshoot.

a better and more robust version of mythprime should hopefully be released this weekend along with a
beta of scanfw.


Running mythprime manually gives a ton of error messages that start with:

greg@arbormyth:~$ mythprime -v
mythprime .55b beta

Checking for available firewire ports:
Acquiring firewire handle... OK.
1 ports found
Bus reset succeeded

Acquiring handle on port 0.
2 devices detected.  checking avc subtypes...
ERROR reading oPCR0: Invalid argument
Skipping ghost node 0
ERROR reading oPCR0: Resource temporarily unavailable
Skipping ghost node 1

Attempting to prime device on port 0 node 2.
Powering device on port 0 node 2...successful.
Establishing P2P connection on node 2, channel 2... P2P: connection established.
P2P: receiving packets... FAILED.

the establishing connection error is then repeated many times.  All p2p connections fail.  Then on to broadcast which also fails, but has a strange error message:

.........
successful connections: 0

P2P priming failed... attempting broadcast priming.
Establishing P2P connection on node 2, channel 2... P2P: connection established.
P2P: receiving packets... FAILED.
Disconnecting P2P connection on node 2, channel 2
Establishing P2P connection on node 2, channel 2... P2P: connection established.

It says it is trying broadcast but the error says p2p connection failed.  Wrong error message?

BTW, I've occasionally gotten the stb output to run via firewire to mplayer, and I know channel changes/power on work.

Thanks for the reply.  I appreciate the assistance.

---

### Post by majoridiot on 2008-06-11
> **notadog said:**
> Running mythprime manually gives a ton of error messages that start with...

It says it is trying broadcast but the error says p2p connection failed.  Wrong error message?

BTW, I've occasionally gotten the stb output to run via firewire to mplayer, and I know channel changes/power on work.

Thanks for the reply.  I appreciate the assistance.

before it establishes a broadcast conenction (or tries), it first tries to get a p2p connection. if
it receives packets, then it tries broadcast.  this is the most reliable (AFAIK) way to stabilize
an unstable broadcast connection.

a total failure like this is not good.  have you tried priming on different channels or just the same one?
i suggest trying priming a variety of local, non-HD channels to see if the results are any different.

i'm also curious why you are showing 3 nodes.  typically, you will have 2- the one the stb is on and
an empty system node.  having an extra one like you do is odd.

---

### Post by notadog on 2008-06-11
> **majoridiot said:**
> ..

a total failure like this is not good.  have you tried priming on different channels or just the same one?
i suggest trying priming a variety of local, non-HD channels to see if the results are any different.

i'm also curious why you are showing 3 nodes.  typically, you will have 2- the one the stb is on and
an empty system node.  having an extra one like you do is odd.

I don't know why three nodes, but ever since I started with fw connections it has shown 3.  Here's what plugreport shows:

greg@arbormyth:/var/log/mythtv$ plugreport
Host Adapter 0
==============

Node 0 GUID 0x000f9ffffe0c8799
------------------------------
oMPR n_plugs=1, data_rate=2, bcast_channel=63
oPCR[0] online=1, bcast_connection=0, n_p2p_connections=0
        channel=63, data_rate=2, overhead_id=0, payload=376
iMPR n_plugs=0, data_rate=2

Node 1 GUID 0x99870cfefe0c8799
------------------------------
libiec61883 error: error reading oMPR
libiec61883 error: error reading iMPR

Node 2 GUID 0x00f1993100001d7d
------------------------------
libiec61883 error: error reading oMPR
libiec61883 error: error reading iMPR

The "live" node, 0 above, sometimes jumps between 0 and 2 on reboots.  I've never noticed it at 1.

Since my last post, I disabled mythprime in the backend init script, deleted all cards via setup, there is a pcHDTV tuner card in the box, redefined the fw stb and connected it to the SD source.  Now channels are tuned and viewable!  

I have not yet redefined the pcHDTV card so the fw/stb is the only active device. 

There seem to some oddities remaining, but I haven't pinned them down yet.

Does the plugreport clarify the mystery of 3?  

Thanks for the help.

---

### Post by majoridiot on 2008-06-11
> **notadog said:**
> I don't know why three nodes, but ever since I started with fw connections it has shown 3.  Here's what plugreport shows:

greg@arbormyth:/var/log/mythtv$ plugreport
Host Adapter 0
==============

Node 0 GUID 0x000f9ffffe0c8799
------------------------------
oMPR n_plugs=1, data_rate=2, bcast_channel=63
oPCR[0] online=1, bcast_connection=0, n_p2p_connections=0
        channel=63, data_rate=2, overhead_id=0, payload=376
iMPR n_plugs=0, data_rate=2

Node 1 GUID 0x99870cfefe0c8799
------------------------------
libiec61883 error: error reading oMPR
libiec61883 error: error reading iMPR

Node 2 GUID 0x00f1993100001d7d
------------------------------
libiec61883 error: error reading oMPR
libiec61883 error: error reading iMPR

The "live" node, 0 above, sometimes jumps between 0 and 2 on reboots.  I've never noticed it at 1.

Since my last post, I disabled mythprime in the backend init script, deleted all cards via setup, there is a pcHDTV tuner card in the box, redefined the fw stb and connected it to the SD source.  Now channels are tuned and viewable!  

I have not yet redefined the pcHDTV card so the fw/stb is the only active device. 

There seem to some oddities remaining, but I haven't pinned them down yet.

Does the plugreport clarify the mystery of 3?  

Thanks for the help.

glad you got the tuner fixed.  the extra node is a heavy mystery, but most likely a harmless oddity.

some motorola stbs are noted for jumping nodes.  in fact, there is another user with a similar
problem on the mythtv-users mailing list.  the new beta mythprime will have an option to reset
the bus first, which should force a node jump if it is going to happen.  until then, if you
PM me, i will send you a motorola-only primer that will reset the bus and then prime... to see
if this fixes your node jumps. on reboot, etc.

---

