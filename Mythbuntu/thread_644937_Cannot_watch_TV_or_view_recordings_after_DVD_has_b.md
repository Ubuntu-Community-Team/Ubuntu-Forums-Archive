---
title: "Cannot watch TV or view recordings after DVD has been in drive"
date: 2007-12-19
forum: Mythbuntu
---

### Post by andrewb78 on 2007-12-19
After a DVD has been in the drive, I cannot watch TV or view recordings. If I try to watch TV, I can change channels and everything, but the video is otherwise black and there is no audio.  If I try to view recordings, after selecting a recording and pressing OK on the remote, I just get the recording menu again after a short pause.  Since DVD viewing isn't working either, it is possible that this issue is related to [http://ubuntuforums.org/showthread.php?t=575130](http://ubuntuforums.org/showthread.php?t=575130).  If there has been no DVD in the drive since boot, both watching TV and viewing recordings work fine.

My setup is Mythbuntu gutsy on AMD64 with a Hauppauge PVR-350.  I am using the TV Out on the PVR-350.  I am using the updates at [http://ppa.launchpad.net/superm1/ubuntu](http://ppa.launchpad.net/superm1/ubuntu) so that the TV Out works correctly.  When I select the "Watch TV" function, the blank screen occurs and the following lines are added to /var/log/mythtv/mythfrontend.log:

```

2007-12-19 12:47:04.350 TV: Attempting to change from None to WatchingLiveTV
2007-12-19 12:47:04.351 Using protocol version 31
2007-12-19 12:47:05.398 IVD: ivtv version 1.0.0
2007-12-19 12:47:05.429 Using the PVR-350 decoder/TV-out
2007-12-19 12:47:05.624 Realtime priority would require SUID as root.
2007-12-19 12:47:05.624 TV: Changing from None to WatchingLiveTV
2007-12-19 12:47:05.627 IVD Error: Writing to decoder
                        eno: Device or resource busy (16)


```

When selecting a recording to watch, I briefly get a blank screen before going back to the recording menu, and the following is added to /var/log/mythtv/mythfrontend.log:

```

2007-12-19 12:52:26.596 TV: Attempting to change from None to WatchingPreRecorded
2007-12-19 12:52:26.687 IVD: ivtv version 1.0.0
2007-12-19 12:52:26.720 Using the PVR-350 decoder/TV-out
2007-12-19 12:52:26.907 Realtime priority would require SUID as root.
2007-12-19 12:52:26.908 IVD Error: Writing to decoder
                        eno: Device or resource busy (16)
2007-12-19 12:52:26.910 TV: Changing from None to WatchingPreRecorded
2007-12-19 12:52:26.949 TV: Attempting to change from WatchingPreRecorded to None
2007-12-19 12:52:26.977 TV: Changing from WatchingPreRecorded to None
0: start_time: 0.036 duration: 161.715
1: start_time: 0.026 duration: 161.691
stream: start_time: 0.289 duration: 1796.939 bitrate=5190 kb/s
2007-12-19 12:52:27.031 AFD: Opened codec 0x8895a0, id(MPEG2VIDEO) type(Video)
2007-12-19 12:52:27.031 AFD: Opened codec 0x91a140, id(MP2) type(Audio)
0: start_time: 0.036 duration: 161.715
1: start_time: 0.026 duration: 161.691
stream: start_time: 0.289 duration: 1796.939 bitrate=5190 kb/s
2007-12-19 12:52:27.560 AFD: Opened codec 0x8895a0, id(MPEG2VIDEO) type(Video)
2007-12-19 12:52:27.560 AFD: Opened codec 0x91a140, id(MP2) type(Audio)
0: start_time: 0.036 duration: 161.715
1: start_time: 0.026 duration: 161.691
stream: start_time: 0.289 duration: 1796.939 bitrate=5190 kb/s
2007-12-19 12:52:28.256 AFD: Opened codec 0x8895a0, id(MPEG2VIDEO) type(Video)
2007-12-19 12:52:28.256 AFD: Opened codec 0x91a140, id(MP2) type(Audio)

```

Suggestions?

---

### Post by Chris on 2008-01-03
Similar problem here.  If I watch a video using xine (which isn't using the PVR-350 MPEG decoder) then after that nothing will play back on the PVR-350.  Mythfrontend reports:

```
IVD Error: Writing to decoder
eno: Device or resource busy (16)
```

Trying to write directly to /dev/video16 gives a "busy" error from the I/O subsystem.  lsof reports nothing using /dev/video16.

So far the only solution I have found is to reboot.  If you Google for this error this post and another on this forum are the only references to this error so no help there.  :(

Has anyone asked this on the MythTV and/or IVTV mailing lists?

---

### Post by rllacey on 2008-01-23
I am a new user and am having the exact same problems using the PVR-350's TV out. Once I view an avi or anything that is not MPEG-2, I can't go back and watch TV or even watch previous recordings. I am getting the same errors as the above posts:

```

2008-01-23 20:28:53.869 NVP: Enabling Audio
2008-01-23 20:28:53.870 IVD: ivtv version 1.0.0
2008-01-23 20:28:53.888 DPMS Deactivated
2008-01-23 20:28:53.898 Using the PVR-350 decoder/TV-out
2008-01-23 20:28:54.066 Realtime priority would require SUID as root.
2008-01-23 20:28:54.068 IVD Error: Writing to decoder
                        eno: Device or resource busy (16)
2008-01-23 20:28:54.069 TV: Changing from None to WatchingPreRecorded
2008-01-23 20:28:54.192 TV: Attempting to change from WatchingPreRecorded to None
2008-01-23 20:28:54.263 TV: Changing from WatchingPreRecorded to None
2008-01-23 20:28:54.355 DPMS Reactivated.
0: start_time: 0.036 duration: 161.670
1: start_time: 0.026 duration: 161.648
stream: start_time: 0.289 duration: 1796.439 bitrate=5191 kb/s
2008-01-23 20:28:54.363 AFD: Opened codec 0x14fe7f0, id(MPEG2VIDEO) type(Video)
2008-01-23 20:28:54.363 AFD: Opened codec 0x2f229d0, id(MP2) type(Audio)
0: start_time: 0.036 duration: 161.670
1: start_time: 0.026 duration: 161.648
stream: start_time: 0.289 duration: 1796.439 bitrate=5191 kb/s
2008-01-23 20:28:54.906 AFD: Opened codec 0x14fe7f0, id(MPEG2VIDEO) type(Video)
2008-01-23 20:28:54.906 AFD: Opened codec 0x2f229d0, id(MP2) type(Audio)

```


Any help or insight would be greatly appreciated

---

### Post by therealbrewer on 2008-01-27
Exact same problem here. PVR-350 with X running over TV-out.. If I watch any avi, then I can't go back to live TV without a reboot. Can't find any further help.

Any ideas?

---

### Post by andrewb78 on 2008-02-02
I would file a bug on this if I had any idea on which project to file it.  Is there anyone actively working on the project who could provide some insight?

---

### Post by drilloe on 2008-02-14
Bumping this due to the same problem. It happens after I watch any movie in some player outside of mythtv.. vlc, mplayer, etc.

Did anyone find a fix?

from dmesg:

```

[   82.006423] ivtv0-fb: Unknown IOCTL 80104007
[   82.014318] ivtv0-fb: Unknown IOCTL 400c4003
[  118.589492] ivtv0: All encoder MPEG stream buffers are full. Dropping data.
[  118.589501] ivtv0: Cause: the application is not reading fast enough.
[  143.625439] ivtv0: All encoder MPEG stream buffers are full. Dropping data.
[  143.625448] ivtv0: Cause: the application is not reading fast enough.
[  266.805947] ivtv0-fb: Unknown IOCTL 80104007
[  266.811615] ivtv0-fb: Unknown IOCTL 400c4003
[  273.288947] ivtv0-fb: Unknown IOCTL 80104007
[  273.295270] ivtv0-fb: Unknown IOCTL 400c4003
[  306.766050] ivtv0-fb: Unknown IOCTL 80104007
[  306.773360] ivtv0-fb: Unknown IOCTL 400c4003
[  324.550152] ivtv0-fb: Unknown IOCTL 80104007
[  324.557024] ivtv0-fb: Unknown IOCTL 400c4003
[  362.409869] ivtv0-fb: Unknown IOCTL 80104007
[  362.415464] ivtv0-fb: Unknown IOCTL 400c4003
[  409.151508] ivtv0-fb: Unknown IOCTL 80104007
[  409.158114] ivtv0-fb: Unknown IOCTL 400c4003
[  450.062062] ivtv0-fb: Unknown IOCTL 80104007
[  450.068229] ivtv0-fb: Unknown IOCTL 400c4003

```

From /var/log/mythtv/mythfrontend.log:

```

2008-02-13 17:07:10.710 Using the PVR-350 decoder/TV-out
2008-02-13 17:07:11.216 TV: Changing from None to WatchingRecording
2008-02-13 17:07:11.220 Realtime priority would require SUID as root.
2008-02-13 17:07:11.223 IVD Error: Writing to decoder
                        eno: Device or resource busy (16)
2008-02-13 17:07:11.262 TV: Attempting to change from WatchingRecording to None
2008-02-13 17:07:11.347 TV: Changing from WatchingRecording to None

```

---

### Post by rllacey on 2008-02-16
> **andrewb78 said:**
> I would file a bug on this if I had any idea on which project to file it.  Is there anyone actively working on the project who could provide some insight?

This is for the Mythbuntu project. I apologize for sounding like a new kid here, but I would file a bug if I knew where to do so. 

In the meantime, it would be nice to be able to reboot your mythtv system from a menu command instead of having to bring up a terminal each time. Anyone ever done this?

---

### Post by andrewb78 on 2008-02-16
I went ahead and filed this against the mythbuntu project in Launchpad: [https://bugs.launchpad.net/mythbuntu/+bug/192538](https://bugs.launchpad.net/mythbuntu/+bug/192538).

---

### Post by mrand on 2008-09-16
Guys, is this still a problem (on either 8.04, or ideally, alpha 8.10)?

[INDENT]   Marc[/INDENT]

---

