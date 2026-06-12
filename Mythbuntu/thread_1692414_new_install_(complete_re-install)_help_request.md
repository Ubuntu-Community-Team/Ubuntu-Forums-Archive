---
title: "new install (complete re-install) help request"
date: 2011-02-21
forum: Mythbuntu
---

### Post by Rod_Myers on 2011-02-21
Hardware
CPU: 		AMD 1GHz
RAM: 		5 gb ram
Video Card: 	NVIDIA (not sure which model)
Remote: 	n/a
HD: 		300 gb hard drive
Tuners:		Hauppauge WinTV PVR-150 [ivtv]

cat /proc/version
Linux version 2.6.35-25-generic (buildd@palmer) (gcc version 4.4.5 (Ubuntu/Linaro 4.4.4-14ubuntu5) ) #44-Ubuntu SMP Fri Jan 21 17:40:48 UTC 2011


I had to re-install mythbuntu, after a 1 year layoff (moved cross country, and myth box sat packed in a box until this weekend. The initial install would not let me see any video from and computer monitor, and the network address changed with the move. Hence the re-install.

This is a backend only.

I have all recordings pointing to a different partition, with mythtv:mythtv ownership, for expansion purposes.

I think I have everything installed correctly, now the configuration is giving me problems. When I attempt to "record" from the "Listings" page, I get this in the error log file.

I'm not sure what I am missing in the configuration settings.

Any help would be appreciated.

Thanks

 tail -f /var/log/mythtv/mythbackend.log

2011-02-21 10:59:00.808 Reschedule requested for id 0.
2011-02-21 10:59:00.845 Scheduled 1 items in 0.0 = 0.01 match + 0.03 place
2011-02-21 10:59:20.831 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2011-02-21 10:59:30.840 TVRec(1): ASK_RECORDING 1 29 0 0
2011-02-21 11:00:02.916 TVRec(1): Changing from None to RecordingOnly
2011-02-21 11:00:02.929 TVRec(1): HW Tuner: 1->1
2011-02-21 11:00:02.966 ProgramInfo(): Updated pathname '':'' -> '1188_20110221110000.nuv'
sh: /dev/null: Permission denied
2011-02-21 11:00:03.024 ret_pid(4553) child(4553) status(0x7e00)
2011-02-21 11:00:03.032 ChannelBase: external tuning program exited with error 126
2011-02-21 11:00:03.040 TVRec(1) Error: Failed to set channel to 188. Reverting to kState_None
2011-02-21 11:00:03.056 TVRec(1): Changing from RecordingOnly to None
2011-02-21 11:00:03.078 ProgramInfo(): Updated pathname '':'' -> '1188_20110221110000.nuv'
2011-02-21 11:00:03.102 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2011-02-21 11:00:03.122 Canceled recording (Recorder Failed): The X-Files "Red Museum": channel 1188 on cardid 1, sourceid 1
2011-02-21 11:00:03.141 ProgramInfo(): Updated pathname '':'' -> '1188_20110221110000.nuv'
2011-02-21 11:00:03.154 ProgramInfo(1188_20110221110000.nuv), Error: GetPlaybackURL: '1188_20110221110000.nuv' should be local, but it can not be found.
2011-02-21 11:00:03.172 ProgramInfo(): Updated pathname '':'' -> '1188_20110221110000.nuv'
2011-02-21 11:00:03.222 ProgramInfo(): Updated pathname '':'' -> '1188_20110221110000.nuv'
2011-02-21 11:00:04.141 Reschedule requested for id 0.
2011-02-21 11:00:04.176 Scheduled 1 items in 0.0 = 0.01 match + 0.02 place
2011-02-21 11:00:06.175 ProgramInfo(): Updated pathname '':'' -> '1188_20110221110000.nuv'
2011-02-21 11:00:06.187 Error deleting 'GetPlaybackURL/UNABLE/TO/FIND/LOCAL/FILE/ON/mythtv/1188_20110221110000.nuv' could not open 
			eno: No such file or directory (2)
2011-02-21 11:00:06.200 Delete Error 'GetPlaybackURL/UNABLE/TO/FIND/LOCAL/FILE/ON/mythtv/1188_20110221110000.nuv'
			eno: No such file or directory (2)
2011-02-21 11:00:10.221 Reschedule requested for id 0.
2011-02-21 11:00:10.255 Scheduled 1 items in 0.0 = 0.01 match + 0.02 place
2011-02-21 11:14:20.881 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2011-02-21 11:17:01.762 MainServer::ANN Monitor
2011-02-21 11:17:01.769 adding: mythtv as a client (events: 0)
2011-02-21 11:29:20.934 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2011-02-21 11:44:20.984 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min

---

### Post by tgm4883 on 2011-02-21
> **Rod_Myers said:**
> 2011-02-21 11:00:02.966 ProgramInfo(): Updated pathname '':'' -> '1188_20110221110000.nuv'
sh: /dev/null: Permission denied

I've cut out both of the errors.

1) .nuv file. You have a PVR-150 so you should have mpg files. Set up your tuner correctly in mythtv-setup. It is an ivtv card

2) permission denied. Obviously permission issues. Either where it's trying to record (which you should have gotten a warning when exiting mythtv-setup that it couldn't write to the recording directory) or possibly it cannot run the channel change script if you use one of those.

---

### Post by Rod_Myers on 2011-02-21
> **tgm4883 said:**
> I've cut out both of the errors.

1) .nuv file. You have a PVR-150 so you should have mpg files. Set up your tuner correctly in mythtv-setup. It is an ivtv card

2) permission denied. Obviously permission issues. Either where it's trying to record (which you should have gotten a warning when exiting mythtv-setup that it couldn't write to the recording directory) or possibly it cannot run the channel change script if you use one of those.

Double-checked. The PVR-150 is selected, and it shows as such. No idea why it still creates nuv files.

No warnings when exiting mythtv-setup about permissions.

I removed the "channel changing" info, and the "permission denied" problem went away, I know get this;


2011-02-21 14:22:41.536 adding: mythtv as a client (events: 2)
2011-02-21 14:22:41.575 MainServer::ANN Monitor
2011-02-21 14:22:41.580 adding: mythtv as a client (events: 2)
2011-02-21 14:22:41.596 MainServer::ANN Monitor
2011-02-21 14:22:41.608 adding: mythtv as a client (events: 2)
2011-02-21 14:22:41.617 Reschedule requested for id 10.
2011-02-21 14:22:41.655 Scheduled 3 items in 0.0 = 0.02 match + 0.02 place
2011-02-21 14:22:41.664 TVRec(1): ASK_RECORDING 1 0 0 0
2011-02-21 14:22:41.811 TVRec(1): Changing from None to RecordingOnly
2011-02-21 14:22:41.820 TVRec(1): HW Tuner: 1->1
2011-02-21 14:22:41.866 Channel(/dev/video0) Warning: You have not set an external channel changing
			script for a composite or s-video input. Channel changing will do nothing.
2011-02-21 14:22:41.869 MainServer::ANN Monitor
2011-02-21 14:22:41.904 adding: mythtv as a client (events: 2)
2011-02-21 14:22:41.898 TVRec(1): rec->GetFileName(): '/store/recordings/1161_20110221142300.nuv'
2011-02-21 14:22:41.967 NVR(/dev/video0): Unknown video codec.  Please go into the TV Settings, Recording Profiles and setup the four 'Software Encoders' profiles.  Assuming RTjpeg for now.
2011-02-21 14:22:41.972 NVR(/dev/video0) Error: Unknown audio codec
2011-02-21 14:22:41.991 AudioInALSA(default) Error: failed to get periods: Invalid argument
2011-02-21 14:22:41.996 NVR(/dev/video0) Error: Failed to open audio device ALSA:default
2011-02-21 14:22:42.016 NVR(/dev/video0) Error: Failed to init audio input device
2011-02-21 14:22:42.045 NVR(/dev/video0): Won't work with the streaming interface, falling back
VIDIOCGMBUF:: Invalid argument
2011-02-21 14:22:42.085 AudioInALSA(default) Error: failed to get periods: Invalid argument
2011-02-21 14:22:42.100 NVR(/dev/video0) Error: Failed to open audio device ALSA:default
2011-02-21 14:22:42.128 TVRec(1): Changing from RecordingOnly to None
2011-02-21 14:22:42.147 ProgramInfo(): Updated pathname '':'' -> '1161_20110221142300.nuv'
2011-02-21 14:22:42.159 ProgramInfo(1161_20110221142300.nuv), Error: Unknown type, recording width was 0
2011-02-21 14:22:42.206 ProgramInfo(): Updated pathname '':'' -> '1161_20110221142300.nuv'
2011-02-21 14:22:42.233 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2011-02-21 14:22:42.264 Started recording: Monk "Mr. Monk and the End, Part II": channel 1161 on cardid 1, sourceid 1
2011-02-21 14:22:42.300 ProgramInfo(): Updated pathname '':'' -> '1161_20110221142300.nuv'
2011-02-21 14:22:42.320 ProgramInfo(): Updated pathname '':'' -> '1161_20110221142300.nuv'
2011-02-21 14:22:42.459 MainServer::ANN Monitor
2011-02-21 14:22:42.468 adding: mythtv as a client (events: 2)
2011-02-21 14:22:42.510 MainServer::ANN Monitor
2011-02-21 14:22:42.516 adding: mythtv as a client (events: 2)
2011-02-21 14:22:42.539 MainServer::ANN Monitor
2011-02-21 14:22:42.545 adding: mythtv as a client (events: 2)
2011-02-21 14:22:42.721 mythbackend version: branches/release-0-23-fixes [26437] [www.mythtv.org](www.mythtv.org)
2011-02-21 14:22:42.728 Using runtime prefix = /usr
2011-02-21 14:22:42.744 Using configuration directory = /home/mythtv/.mythtv
2011-02-21 14:22:42.760 Empty LocalHostName.
2011-02-21 14:22:42.784 Using localhost value of mythtv
2011-02-21 14:22:42.813 New DB connection, total: 1
2011-02-21 14:22:42.826 Connected to database 'mythconverg' at host: localhost
2011-02-21 14:22:42.852 Closing DB connection named 'DBManager0'
2011-02-21 14:22:42.865 Connected to database 'mythconverg' at host: localhost
2011-02-21 14:22:42.893 Current MythTV Schema Version (DBSchemaVer): 1254
2011-02-21 14:22:42.922 ProgramInfo(): Updated pathname '':'' -> '1161_20110221142300.nuv'
2011-02-21 14:22:42.942 Preview Error: Previewer file '/store/recordings/1161_20110221142300.nuv' is not valid.
2011-02-21 14:22:42.950 Preview Error: Run() file not local: '/store/recordings/1161_20110221142300.nuv'
2011-02-21 14:22:42.975 ~MythContext waiting for threads to exit.
2011-02-21 14:22:43.043 Preview Error: Encountered problems running '/usr/bin/mythbackend --generate-preview 0x0 --chanid 1161 --starttime 20110221142300 '
2011-02-21 14:22:43.301 Reschedule requested for id 0.
2011-02-21 14:22:43.308 Reschedule requested for id 10.
2011-02-21 14:22:43.359 Scheduled 3 items in 0.1 = 0.03 match + 0.03 place
2011-02-21 14:22:43.529 MainServer::ANN Monitor
2011-02-21 14:22:43.536 adding: mythtv as a client (events: 2)
2011-02-21 14:23:29.528 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min

---

### Post by nickrout on 2011-02-21
I believe you have your card set up as a v4l card, not a IVTV Mpeg-2 encoder card. Please check again.

---

### Post by tgm4883 on 2011-02-21
Yep check it again, it should be a IVTV card. Post a screenshot here if you need to.

The permission issue is likely because permissions are incorrect on your channel change script.  

What is the output of

```
ls -l /path/to/channel_change/script
```

---

### Post by Rod_Myers on 2011-02-21
> **nickrout said:**
> I believe you have your card set up as a v4l card, not a IVTV Mpeg-2 encoder card. Please check again.

Yes I did, that was the default. Now changed, and appears to be working.

Thank you

---

### Post by Rod_Myers on 2011-02-21
> **tgm4883 said:**
> Yep check it again, it should be a IVTV card. Post a screenshot here if you need to.

The permission issue is likely because permissions are incorrect on your channel change script.  

What is the output of

```
ls -l /path/to/channel_change/script
```

I don't have it changing channels, no script inserted. At this point in time

---

### Post by nickrout on 2011-02-22
oops misread, nice it's working

---

### Post by Rod_Myers on 2011-02-22
> **nickrout said:**
> oops misread, nice it's working

No idea why was not set that way by default. 

Just checked again this morning, and records as it should.

thank you all.

---

### Post by tgm4883 on 2011-02-22
> **Rod_Myers said:**
> No idea why was not set that way by default. 

Just checked again this morning, and records as it should.

thank you all.

There is no default. We don't guess what tuner card you have, that is something you set yourself.

---

### Post by Rod_Myers on 2011-02-22
Did not know that.

Now I do. thanks

---

