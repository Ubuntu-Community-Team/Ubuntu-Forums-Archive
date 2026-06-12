---
title: "LiveTV Stopped working"
date: 2008-03-17
forum: Mythbuntu
---

### Post by pdragon04 on 2008-03-17
My LiveTV just suddenly stopped working today. Was working fine last week and I haven't changed anything. Watched a few videos from MythVideo yesterday, but that's about all I did with it this weekend.

Getting this in the Frontend and Backend Logs

2008-03-17 18:20:02.893 TV: Attempting to change from None to WatchingLiveTV
2008-03-17 18:20:02.896 Using Idle Timer. 240 minutes
2008-03-17 18:20:02.898 Using protocol version 40
2008-03-17 18:20:16.796 RingBuf(/opt/mythtv/recordings/1059_20080317182009.mpg): Invalid file (fd -1) when opening '/opt/mythtv/recordings/1059_20080317182009.mpg'.
2008-03-17 18:20:16.825 NVP::OpenFile(): Error, file not found: /opt/mythtv/recordings/1059_20080317182009.mpg
2008-03-17 18:20:16.829 TV Error: StartPlayer(): NVP is not playing after 20000 msec
2008-03-17 18:20:16.841 DPMS Deactivated 
2008-03-17 18:20:20.693 TV Error: LiveTV not successfully started
2008-03-17 18:20:20.752 DPMS Reactivated.

Gives a different file name every time. I've checked the permissions on the recordings folder and everything is as it was before. 

Any ideas?

---

### Post by pdragon04 on 2008-03-17
2008-03-17 18:41:15.246 TVRec(1): Changing from None to WatchingLiveTV
2008-03-17 18:41:15.256 TVRec(1): HW Tuner: 1->1
2008-03-17 18:41:16.707 MPEGRec(/dev/video0) Warning: Audio sample rate 32000 Hz
                        is not supported by ivtv driver, using 48000 Hz instead.
2008-03-17 18:41:16.715 AutoExpire: CalcParams(): Max required Free Space: 16.0 GB w/freq: 15 min
2008-03-17 18:41:22.475 MPEGRec(/dev/video0) Error: select timeout - ivtv driver has stopped responding
2008-03-17 18:41:23.275 TVRec(1): Changing from WatchingLiveTV to None


Had that for my backend log. Seems ivtv failed to load properly. Rebooting fixed it. This is the second problem I've run into since upgrading to .21 that keeps requiring me to reboot my mythtv box to fix it. Was hoping I wouldn't have to reload for 8.04, but looks like I am at this point.

---

