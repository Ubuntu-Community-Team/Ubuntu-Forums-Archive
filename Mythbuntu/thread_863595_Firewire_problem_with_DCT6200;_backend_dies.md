---
title: "Firewire problem with DCT6200; backend dies"
date: 2008-07-18
forum: Mythbuntu
---

### Post by notadog on 2008-07-18
I'm running mythbuntu 7.10 using a firewire feed from Comcast via a DCT 6200, and having intermittent problems that cause the backend to terminate w/o any specific message.  At the end of this note is a sample of typical backend log entries leading up to such a failure.

Basically, the backend has periods of messages saying "Warning: no input...".  Bunches of such messages about every minute for, in this case, about 13 minutes before the backend dies.  The period of warning just prior to the backend dying lasts longer, almost 10 seconds.  Some sort of time out or time limit hit?

After a subsequent restart the recording runs to completeion while logging many similar message sequences.  I suppose it could be flaky output from the STB, but that seems unlikely since the STB otherwise seems to work fine.

I'd appreciate any advice on the cause or even better the cure for this problem.

Thanks.  Hal

Example from mythbackend.log follows.

.........
2008-07-16 21:00:04.232 Started recording: Project Runway: channel 1048 on cardid 1, sourceid 1
2008-07-16 21:00:04.750 LFireDev(000F9FFFFE0C8799), Warning: No Input in 50 msec...
2008-07-16 21:00:04.806 LFireDev(000F9FFFFE0C8799), Warning: No Input in 100 msec...
..snip
2008-07-16 21:00:05.794 LFireDev(000F9FFFFE0C8799), Warning: No Input in 1050 msec...
2008-07-16 21:00:05.794 LFireDev(000F9FFFFE0C8799): ResetBus() -- begin
2008-07-16 21:00:05.826 LFireDev(000F9FFFFE0C8799): ResetBus() -- end
2008-07-16 21:00:05.827 LFireDev(000F9FFFFE0C8799): SignalReset(509->510)
2008-07-16 21:00:05.828 LFireDev(000F9FFFFE0C8799): SignalReset(509->510): Updating device list -- begin
2008-07-16 21:00:06.146 LFireDev(000F9FFFFE0C8799): SignalReset(509->510): Updating device list -- end
2008-07-16 21:00:06.198 LFireDev(000F9FFFFE0C8799), Warning: No Input in 50 msec...
2008-07-16 21:00:06.250 LFireDev(000F9FFFFE0C8799), Warning: No Input in 100 msec...
libiec61883 warning: iec61883_cmp_create_bcast_output: Failed to set the oPCR[0] plug for node 63.
2008-07-16 21:00:06.251 LFireDev(000F9FFFFE0C8799), Error: Bus Reset : Failed to reconnect
2008-07-16 21:00:06.302 LFireDev(000F9FFFFE0C8799), Warning: No Input in 150 msec...
..snip
2008-07-16 21:00:07.506 LFireDev(000F9FFFFE0C8799), Warning: No Input in 50 msec...
2008-07-16 21:00:07.558 LFireDev(000F9FFFFE0C8799), Warning: No Input in 100 msec...
2008-07-16 21:00:07.864 LFireDev(000F9FFFFE0C8799): Buffered packets 2000 (8000 KB)
2008-07-16 21:01:07.634 LFireDev(000F9FFFFE0C8799), Warning: No Input in 150 msec...
..snip
2008-07-16 21:01:10.298 LFireDev(000F9FFFFE0C8799), Warning: No Input in 100 msec...
2008-07-16 21:02:04.031 Reschedule requested for id -1.
2008-07-16 21:02:04.085 Scheduled 52 items in 0.1 = 0.01 match + 0.04 place
2008-07-16 21:02:09.562 LFireDev(000F9FFFFE0C8799), Warning: No Input in 150 msec...
2008-0V7-16 21:02:09.618 LFireDev(000F9FFFFE0C8799), Warning: No Input in 200 msec...
2008-07-16 21:02:09.674 LFireDev(000F9FFFFE0C8799), Warning: No Input in 250 msec...
2008-07-16 21:02:09.726 LFireDev(000F9FFFFE0C8799), Warning: No Input in 300 msec...
2008-07-16 21:02:09.778 LFireDev(000F9FFFFE0C8799), Warning: No Input in 350 msec...
.. big snip
2008-07-16 21:13:39.914 LFireDev(000F9FFFFE0C8799): ResetBus() -- begin
2008-07-16 21:13:39.915 LFireDev(000F9FFFFE0C8799): ResetBus() -- end
2008-07-16 21:13:39.916 LFireDev(000F9FFFFE0C8799): SignalReset(540->541)
2008-07-16 21:13:39.917 LFireDev(000F9FFFFE0C8799): SignalReset(540->541): Updating device list -- begin
2008-07-16 21:13:40.119 LFireDev(000F9FFFFE0C8799): SignalReset(540->541): Updating device list -- end
2008-07-16 21:13:40.170 LFireDev(000F9FFFFE0C8799), Warning: No Input in 50 msec...
2008-07-16 21:13:40.222 LFireDev(000F9FFFFE0C8799), Warning: No Input in 100 msec...

--- backend dies at this point. ---

---

### Post by ntsecrets on 2008-08-26
I've had this same issue with knoppmyth, on certain channels it will lose signal every 60 seconds, sometimes it recovers and sometimes it crashes.  I've talked to other myth users that have had the same issue, but not a whole lot is known about this issue.  I don't know if it is a firmware/box issue or a firewire hardware or what.  I have a 6200 box from RCN.  I even upgraded my kernel to 2.6.24-1-686.  Have you found out any more info?

Thanks in advance,
Mike

---

