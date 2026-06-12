---
title: "How do I make FireWire more reliable?"
date: 2008-03-06
forum: Mythbuntu
---

### Post by volkswagner on 2008-03-06
I have followed the myth firewire how to.  I have Time Warner, NY with SA3250HD box.

Channel changing works great.  I am using sa3250ch via FW  for my S-video input on my pvr150.  Firewire capture is very unreliable.  It is even more unpredictable.  

I have the primer working on startup. I have permissions sorted out.

 When I go to live tv it breaks the firewire connection.  I have confirmed this via an ssh session.  If I try live tv, and get no connection, a bus reset usually gets a good p2p response in the terminal.  If I try live tv again, I will have to reset the FW bus to get a good p2p.  I can get reliable p2p, even after issuing channel changes.  Myth tv seems to break the connection.

Is there anything I can do to see if this is due to the cable box or myth.  I realize my thinking that reliable channel changes should equate to reliable capture is naive. 

here are some of the logs at the crash.

From Frontend log

```
2008-03-06 19:06:46.891 New DB connection, total: 2

2008-03-06 19:06:46.891 Connected to database 'mythconverg' at host: localhost

SIP listening on IP Address 192.168.1.107:5060 NAT address 192.168.1.107

SIP: Cannot register; proxy, username or password not set

2008-03-06 19:06:55.743 Connecting to backend server: 192.168.1.107:6543 (try 1 of 5)

2008-03-06 19:06:55.744 Using protocol version 31

2008-03-06 19:06:55.758 TV: Attempting to change from None to WatchingLiveTV

2008-03-06 19:06:55.758 Using protocol version 31

2008-03-06 19:07:03.354 RingBuf(/var/lib/mythtv/recordings/4115_20080306190656.mpg): Invalid file (fd -1) when opening '/var/lib/mythtv/recordings/4115_2008$

2008-03-06 19:07:03.358 DPMS Deactivated

2008-03-06 19:07:03.371 NVP::OpenFile(): Error, file not found: /var/lib/mythtv/recordings/4115_20080306190656.mpg

2008-03-06 19:07:03.378 TV Error: StartPlayer(): NVP is not playing after 20000 msec

2008-03-06 19:07:10.379 MythSocket(22f08e0:19): readStringList: Error, timeout (quick).

2008-03-06 19:07:10.379 RemoteEncoder::SendReceiveStringList(): No response.

2008-03-06 19:07:10.381 TV Error: LiveTV not successfully started

2008-03-06 19:07:10.391 DPMS Reactivated.

2008-03-06 19:08:20.590 TV: Attempting to change from None to WatchingLiveTV

2008-03-06 19:08:20.590 Using protocol version 31

2008-03-06 19:08:28.166 RingBuf(/var/lib/mythtv/recordings/4115_20080306190821.mpg): Invalid file (fd -1) when opening '/var/lib/mythtv/recordings/4115_2008$

2008-03-06 19:08:28.167 DPMS Deactivated

2008-03-06 19:08:28.173 NVP::OpenFile(): Error, file not found: /var/lib/mythtv/recordings/4115_20080306190821.mpg

2008-03-06 19:08:28.178 TV Error: StartPlayer(): NVP is not playing after 20000 msec

2008-03-06 19:08:35.179 MythSocket(16b7210:19): readStringList: Error, timeout (quick).

2008-03-06 19:08:35.179 RemoteEncoder::SendReceiveStringList(): No response.

2008-03-06 19:08:35.181 TV Error: LiveTV not successfully started

2008-03-06 19:08:35.195 DPMS Reactivated.
```


Backend Log
```

2008-03-06 19:06:55.764 TVRec(4): Changing from None to WatchingLiveTV

2008-03-06 19:06:55.771 TVRec(4): HW Tuner: 4->4

node 0: vendor_id = 0x00001692 model_id = 0x00000be0

Using single number channel change command method

AV/C Command: cmd0=0x00487ce7 cmd1=0x04007300 cmd2=0x00000000

2008-03-06 19:06:56.806 ret_pid(10568) child(10568) status(0x0)

2008-03-06 19:06:56.810 External Tuning program exited with no error

libiec61883 warning: Overlayed connection on channel 0.

You may need to manually set the channel on the receiving node.

2008-03-06 19:06:56.863 FireRec: Buffered packets 2000 (8000 KB)

2008-03-06 19:07:03.380 TVRec(4): Changing from WatchingLiveTV to None

2008-03-06 19:07:11.871 FireRec: No Input in 15 seconds [P:0 N:0] (select)

2008-03-06 19:07:11.886 Finished recording Dora the Explorer "Treasure Island": channel 4115

2008-03-06 19:07:11.893 scheduler: Finished recording: Dora the Explorer "Treasure Island": channel 4115

2008-03-06 19:07:11.903 MythSocket(2aaaac0101a0:-1): writeStringList: Error, socket went unconnected.

2008-03-06 19:08:20.591 MainServer::HandleAnnounce Playback

2008-03-06 19:08:20.592 adding: FamilyRoom as a client (events: 0)

2008-03-06 19:08:20.593 TVRec(4): Changing from None to WatchingLiveTV

2008-03-06 19:08:20.595 TVRec(4): HW Tuner: 4->4

node 0: vendor_id = 0x00001692 model_id = 0x00000be0

Using single number channel change command method

AV/C Command: cmd0=0x00487ce7 cmd1=0x04007300 cmd2=0x00000000

2008-03-06 19:08:21.634 ret_pid(10582) child(10582) status(0x0)

2008-03-06 19:08:21.638 External Tuning program exited with no error

libiec61883 warning: Overlayed connection on channel 0.

You may need to manually set the channel on the receiving node.

2008-03-06 19:08:21.674 FireRec: Buffered packets 2000 (8000 KB)

2008-03-06 19:08:23.525 FireRec, Error: TS packet out of sync.

2008-03-06 19:08:23.526 FireRec, Error: TS packet out of sync.

2008-03-06 19:08:23.526 FireRec, Error: TS packet out of sync.

2008-03-06 19:08:23.527 FireRec, Error: TS packet out of sync.

2008-03-06 19:08:23.527 FireRec, Error: TS packet out of sync.

2008-03-06 19:08:23.528 FireRec, Error: TS packet out of sync.

	Edit
2008-03-06 19:08:23.689 FireRec, Error: TS packet out of sync.

2008-03-06 19:08:23.690 FireRec, Error: TS packet out of sync.

2008-03-06 19:08:23.690 FireRec, Error: TS packet out of sync.

2008-03-06 19:08:23.691 FireRec, Error: TS packet out of sync.

2008-03-06 19:08:28.179 TVRec(4): Changing from WatchingLiveTV to None

2008-03-06 19:08:38.691 FireRec: No Input in 15 seconds [P:0 N:0] (select)

2008-03-06 19:08:38.708 Finished recording Dora the Explorer "Treasure Island": channel 4115

2008-03-06 19:08:38.723 MythSocket(2aaaac0101a0:-1): writeStringList: Error, socket went unconnected.

2008-03-06 19:08:49.302 Expiring Dora the Explorer "Treasure Island" from Thu Mar 6 19:00:00 2008, 0 MBytes, forced expire (LiveTV recording)

2008-03-06 19:10:49.495 Expiring Dora the Explorer "Treasure Island" from Thu Mar 6 19:00:00 2008, 0 MBytes, forced expire (LiveTV recording)
```



Was working now change channels several times broke at channel 64

Frontend log
```

2008-03-06 19:51:44.129 NVP: prebuffering pause

2008-03-06 19:51:46.174 NVP: Prebuffer wait timed out 10 times.

2008-03-06 19:51:46.736 AFD: Opened codec 0x2aaacc01d220, id(MPEG2VIDEO) type(Video)

2008-03-06 19:51:46.737 AFD: Opened codec 0x2aaacc01d790, id(AC3) type(Audio)

2008-03-06 19:52:08.366 NVP: prebuffering pause

2008-03-06 19:52:10.475 NVP: Prebuffer wait timed out 10 times.

2008-03-06 19:52:12.579 NVP: Prebuffer wait timed out 10 times.

2008-03-06 19:52:14.663 NVP: Prebuffer wait timed out 10 times.

2008-03-06 19:52:16.087 RingBuf(/var/lib/mythtv/recordings/4064_20080306195208.mpg): Invalid file (fd -1) when opening '/var/lib/mythtv/recordings/4064_2008$

2008-03-06 19:52:16.087 NVP, Error: JumpToProgram's OpenFile failed.

2008-03-06 19:52:16.098 TV: Attempting to change from WatchingLiveTV to None

2008-03-06 19:52:23.100 MythSocket(16de1b0:19): readStringList: Error, timeout (quick).

2008-03-06 19:52:23.100 RemoteEncoder::SendReceiveStringList(): No response.

2008-03-06 19:52:23.469 TV: Changing from WatchingLiveTV to None

2008-03-06 19:52:23.476 DPMS Reactivated.
```

---

### Post by majoridiot on 2008-03-07
> **volkswagner said:**
> I have followed the myth firewire how to.  I have Time Warner, NY with SA3250HD box.

Channel changing works great.  I am using sa3250ch via FW  for my S-video input on my pvr150.  Firewire capture is very unreliable.  It is even more unpredictable.  

I have the primer working on startup. I have permissions sorted out.

 When I go to live tv it breaks the firewire connection.  I have confirmed this via an ssh session.  If I try live tv, and get no connection, a bus reset usually gets a good p2p response in the terminal.  If I try live tv again, I will have to reset the FW bus to get a good p2p.  I can get reliable p2p, even after issuing channel changes.  Myth tv seems to break the connection.

Is there anything I can do to see if this is due to the cable box or myth.  I realize my thinking that reliable channel changes should equate to reliable capture is naive. 

here are some of the logs at the crash.

From Frontend log

```
2008-03-06 19:06:46.891 New DB connection, total: 2

2008-03-06 19:06:46.891 Connected to database 'mythconverg' at host: localhost

SIP listening on IP Address 192.168.1.107:5060 NAT address 192.168.1.107

SIP: Cannot register; proxy, username or password not set

2008-03-06 19:06:55.743 Connecting to backend server: 192.168.1.107:6543 (try 1 of 5)

2008-03-06 19:06:55.744 Using protocol version 31

2008-03-06 19:06:55.758 TV: Attempting to change from None to WatchingLiveTV

2008-03-06 19:06:55.758 Using protocol version 31

2008-03-06 19:07:03.354 RingBuf(/var/lib/mythtv/recordings/4115_20080306190656.mpg): Invalid file (fd -1) when opening '/var/lib/mythtv/recordings/4115_2008$

2008-03-06 19:07:03.358 DPMS Deactivated

2008-03-06 19:07:03.371 NVP::OpenFile(): Error, file not found: /var/lib/mythtv/recordings/4115_20080306190656.mpg

2008-03-06 19:07:03.378 TV Error: StartPlayer(): NVP is not playing after 20000 msec

2008-03-06 19:07:10.379 MythSocket(22f08e0:19): readStringList: Error, timeout (quick).

2008-03-06 19:07:10.379 RemoteEncoder::SendReceiveStringList(): No response.

2008-03-06 19:07:10.381 TV Error: LiveTV not successfully started

2008-03-06 19:07:10.391 DPMS Reactivated.

2008-03-06 19:08:20.590 TV: Attempting to change from None to WatchingLiveTV

2008-03-06 19:08:20.590 Using protocol version 31

2008-03-06 19:08:28.166 RingBuf(/var/lib/mythtv/recordings/4115_20080306190821.mpg): Invalid file (fd -1) when opening '/var/lib/mythtv/recordings/4115_2008$

2008-03-06 19:08:28.167 DPMS Deactivated

2008-03-06 19:08:28.173 NVP::OpenFile(): Error, file not found: /var/lib/mythtv/recordings/4115_20080306190821.mpg

2008-03-06 19:08:28.178 TV Error: StartPlayer(): NVP is not playing after 20000 msec

2008-03-06 19:08:35.179 MythSocket(16b7210:19): readStringList: Error, timeout (quick).

2008-03-06 19:08:35.179 RemoteEncoder::SendReceiveStringList(): No response.

2008-03-06 19:08:35.181 TV Error: LiveTV not successfully started

2008-03-06 19:08:35.195 DPMS Reactivated.
```


Backend Log
```

2008-03-06 19:06:55.764 TVRec(4): Changing from None to WatchingLiveTV

2008-03-06 19:06:55.771 TVRec(4): HW Tuner: 4->4

node 0: vendor_id = 0x00001692 model_id = 0x00000be0

Using single number channel change command method

AV/C Command: cmd0=0x00487ce7 cmd1=0x04007300 cmd2=0x00000000

2008-03-06 19:06:56.806 ret_pid(10568) child(10568) status(0x0)

2008-03-06 19:06:56.810 External Tuning program exited with no error

libiec61883 warning: Overlayed connection on channel 0.

You may need to manually set the channel on the receiving node.

2008-03-06 19:06:56.863 FireRec: Buffered packets 2000 (8000 KB)

2008-03-06 19:07:03.380 TVRec(4): Changing from WatchingLiveTV to None

2008-03-06 19:07:11.871 FireRec: No Input in 15 seconds [P:0 N:0] (select)

2008-03-06 19:07:11.886 Finished recording Dora the Explorer "Treasure Island": channel 4115

2008-03-06 19:07:11.893 scheduler: Finished recording: Dora the Explorer "Treasure Island": channel 4115

2008-03-06 19:07:11.903 MythSocket(2aaaac0101a0:-1): writeStringList: Error, socket went unconnected.

2008-03-06 19:08:20.591 MainServer::HandleAnnounce Playback

2008-03-06 19:08:20.592 adding: FamilyRoom as a client (events: 0)

2008-03-06 19:08:20.593 TVRec(4): Changing from None to WatchingLiveTV

2008-03-06 19:08:20.595 TVRec(4): HW Tuner: 4->4

node 0: vendor_id = 0x00001692 model_id = 0x00000be0

Using single number channel change command method

AV/C Command: cmd0=0x00487ce7 cmd1=0x04007300 cmd2=0x00000000

2008-03-06 19:08:21.634 ret_pid(10582) child(10582) status(0x0)

2008-03-06 19:08:21.638 External Tuning program exited with no error

libiec61883 warning: Overlayed connection on channel 0.

You may need to manually set the channel on the receiving node.

2008-03-06 19:08:21.674 FireRec: Buffered packets 2000 (8000 KB)

2008-03-06 19:08:23.525 FireRec, Error: TS packet out of sync.

2008-03-06 19:08:23.526 FireRec, Error: TS packet out of sync.

2008-03-06 19:08:23.526 FireRec, Error: TS packet out of sync.

2008-03-06 19:08:23.527 FireRec, Error: TS packet out of sync.

2008-03-06 19:08:23.527 FireRec, Error: TS packet out of sync.

2008-03-06 19:08:23.528 FireRec, Error: TS packet out of sync.

	Edit
2008-03-06 19:08:23.689 FireRec, Error: TS packet out of sync.

2008-03-06 19:08:23.690 FireRec, Error: TS packet out of sync.

2008-03-06 19:08:23.690 FireRec, Error: TS packet out of sync.

2008-03-06 19:08:23.691 FireRec, Error: TS packet out of sync.

2008-03-06 19:08:28.179 TVRec(4): Changing from WatchingLiveTV to None

2008-03-06 19:08:38.691 FireRec: No Input in 15 seconds [P:0 N:0] (select)

2008-03-06 19:08:38.708 Finished recording Dora the Explorer "Treasure Island": channel 4115

2008-03-06 19:08:38.723 MythSocket(2aaaac0101a0:-1): writeStringList: Error, socket went unconnected.

2008-03-06 19:08:49.302 Expiring Dora the Explorer "Treasure Island" from Thu Mar 6 19:00:00 2008, 0 MBytes, forced expire (LiveTV recording)

2008-03-06 19:10:49.495 Expiring Dora the Explorer "Treasure Island" from Thu Mar 6 19:00:00 2008, 0 MBytes, forced expire (LiveTV recording)
```



Was working now change channels several times broke at channel 64

Frontend log
```

2008-03-06 19:51:44.129 NVP: prebuffering pause

2008-03-06 19:51:46.174 NVP: Prebuffer wait timed out 10 times.

2008-03-06 19:51:46.736 AFD: Opened codec 0x2aaacc01d220, id(MPEG2VIDEO) type(Video)

2008-03-06 19:51:46.737 AFD: Opened codec 0x2aaacc01d790, id(AC3) type(Audio)

2008-03-06 19:52:08.366 NVP: prebuffering pause

2008-03-06 19:52:10.475 NVP: Prebuffer wait timed out 10 times.

2008-03-06 19:52:12.579 NVP: Prebuffer wait timed out 10 times.

2008-03-06 19:52:14.663 NVP: Prebuffer wait timed out 10 times.

2008-03-06 19:52:16.087 RingBuf(/var/lib/mythtv/recordings/4064_20080306195208.mpg): Invalid file (fd -1) when opening '/var/lib/mythtv/recordings/4064_2008$

2008-03-06 19:52:16.087 NVP, Error: JumpToProgram's OpenFile failed.

2008-03-06 19:52:16.098 TV: Attempting to change from WatchingLiveTV to None

2008-03-06 19:52:23.100 MythSocket(16de1b0:19): readStringList: Error, timeout (quick).

2008-03-06 19:52:23.100 RemoteEncoder::SendReceiveStringList(): No response.

2008-03-06 19:52:23.469 TV: Changing from WatchingLiveTV to None

2008-03-06 19:52:23.476 DPMS Reactivated.
```

does your sa3250HD have more than one firewire port?  if so, have you tried the other port for reliability?
in my experience, on SA boxes with two ports, both will *seem* to test ok with the tester, but only one
of the two if fully functional- the other tends to be either crippled or extremely flaky.  this seems to be a
possibility, since the logs do indicate that you are at times getting *something* from the stb.

if you have already tried this, then more info on your setup might help.  what port, node and method
of connection (p2p or broadcast) are you using?

---

### Post by volkswagner on 2008-03-07
Thanks for the reply and the excellent How to.

My sa3250hd has two FW ports.  When I first setup the box, I discovered one port was useless.  I had zero luck with broadcast.  I am using p2p.  The plugreport shows port 0, node 0.  I had to add the -s -v switches to the channel change command to get it to work.

I can't find a common denominator on when the connection breaks.  I am starting to think TWcable is the culprit or maybe the box.

It seems to me the command to reset the bus is less effective now, compared to when I first got things working.  Could this be due to running updates on mythbuntu?

Since the Firewire was the last card I installed, myth will alway choose it first.  The fact that it rarely works without fiddeling, caused me to delete the input until I can get it sorted.

---

### Post by majoridiot on 2008-03-07
> **volkswagner said:**
> Thanks for the reply and the excellent How to.

My sa3250hd has two FW ports.  When I first setup the box, I discovered one port was useless.  I had zero luck with broadcast.  I am using p2p.  The plugreport shows port 0, node 0.  I had to add the -s -v switches to the channel change command to get it to work.

I can't find a common denominator on when the connection breaks.  I am starting to think TWcable is the culprit or maybe the box.

It seems to me the command to reset the bus is less effective now, compared to when I first got things working.  Could this be due to running updates on mythbuntu?

Since the Firewire was the last card I installed, myth will alway choose it first.  The fact that it rarely works without fiddeling, caused me to delete the input until I can get it sorted.

was it just a livetv issue or would you have recordings fail, too?

---

### Post by volkswagner on 2008-03-08
Recordings also Failed.  The recorded program would show up as an empty file, in the recordings directory.

---

### Post by majoridiot on 2008-03-08
> **volkswagner said:**
> Recordings also Failed.  The recorded program would show up as an empty file, in the recordings directory.

from what you are describing, it sounds like a problem with the stb.

if you have correctly handled permissions, priming and tuner configurations for the firewire connection
and still are just hit-and-miss with reliability, then it pretty much has to be the cable box.  since you have 
already tried both ports on the stb and only found one functional, i would say it is a distinct possibility
you have a flaky box and should consider swapping it out with the cable co.

if you want to try more troubleshooting, i'm willing to try and help you out remotely, to see if i can find a 
problem.  feel free to PM me if you would like to give this a shot next week.

---

### Post by volkswagner on 2008-03-08
> **majoridiot said:**
> from what you are describing, it sounds like a problem with the stb.

if you have correctly handled permissions, priming and tuner configurations for the firewire connection
and still are just hit-and-miss with reliability, then it pretty much has to be the cable box.  since you have 
already tried both ports on the stb and only found one functional, i would say it is a distinct possibility
you have a flaky box and should consider swapping it out with the cable co.

if you want to try more troubleshooting, i'm willing to try and help you out remotely, to see if i can find a 
problem.  feel free to PM me if you would like to give this a shot next week.

This is most generous of you.  Before I spend  anymore time, I will gladly exchange the cablebox.  TWcable is in my home town.  Your response hints that firewire should be more stable.  I have seen so many people with troubles I thought it may be the nature of the beast.  I am aware that exchanging faulty boxes is common.  Not just for firewire problems.  I think this is a five or six year old device.

I will post back next week with results of the new box.

Thanks again.  

Cheers

---

