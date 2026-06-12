---
title: "Video frame buffering failed too many times mythvideo dvd playback"
date: 2010-06-15
forum: Mythbuntu
---

### Post by Erkander on 2010-06-15
Just installed 10.04 on a fresh system that had been using Knoppmyth.  On some of my ripped DVD's I'm getting a pause then a "Video frame buffering failed too many times" error.  I'm using the internal player and it's on a SATA drive if that helps at all.

Also while ISO's worked on Knoppmyth, they lock the system up with Mythbuntu.  While that's annoying, I can work around that, but the above error is a game killer so far.  I LOVE Mythbuntu and don't want to go back to Knoppmyth, specially since I've spent a whole day on the install so far.

I've looked around and have seen that there may be some patches to fix this either forth-coming or out already, but I haven't been able to find the exact whereabouts of the files.  While I'm familiar with Linux, I'm still pretty green, so I need details please.  Any ideas?

Thanks in advance,
Erkander

---

### Post by larsolav on 2010-06-15
Have you Activated Auto Builds? See: 
[http://www.mythbuntu.org/auto-builds](http://www.mythbuntu.org/auto-builds)
That should update your system including fixing bugs etc.

---

### Post by Erkander on 2010-06-15
Thanks!  I'll try that tonight!

--Erkander

---

### Post by Erkander on 2010-06-15
Got auto-builds updated, but the synaptic manager shows everything to be of the newest version.

This problem is worse than I thought.  The few movies that it WILL play give the same error if you skip forward at all.

HELP!

--Erkander

HUH.  Just saw the error logs.  I'm getting a Failed to create VDPAU device error, a WriteAudio: buffer underrun error AND a "No DTS Seeking Hack!" 

?!?!

---

### Post by Erkander on 2010-06-16
Whoops.  I missed a step.  You have to hit refresh and then mark updates on the synaptic manager for it to really update.  NEWB!

Everything works now.  Thanks folks!!!  Even the ISO's!  w00t!

--Erkander

---

### Post by SMANN on 2010-06-19
I had this issue.  "Video frame buffering failed..." w/ both .iso's and physical disks.  I enabled auto-build to the .23+fixes.  Now the dvd's, both .iso and physical, will play but at what seems to be 2x speed for both audio and video.  Behavior is identical on 2 different boxes and with multiple .iso and physical disks.  Didn't experience this issue on 8.04 with the same hardware.

Any suggestions?

Here is mythfrontend.log for trying to play an .iso

```

2010-06-19 22:32:46.870 MythVideo::ScanVideoDirectory Scanning (/storage3)
2010-06-19 22:33:16.637 TV: Attempting to change from None to WatchingDVD
libdvdread: Using libdvdcss version 1.2.10 for DVD access

libdvdread: Attempting to retrieve all CSS keys
libdvdread: This can take a _long_ time, please be patient

libdvdread: Get key for /VIDEO_TS/VIDEO_TS.VOB at 0x00000132
libdvdread: Elapsed time 1
libdvdread: Get key for /VIDEO_TS/VTS_01_0.VOB at 0x00017f48
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_1.VOB at 0x000180ae
libdvdread: Elapsed time 1
libdvdread: Get key for /VIDEO_TS/VTS_02_1.VOB at 0x00257c28
libdvdread: Elapsed time 0
libdvdread: Found 2 VTS's
libdvdread: Elapsed time 2
libdvdnav: Using dvdnav version svnR1169
libdvdnav: DVD Title: JAZZICONS2_WES_MONTGOMERY
libdvdnav: DVD Serial Number: 36fa746c
libdvdnav: DVD Title (Alternative):
libdvdnav: Unable to find map file '/home/d/.dvdnav/JAZZICONS2_WES_MONTGOMERY.map'
libdvdnav: DVD disk reports itself with Region mask 0x00000000. Regions: 1 2 3 4 5 6 7 8
2010-06-19 22:33:18.842 Opened DVD device at /storage3/Music Videos/jazzicons2_wes_montgomery.iso
2010-06-19 22:33:18.852 There are 2 titles on the disk
2010-06-19 22:33:18.852 Title 0 has 0 parts.
2010-06-19 22:33:18.852 Title 1 has 16 parts.
2010-06-19 22:33:19.019 AFD: Opened codec 0x41c75e0, id(MPEG2VIDEO) type(Video)
2010-06-19 22:33:19.020 NVP(3): Disabling Audio, params(-1,-1,-1)
2010-06-19 22:33:19.044 VideoOutputXv: XVideo Adaptor Name: 'NV17 Video Texture'
2010-06-19 22:33:19.097 OSD Theme Dimensions W: 640 H: 480
2010-06-19 22:33:19.209 TV: Changing from None to WatchingDVD
2010-06-19 22:33:19.211 OpenGLVideoSync()
2010-06-19 22:33:19.253 Video timing method: SGI OpenGL
2010-06-19 22:33:35.352 AFD: Warning, video codec 0x41c75e0 id(MPEG2VIDEO) type (Video) already open.
2010-06-19 22:33:35.388 AFD: codec AC3 has 0 channels
2010-06-19 22:33:35.388 AFD: Opened codec 0x7f219ca139a0, id(AC3) type(Audio)
2010-06-19 22:33:35.433 Opening audio device 'default'. ch 2(2) sr 48000 (reenc 0)
2010-06-19 22:33:35.433 Opening ALSA audio device 'default'.
2010-06-19 22:33:35.474 Mixer unable to find control Master 1
2010-06-19 22:33:35.474 mixer unable to find control Master 1
2010-06-19 22:33:35.474 Mixer unable to find control Master 1
2010-06-19 22:33:35.474 mixer unable to find control Master 1
2010-06-19 22:33:35.474 NVP(3): Enabling Audio
2010-06-19 22:33:55.767 AFD: Warning, video codec 0x41c75e0 id(MPEG2VIDEO) type (Video) already open.
2010-06-19 22:33:55.767 AFD: Opened codec 0x7f21945a96f0, id(DVD_SUBTITLE) type(Subtitle)
2010-06-19 22:33:55.767 NVP(3): Disabling Audio, params(-1,-1,-1)
2010-06-19 22:33:55.869 [mpeg2video @ 0x7f21b69e0380]ac-tex damaged at 18 1
2010-06-19 22:33:55.869 [mpeg2video @ 0x7f21b69e0380]Warning MVs not available
2010-06-19 22:33:55.896 [mpeg2video @ 0x7f21b69e0380]ac-tex damaged at 18 1
2010-06-19 22:33:55.896 [mpeg2video @ 0x7f21b69e0380]Warning MVs not available
2010-06-19 22:33:55.943 AFD: Warning, video codec 0x41c75e0 id(MPEG2VIDEO) type (Video) already open.
2010-06-19 22:33:55.979 AFD: codec PCM_DVD has 0 channels
2010-06-19 22:33:55.979 AFD: Opened codec 0x7f21947b9430, id(PCM_DVD) type(Audio)
2010-06-19 22:33:56.023 Opening audio device 'default'. ch 2(2) sr 48000 (reenc 0)
2010-06-19 22:33:56.023 Opening ALSA audio device 'default'.
2010-06-19 22:33:56.064 Mixer unable to find control Master 1
2010-06-19 22:33:56.064 mixer unable to find control Master 1
2010-06-19 22:33:56.064 Mixer unable to find control Master 1
2010-06-19 22:33:56.064 mixer unable to find control Master 1
2010-06-19 22:33:56.064 NVP(3): Enabling Audio
2010-06-19 22:33:56.396 WriteAudio: buffer underrun
2010-06-19 22:34:08.383 Marking recording as watched using offset 4 minutes
2010-06-19 22:34:08.510 TV: Attempting to change from WatchingDVD to None
2010-06-19 22:34:08.510 TV: Changing from WatchingDVD to None
2010-06-19 22:34:08.523 ~OpenGLVideoSync() -- closing opengl vsync
```

---

