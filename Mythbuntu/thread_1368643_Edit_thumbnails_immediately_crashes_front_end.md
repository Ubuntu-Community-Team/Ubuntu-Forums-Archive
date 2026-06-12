---
title: "Edit thumbnails immediately crashes front end"
date: 2009-12-30
forum: Mythbuntu
---

### Post by eljeffe on 2009-12-30
I've been working on mythbuntu for a couple of weeks now. I've got almost everything working but have one problem that has perplexed me.

I'm running the trunk testing version at the moment, but have had this problem with the "released" 0.22 and ever since.

Whenever I try to archive a file through the optical disks -> Create dvd menu, I cannot chose thumbnails. I get to the screen where I should be able to do this, hit 'i', see the screen for a split second and it crashes.

Below seems to be the relevant section of the front end log.

```
2009-12-30 19:24:32.580 Using the OpenGL painter
2009-12-30 19:24:32.869 Loaded base theme from /usr/share/mythtv/themes/MythCenter/base.xml
2009-12-30 19:24:32.872 Loaded base theme from /usr/share/mythtv/themes/default/base.xml
2009-12-30 19:24:32.872 Unable to load window 'backgroundwindow' from base
2009-12-30 19:24:32.875 Current MythTV Schema Version (DBSchemaVer): 1247
2009-12-30 19:24:32.882 New DB connection, total: 2
2009-12-30 19:24:32.882 Connected to database 'mythconverg' at host: localhost
2009-12-30 19:24:33.001 Desktop video mode: 2080x1024 59.9341 Hz
2009-12-30 19:24:34.500 Registering Internal as a media playback plugin.
2009-12-30 19:24:34.515 Registering WebBrowser as a media playback plugin.
2009-12-30 19:24:34.519 Plugin mythflix (0.23.20091112-1) binary version does not match libraries (0.23.20091229-1)
2009-12-30 19:24:34.520 Unable to initialize plugin 'mythflix'.
2009-12-30 19:24:34.537 MMUnix::AddDevice() Error: failed to stat /dev/bdi, 
			eno: No such file or directory (2)
2009-12-30 19:24:34.542 MMUnix::AddDevice() Error: failed to stat /dev/power, 
			eno: No such file or directory (2)
2009-12-30 19:24:34.545 MMUnix::AddDevice() Error: failed to stat /dev/trace, 
			eno: No such file or directory (2)
2009-12-30 19:24:34.550 MonitorRegisterExtensions(0x100, gif,jpg,png)
2009-12-30 19:24:34.566 Current MythMusic Schema Version (MusicDBSchemaVer): 1017
2009-12-30 19:24:34.588 MonitorRegisterExtensions(0x40, mp3,mp2,ogg,oga,flac,wma,wav,ac3,oma,omg,atp,ra,dts,aac,m4a,aa3,tta,mka,aiff,swa,wv)
2009-12-30 19:24:34.598 Current MythVideo Schema Version (mythvideo.DBSchemaVer): 1031
2009-12-30 19:24:34.615 Loading window theme from /usr/share/mythtv/themes/MythCenter/menu-ui.xml
2009-12-30 19:24:34.705 Loading menu theme from /usr/share/mythtv/themes/defaultmenu//mainmenu.xml
2009-12-30 19:24:34.708 Found mainmenu.xml for theme 'MythCenter'
2009-12-30 19:24:34.722 Using ARB NPOT texture extension
2009-12-30 19:24:34.764 MythContext: Connecting to backend server: 127.0.0.1:6543 (try 1 of 1)
2009-12-30 19:24:34.765 Using protocol version 56
2009-12-30 19:24:34.932 SendReceiveStringList(QUERY_TIME_ZONE) called from UI thread
2009-12-30 19:34:00.441 Loading menu theme from /usr/share/mythtv/themes/defaultmenu//optical_menu.xml
2009-12-30 19:34:03.334 Loading window theme from /usr/share/mythtv/themes/MythCenter/menu-ui.xml
2009-12-30 19:34:03.380 Loading menu theme from /usr/share/mythtv/archivemenu.xml
2009-12-30 19:34:05.119 Loading window theme from /usr/share/mythtv/themes/MythCenter/mytharchive-ui.xml
2009-12-30 19:34:05.120 Loading window theme from /usr/share/mythtv/themes/default/mytharchive-ui.xml
2009-12-30 19:34:05.137 Theme error: Unknown widget type
Type: 'context'
Name: ''
Line: 79
2009-12-30 19:34:10.730 Loading window theme from /usr/share/mythtv/themes/MythCenter/mythburn-ui.xml
2009-12-30 19:34:10.730 Loading window theme from /usr/share/mythtv/themes/default/mythburn-ui.xml
2009-12-30 19:34:13.993 Loading window theme from /usr/share/mythtv/themes/MythCenter/mythburn-ui.xml
2009-12-30 19:34:13.993 Loading window theme from /usr/share/mythtv/themes/default/mythburn-ui.xml
2009-12-30 19:34:14.011 MythArchive: Loading encoding profiles from /usr/share/mythtv/mytharchive/encoder_profiles/ffmpeg_dvd_ntsc.xml
2009-12-30 19:34:15.835 Loading window theme from /usr/share/mythtv/themes/MythCenter/mytharchive-ui.xml
2009-12-30 19:34:15.835 Loading window theme from /usr/share/mythtv/themes/default/mytharchive-ui.xml
loading file from: /usr/share/mythtv/mytharchive/themes/Black/theme.xml
chapterNodeList.count(): 0
chapterNodeList.size(): 0
2009-12-30 19:34:36.506 Loading window theme from /usr/share/mythtv/themes/MythCenter/mythburn-ui.xml
2009-12-30 19:34:36.506 Loading window theme from /usr/share/mythtv/themes/default/mythburn-ui.xml
2009-12-30 19:34:36.524 Unable to find image file: mv_browse_nocover.png
2009-12-30 19:34:36.526 Unable to find image file: mv_browse_nocover.png
2009-12-30 19:34:36.527 Unable to find image file: mv_browse_nocover.png
2009-12-30 19:34:36.877 ProgramInfo: Updated pathname '':'' -> '7013_20091230193000.nuv'
Input #0, nuv, from '/spare/mythtv/recordings/7013_20091230193000.nuv':
  Duration: 00:11:52.41, start: 0.057000, bitrate: 1411 kb/s
    Stream #0.0: Video: mpeg4, yuv420p, 720x480, PAR 8:9 DAR 4:3, 30 tbr, 1k tbn, 1k tbc
    Stream #0.1: Audio: mp3, 48000 Hz, 2 channels, s16, 1411 kb/s
[swscaler @ 0x2ea2380]No accelerated colorspace conversion found.

``` 

I'm not sure where to proceed. I've been searching as many forums as I could find and I seem to be unique in having this problem.

Any Ideas and what I should investigate?

Thanks

---

### Post by azmyth on 2009-12-31
In Settings -> Media Settings -> Archive Settings (1st screen)

I'd check the temp directory listed to make sure you have permissions set so the temp work like frame changes can occur.

Under this directory, I have three subs.

config  logs  work

---

### Post by eljeffe on 2009-12-31
Thanks for your reply.

I found they were set to the username running the front end, rather than mythtv.

I changed them to:

drwxrwxr x 3 mythtv mythtv 4096 2009-12-30 19:47 config
drwxrwxr x 2 mythtv mythtv 4096 2009-12-30 22:53 logs
drwxrwxr x 7 mythtv mythtv 4096 2009-12-30 19:24 work

It still doesn't work. I don't know if it's related, but in looking closer at the log, it appears that a half hour recording shows

```
2009-12-31 15:04:57.562 ProgramInfo: Updated pathname '':'' -> '7007_20091230203000.nuv'
Input #0, nuv, from '/spare/mythtv/recordings/7007_20091230203000.nuv':
  **Duration: 01:17:01.40**, start: 0.062000, bitrate: 1411 kb/s
    Stream #0.0: Video: mpeg4, yuv420p, 720x480, PAR 8:9 DAR 4:3, 29.92 tbr, 1k tbn, 1k tbc
    Stream #0.1: Audio: mp3, 48000 Hz, 2 channels, s16, 1411 kb/s
[swscaler @ 0x7f9458f6a270]No accelerated colorspace conversion found.
```

---

### Post by azmyth on 2010-01-01
I have a second tuner that creates a nuv file. I just tried the same thing and it gave me a floating point exception. Mine also said the nuv file was 1TB. No problems with the mpg from the PVR150.

---

### Post by eljeffe on 2010-01-02
So it sounds like the files themselves could be the issue.     Hmm. 

I'm using a v4linux driver on a BT848 card.

When I get the chance I'll see if I can do it on a straight mpg file from a DVD rip or something that wasn't generated by the card. 

Thanks

---

### Post by eljeffe on 2010-01-02
I got a little farther, but still not working. I tried it with an mpg that I ripped from a DVD and an AVI. Both got to the screen from which I should have been able to seek for a frame. When I tried to move through the video, that was when it crashed this time.

from an mpg:

```
chapterNodeList.count(): 0
chapterNodeList.size(): 0
2010-01-02 15:15:41.095 Loading window theme from /usr/share/mythtv/themes/MythCenter/mythburn-ui.xml
2010-01-02 15:15:41.095 Loading window theme from /usr/share/mythtv/themes/default/mythburn-ui.xml
2010-01-02 15:15:41.210 Unable to find image file: mv_browse_nocover.png
2010-01-02 15:15:41.210 Unable to find image file: mv_browse_nocover.png
2010-01-02 15:15:41.220 Unable to find image file: mv_browse_nocover.png
2010-01-02 15:15:41.705 ThumbFinder: Failed to get start time
ASSERT failure in QList<T>::at: "index out of range", file /usr/include/qt4/QtCore/qlist.h, line 395
```

from an avi:

```
chapterNodeList.count(): 0
chapterNodeList.size(): 0
2010-01-02 15:21:23.448 Loading window theme from /usr/share/mythtv/themes/MythCenter/mythburn-ui.xml
2010-01-02 15:21:23.448 Loading window theme from /usr/share/mythtv/themes/default/mythburn-ui.xml
2010-01-02 15:21:23.516 Unable to find image file: mv_browse_nocover.png
2010-01-02 15:21:23.516 Unable to find image file: mv_browse_nocover.png
2010-01-02 15:21:23.517 Unable to find image file: mv_browse_nocover.png
Input #0, avi, from '/home/jeff/Videos/The Tim Conway Show/Tim Conway Show 01x02 The Mail Contract.avi':
  Duration: 00:25:41.95, start: 0.000000, bitrate: 948 kb/s
    Stream #0.0: Video: mpeg4, yuv420p, 416x320 [PAR 1:1 DAR 13:10], 29.97 tbr, 29.97 tbn, 29.98 tbc
    Stream #0.1: Audio: mp3, 48000 Hz, 2 channels, s16, 120 kb/s
2010-01-02 15:21:23.907 ThumbFinder: Failed to get start time
```

Not sure where the issue is now.

---

### Post by azmyth on 2010-01-02
I just tried this and it crashed. I think the problem has to do with no seek table on a video whereas a TV recording has one. You could try building one for the avi or mpeg video.

[http://www.mythtv.org/wiki/MythVideo#Rebuild_seek_table](http://www.mythtv.org/wiki/MythVideo#Rebuild_seek_table)

As for the nuv, it's a special file and I think it's decoded on playback thus when mytharch tries to find a frame there isn't one. This is just a guess though.

---

### Post by eljeffe on 2010-01-03
Hmm. I tried this with AVI, OGG, and MPEG files. 

The good news is that it worked with the MPEG, but the AVI and OGG still blew chunks. 

I had already tried this with recordings in nuv, but that never worked. Mostly I wanted to use this feature to archive recordings, but apparently there is something about the files that get transcoded from my recording source that cause problems. 

Does the input you use that doesn't work use the v4l drivers?

---

