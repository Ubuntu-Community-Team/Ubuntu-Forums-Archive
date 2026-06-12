---
title: "Fast Forward not working after upgrade from 7.10 -&gt; 8.04.1"
date: 2008-07-22
forum: Mythbuntu
---

### Post by philpem on 2008-07-22
**Solution found: see my post later in this thread.**

Hi,
I've just upgraded my MythTV box from Mythbuntu 7.10 to 8.04. Since upgrading if I attempt to fast-forward pre-recorded video at more than 3x speed, MythTV hangs for a few seconds then drops back to the previous OSD page.

I found these messages in mythfrontend.log:
```
2008-07-22 23:46:16.886 New DB connection, total: 3
2008-07-22 23:46:16.886 Realtime priority would require SUID as root.
2008-07-22 23:46:16.886 Connected to database 'mythconverg' at host: localhost
2008-07-22 23:46:16.984 Video timing method: RTC
Initialize Yadif Deinterlacer. In-Pixformat = 1 Out-Pixformat=1
yadifdeint: size changed from 0 x 0 -> 544 x 576
2008-07-22 23:46:22.146 NVP: prebuffering pause
2008-07-22 23:46:22.148 WriteAudio: buffer underrun
2008-07-22 23:46:22.677 NVP: Prebuffer wait timed out 10 times.
2008-07-22 23:46:23.207 NVP: Prebuffer wait timed out 10 times.
2008-07-22 23:46:23.737 NVP: Prebuffer wait timed out 10 times.
2008-07-22 23:46:24.268 NVP: Prebuffer wait timed out 10 times.
2008-07-22 23:46:24.799 NVP: Prebuffer wait timed out 10 times.
2008-07-22 23:46:25.330 NVP: Prebuffer wait timed out 10 times.
2008-07-22 23:46:25.860 NVP: Prebuffer wait timed out 10 times.
2008-07-22 23:46:26.390 NVP: Prebuffer wait timed out 10 times.
2008-07-22 23:46:26.921 NVP: Prebuffer wait timed out 10 times.
2008-07-22 23:46:27.451 NVP: Prebuffer wait timed out 10 times.
2008-07-22 23:46:27.982 NVP: Prebuffer wait timed out 10 times.
2008-07-22 23:46:28.512 NVP: Prebuffer wait timed out 10 times.
2008-07-22 23:46:29.042 NVP: Prebuffer wait timed out 10 times.
2008-07-22 23:46:29.573 NVP: Prebuffer wait timed out 10 times.
2008-07-22 23:46:30.103 NVP: Prebuffer wait timed out 10 times.
2008-07-22 23:46:30.634 NVP: Prebuffer wait timed out 10 times.
2008-07-22 23:46:31.164 NVP: Prebuffer wait timed out 10 times.
2008-07-22 23:46:31.694 NVP: Prebuffer wait timed out 10 times.
2008-07-22 23:46:32.227 NVP: Prebuffer wait timed out 10 times.
2008-07-22 23:46:32.758 NVP: Prebuffer wait timed out 10 times.
2008-07-22 23:46:33.288 NVP: Prebuffer wait timed out 10 times.
2008-07-22 23:46:33.818 NVP: Prebuffer wait timed out 10 times.
2008-07-22 23:46:34.349 NVP: Prebuffer wait timed out 10 times.
2008-07-22 23:46:34.879 NVP: Prebuffer wait timed out 10 times.
2008-07-22 23:46:35.409 NVP: Prebuffer wait timed out 10 times.
2008-07-22 23:46:35.939 NVP: Prebuffer wait timed out 10 times.
2008-07-22 23:46:36.470 NVP: Prebuffer wait timed out 10 times.
2008-07-22 23:46:37.000 NVP: Prebuffer wait timed out 10 times.
2008-07-22 23:46:37.530 NVP: Prebuffer wait timed out 10 times.
2008-07-22 23:46:38.061 NVP: Prebuffer wait timed out 10 times.
2008-07-22 23:46:38.591 NVP: Prebuffer wait timed out 10 times.
2008-07-22 23:46:39.121 NVP: Prebuffer wait timed out 10 times.
2008-07-22 23:46:39.652 NVP: Prebuffer wait timed out 10 times.
2008-07-22 23:46:40.182 NVP: Prebuffer wait timed out 10 times.
2008-07-22 23:46:40.712 NVP: Prebuffer wait timed out 10 times.
2008-07-22 23:46:41.224 AFD Error: av_seek_frame(ic, -1, 7160000, 0) -- error
2008-07-22 23:46:41.243 NVP: Prebuffer wait timed out 10 times.
2008-07-22 23:46:45.437 AFD Error: av_seek_frame(ic, -1, 9400000, 0) -- error
2008-07-22 23:46:48.923 NVP: Prebuffer wait timed out 10 times.
2008-07-22 23:46:50.108 AFD Error: av_seek_frame(ic, -1, 8280000, 0) -- error
2008-07-22 23:46:50.507 TV: Attempting to change from WatchingPreRecorded to None
2008-07-22 23:46:50.541 TV: Changing from WatchingPreRecorded to None
2008-07-22 23:46:50.706 DPMS Reactivated.

```

What's going on? This worked fine before I upgraded...

Thanks,
Phil.

---

### Post by philpem on 2008-07-24
How bloomin' predictable.

Wiped out 7.10, reinstalled Mb 8.04LTS from clean. Including losing most of my video collection due to misreading a very non-obvious popup in the installer (MB dev'rs -- make the installer say that it's going to nuke /var/lib/mythtv/* before it does so, please).

It still doesn't work.

FF/REW still break with the NVP errors mentioned above. DVD playback is totally shot to hell.

No such problems with VideoLAN or Mplayer.

As I said before, this is a base install, all I've added is build-essential, madwifi CVS and the dev.kewl.org branch of v4l-dvb (for hauppauge hvr3000 multifrontend support).

Any ideas folks?

---

### Post by Lindsay.Mathieson on 2008-07-25
Are you using a remote to test this or direct via the keyboard?

Just wondering if your remote/lirc is the problem

---

### Post by philpem on 2008-07-25
> **Lindsay.Mathieson said:**
> Are you using a remote to test this or direct via the keyboard?

Just wondering if your remote/lirc is the problem

The remote is the Hauppauge "silver surfboard" fed to a Nova-T-500. I used irrecord to build the remote control spec file.

I've tested with and without lircd running -- the same thing happens in both cases. Video freezes, then a few seconds later Mythfrontend drops back to the menu (or in some cases crashes entirely).

Thanks,
Phil.

---

### Post by Archmage on 2008-07-25
Are you using the restricted drivers? I know that Hardy have some difficults getting the restriced drivers.

---

### Post by philpem on 2008-07-25
> **Archmage said:**
> Are you using the restricted drivers? I know that Hardy have some difficults getting the restriced drivers.

I'm using two "restricted" drivers -- the nVidia graphics driver and Madwifi. Madwifi is compiled from the "new HAL" source (new HAL is required for the AirPace PCIe wifi card, which is still not supported by madwifi stable). The nV drivers came from the Ubuntu repo.

It's been doing this on the base install, and on the same install after an 'apt-get upgrade'. If it is the nV drivers, the ones on the CD-R are no better.

---

### Post by thespirit3 on 2008-07-25
Similar problem here - although it only happens on some recorded shows.

2008-07-25 20:01:00.397 VideoOutputXv: XVideo Adaptor Name: 'NV17 Video Texture'
2008-07-25 20:01:00.451 OSD Theme Dimensions W: 640 H: 480
2008-07-25 20:01:00.724 TV: Changing from None to WatchingPreRecorded
2008-07-25 20:01:00.727 Realtime priority would require SUID as root.
2008-07-25 20:01:00.824 OpenGLVideoSync()
2008-07-25 20:01:00.852 Video timing method: SGI OpenGL
2008-07-25 20:01:03.247 NVP: prebuffering pause
2008-07-25 20:01:03.891 NVP: Prebuffer wait timed out 10 times.
2008-07-25 20:01:04.558 NVP: Prebuffer wait timed out 10 times.
2008-07-25 20:01:05.224 NVP: Prebuffer wait timed out 10 times.
2008-07-25 20:01:05.905 NVP: Prebuffer wait timed out 10 times.
2008-07-25 20:01:06.571 NVP: Prebuffer wait timed out 10 times.
2008-07-25 20:01:07.238 NVP: Prebuffer wait timed out 10 times.
2008-07-25 20:01:07.957 NVP: Prebuffer wait timed out 10 times.
2008-07-25 20:01:08.625 NVP: Prebuffer wait timed out 10 times.
2008-07-25 20:01:09.291 NVP: Prebuffer wait timed out 10 times.
2008-07-25 20:01:09.958 NVP: Prebuffer wait timed out 10 times.
2008-07-25 20:01:10.625 NVP: Prebuffer wait timed out 10 times.
2008-07-25 20:01:11.291 NVP: Prebuffer wait timed out 10 times.
2008-07-25 20:01:12.051 NVP: Prebuffer wait timed out 10 times.
2008-07-25 20:01:12.717 NVP: Prebuffer wait timed out 10 times.
2008-07-25 20:01:13.384 NVP: Prebuffer wait timed out 10 times.
2008-07-25 20:01:14.051 NVP: Prebuffer wait timed out 10 times.
2008-07-25 20:01:14.717 NVP: Prebuffer wait timed out 10 times.
2008-07-25 20:01:15.384 NVP: Prebuffer wait timed out 10 times.
2008-07-25 20:01:16.050 NVP: Prebuffer wait timed out 10 times.

and so on.

Actually, we *can* FF at 3x speed, but then often when hitting play it'll freeze before timing out and going back to the menu.

---

### Post by philpem on 2008-07-31
Run these commands:
$ sudo apt-get update
$ sudo apt-get upgrade

My PVR just took an update and fast forward works again. Full list of updated packages follows:

procps
ufw
libavutil1d
libavcodec1d
libavformat1d
libswscale1d
ffmpeg
libglib
xulrunner
firefox-3.0
firefox
gtk2-engines
libhal1
libsmbios1
hal
libpostproc1d
libwnck-common

I suspect ffmpeg might have something to do with it, or maybe libavcodec. Does anyone want to check the changelogs?

---

### Post by korgman on 2009-01-25
I was having the exact same problem.  Did an update, FFWD is working fine now.

---

