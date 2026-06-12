---
title: "MythFronent Issues"
date: 2008-04-29
forum: Mythbuntu
---

### Post by tcpankon on 2008-04-29
Having an issue playing recordings on multiple remote frontends.

Upgraded Mythbuntu backend/frontend from 7.10 to 8.04.  Other two frontends are both fresh kubuntu 8.04 installs with necessary myth packages installed.  Backend/Frontend is able to play all of the recordings fine.  

When I try to play recordings on the frontends, a couple work fine, yet most will load a black screen for 5-10 seconds then exit back to screen to select recordings.  On the frontend, doing a tail -f /var/log/mythtv/mythfrontend.log shows the following:

```




2008-04-29 12:54:50.846 TV: Attempting to change from None to WatchingPreRecorded
2008-04-29 12:54:50.948 DPMS Deactivated
2008-04-29 12:54:50.961 AFD: Opened codec 0x865f2a0, id(MPEG2VIDEO) type(Video)
2008-04-29 12:54:50.961 AFD: codec MP2 has 2 channels
2008-04-29 12:54:50.962 AFD: Opened codec 0x8658610, id(MP2) type(Audio)
2008-04-29 12:54:51.408 AFD: Opened codec 0x8610e30, id(MPEG2VIDEO) type(Video)
2008-04-29 12:54:51.408 AFD: codec MP2 has 2 channels
2008-04-29 12:54:51.408 AFD: Opened codec 0x8653320, id(MP2) type(Audio)
2008-04-29 12:54:51.410 Opening audio device 'default'. ch 2(2) sr 48000
2008-04-29 12:54:51.410 Opening ALSA audio device 'default'.
ALSA lib control.c:909:(snd_ctl_open_noupdate) Invalid CTL /dev/mixer
2008-04-29 12:54:51.412 AudioOutput Warning: Mixer attach error -2: No such file or directory
                        Check Mixer Name in Setup: '/dev/mixer'
2008-04-29 12:54:51.782 VideoOutputXv: XVideo Adaptor Name: 'NV17 Video Texture'
2008-04-29 12:54:51.886 OSD Theme Dimensions W: 640 H: 480
2008-04-29 12:54:52.615 Realtime priority would require SUID as root.
2008-04-29 12:54:52.616 TV: Changing from None to WatchingPreRecorded
2008-04-29 12:54:52.724 Video timing method: USleep with busy wait

```

ABOVE IS PLAYING A WORKING VIDEO

```

2008-04-29 12:54:57.214 TV: Attempting to change from WatchingPreRecorded to None
2008-04-29 12:54:57.282 TV: Changing from WatchingPreRecorded to None
2008-04-29 12:54:57.460 DPMS Reactivated.
2008-04-29 12:54:58.062 AFD: Opened codec 0x865f2a0, id(MPEG2VIDEO) type(Video)
2008-04-29 12:54:58.062 AFD: codec MP2 has 2 channels
2008-04-29 12:54:58.062 AFD: Opened codec 0x8658610, id(MP2) type(Audio)
2008-04-29 12:54:58.809 AFD: Opened codec 0x865f2a0, id(MPEG2VIDEO) type(Video)
2008-04-29 12:54:58.810 AFD: codec MP2 has 2 channels
2008-04-29 12:54:58.810 AFD: Opened codec 0x8658610, id(MP2) type(Audio)
2008-04-29 12:54:59.918 AFD: Opened codec 0x865f2a0, id(MPEG2VIDEO) type(Video)
2008-04-29 12:54:59.918 AFD: codec MP2 has 2 channels
2008-04-29 12:54:59.918 AFD: Opened codec 0x8658610, id(MP2) type(Audio)
2008-04-29 12:55:00.869 AFD: Opened codec 0x865f2a0, id(MPEG2VIDEO) type(Video)
2008-04-29 12:55:00.870 AFD: codec MP2 has 2 channels
2008-04-29 12:55:00.870 AFD: Opened codec 0x8658610, id(MP2) type(Audio)

```

ABOVE IS STOPPING THE PLAYBACK OF WORKING VIDEO

```

2008-04-29 12:55:04.609 GetRecordBasename found no entry
2008-04-29 12:55:04.621 TV: Attempting to change from None to WatchingPreRecorded
2008-04-29 12:55:04.624 GetRecordBasename found no entry
2008-04-29 12:55:04.659 GetRecordBasename found no entry
2008-04-29 12:55:04.737 DPMS Deactivated
2008-04-29 12:55:04.863 NVP::OpenFile(): Error, couldn't read file: myth://192.168.10.3:6543/
2008-04-29 12:55:04.864 TV Error: StartPlayer(): NVP is not playing after 20000 msec
2008-04-29 12:55:04.864 TV: Changing from None to WatchingPreRecorded
2008-04-29 12:55:04.865 TV: Attempting to change from WatchingPreRecorded to None
2008-04-29 12:55:04.919 TV: Changing from WatchingPreRecorded to None
2008-04-29 12:55:05.097 DPMS Reactivated.
2008-04-29 12:55:05.133 AFD: Opened codec 0x865f2a0, id(MPEG2VIDEO) type(Video)
2008-04-29 12:55:05.133 AFD: codec MP2 has 2 channels
2008-04-29 12:55:05.133 AFD: Opened codec 0x8658610, id(MP2) type(Audio)
2008-04-29 12:55:06.181 AFD: Opened codec 0x865f2a0, id(MPEG2VIDEO) type(Video)
2008-04-29 12:55:06.181 AFD: codec MP2 has 2 channels
2008-04-29 12:55:06.182 AFD: Opened codec 0x8658610, id(MP2) type(Audio)
2008-04-29 12:55:07.326 AFD: Opened codec 0x865f2a0, id(MPEG2VIDEO) type(Video)
2008-04-29 12:55:07.326 AFD: codec MP2 has 2 channels
2008-04-29 12:55:07.326 AFD: Opened codec 0x8658610, id(MP2) type(Audio)
2008-04-29 12:55:20.914 AFD: Opened codec 0x865f2a0, id(MPEG2VIDEO) type(Video)
2008-04-29 12:55:20.914 AFD: codec MP2 has 2 channels
2008-04-29 12:55:20.914 AFD: Opened codec 0x8658610, id(MP2) type(Audio)
```

ABOVE IS WATCHING RECORDING THAT FALLS BACK TO SELECTION SCREEN

If all else fails, I will probably be doing a fresh install on the backend, but hopefully someone can give me some tips as to where to look.

Thanks

---

### Post by gr8nash on 2008-04-29
I also have the exact same problem.. all my frontends cant play video in stream mode...or just using the default..local file playback with streaming fallback.

i get this:

2008-04-29 19:15:36.432 TV: Attempting to change from None to WatchingRecording
2008-04-29 19:15:36.433 GetRecordBasename found no entry
2008-04-29 19:15:42.937 RingBuf(/tv/): Invalid file (fd -1) when opening '/tv/'.
2008-04-29 19:15:44.010 RingBuf(/tv/): Invalid file (fd -1) when opening '/tv/'.

Im sharing over NFS from the backend...and can play the recordings just fine with VLC over NFS... its just myth thats having the problem... also Live TV works through mythTV..and so does the preview video in the recording screen... VERY frustrating..day 4 of the problem. =(

---

### Post by gr8nash on 2008-04-30
Bump... anyone seen this issue..it kicking my butt.. i have been into mythtv since .12 and suddenly im feeling like a newb.  I cant seem to get any of my frontends to play recordings....but the preview window works fine. and live TV works fine

---

### Post by tcpankon on 2008-05-01
Last night I just did a fresh install of Kubuntu and added the backend/frontend features.  I will post an update either way if this fixed the problem.

---

### Post by gr8nash on 2008-05-03
soooooo how did it go? :popcorn:  Im still messed..im about to give up and hope a reinstall fixes it

---

### Post by bodyjarrocks on 2008-05-06
I'm having this issue too.  It is also being tracked on the MythTV-users mailing list (posted by me):
[http://www.gossamer-threads.com/lists/mythtv/users/333216#333216](http://www.gossamer-threads.com/lists/mythtv/users/333216#333216)

Anyone figure it out?

Mike

---

### Post by tcpankon on 2008-05-07
After doing a fresh install, the frontends appear to be working as expected...now I'm having a new issue where my backend seems to be hardlocking at least once a day.  not sure if it's a RAM issue or what as I haven't had a lot of time to dedicate to testing.  An overnight memtest didn't show any errors so I guess it could be a number of things.

So to answer the original question, a reinstall seemed to fix the issue I had when I upgraded from 7.04 to 8.10

---

### Post by Unibrav on 2008-05-23
I had the same problem. I fixed it by setting the time on both frontend and backend to the same time. My frontend was UTC and my backend was Central when it was happening. Changing my frontend to Central and setting the clock via NTP fixed everything.

I hope that helps.

---

### Post by bturig on 2008-09-26
My fix is to set frontend timezone to the same as backend

sudo dpkg-reconfigure tzdata

---

### Post by kdog_1914 on 2008-11-03
> **bturig said:**
> My fix is to set frontend timezone to the same as backend

sudo dpkg-reconfigure tzdata

Eureka...  Time zone set to whatever popped up as I was using a desktop install without a mouse...

Thank you!!!  I would have reinstalled had I not found your post.

---

### Post by Wes Baker on 2010-09-29
Hey Guys,


Just wanted to add that I had very similar symptoms to this, but it was a different cause so here's something else you can try if the above doesn't work, and you have this problem, but it only affects a slave backend.

Check the database tab of the general settings page in the setup section of mythfrontend.

Make sure the settings are the same in each frontend, and they match the master mysql details.

This was caused in my case because I did two standalone installs, and then connected them later, but all i only changed the backend setup on the new slave machine.  So, now I know that you need to changed the frontend setup too!

---

