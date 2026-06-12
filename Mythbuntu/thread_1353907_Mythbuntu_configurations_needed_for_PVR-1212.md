---
title: "Mythbuntu configurations needed for PVR-1212"
date: 2009-12-13
forum: Mythbuntu
---

### Post by Jumping_jackas on 2009-12-13
Backend is a SFF HP 5150 with 9.10 Mythbuntu and a PVR-1212 HDPVR. Frontend is a SFF HP 5150 with 9.10 Mythbuntu.

I can not get "watch tv" to work. I guess it is because the backend is not setup correctly to trap the source stream from the pvr-1212 HD PVR. cat /dev/video0 > test.ts works fine and VLC "open capture device" on the backend works fine. Thanks for your help in advance. The next chalange after this will be configuring the IRBlaster to change the channels on my DCT1000 motorola STB.


snip from backend logfile:

2009-12-13 06:39:07.216 MainServer::ANN Monitor
2009-12-13 06:39:07.268 TVRec(1): HW Tuner: 1->1
2009-12-13 06:39:07.304 adding: MythtvBackend as a client (events: 1)
2009-12-13 06:39:07.489 Channel(/dev/video0)::Tune(): Error -1 while setting frequency (v2): Invalid argument
2009-12-13 06:39:07.529 TVRec(1) Error: Failed to set channel to 66. Reverting to kState_None
2009-12-13 06:39:07.579 TVRec(1): Changing from Watching RecordingOnly to None
2009-12-13 06:39:07.672 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2009-12-13 06:39:07.736 Canceled recording (Recorder Failed): Tom & Jerry: channel 1066 on cardid 1, sourceid 1
2009-12-13 06:39:07.792 ProgramInfo, Error: GetPlaybackURL: '1066_20091213063900.mpg' should be local, but it can not be found.
2009-12-13 06:39:08.779 Reschedule requested for id 0.
2009-12-13 06:39:08.891 Scheduled 1 items in 0.1 = 0.05 match + 0.06 place
2009-12-13 06:39:10.860 Error deleting '/GetPlaybackURL/UNABLE/TO/FIND/LOCAL/FILE/ON/MythtvBackend/1066_20091213063900.mpg' could not open
                        eno: No such file or directory (2)
2009-12-13 06:39:10.908 Delete Error '/GetPlaybackURL/UNABLE/TO/FIND/LOCAL/FILE/ON/MythtvBackend/1066_20091213063900.mpg'
                        eno: No such file or directory (2)
2009-12-13 06:39:14.963 Reschedule requested for id 0.

---

### Post by Jumping_jackas on 2009-12-14
rectal cranial inversion prevented me from reading the ALL of the instructions. including these;

**Important Note:** You must set a channel change script for the HD-PVR to work properly. If you don't care about channel changes, you can set it to /bin/true, but there absolutely must be a channel change script defined. 
**Important Note 2:** You must leave Preset tuner to channel empty or LiveTV and channel changes will not work


Now I only need to resolve the ability to remote control my DCT1000 Motorola STB.

---

