---
title: "EPG hangs mythbuntu"
date: 2008-08-09
forum: Mythbuntu
---

### Post by sadale_1270 on 2008-08-09
I just did an upgrade to from 7.04 to 8.04. Everything works just fine, the remote, etc., everything.  Except that when I go into the program guide in live tv (only in live tv) the guide locks up completely for about 10 minutes.  No response from the remote, no nothing.  The live tv window continues to play correctly, but the rest of the system is shot.  The lockup repeates if I move up or down in the guide.  If I hit exit, eventually it will exit.

I went into the ocnifguration and turned the EPG to the low CPU setting, no change.


Thoughts?

TIA
Steve

---

### Post by volkswagner on 2008-08-09
Any relevant info in the logs?

What video and drivers are you using?

---

### Post by sadale_1270 on 2008-08-10
The card is an Nvidia 7300GT using the most recent version of the Nvidia drivers.  I don't remember specifically which they are, but they are the most recent ones you can install directly through ubuntu...

Here is my frontend log for today:

2008-08-09 09:57:50.525 TV: Changing from None to WatchingLiveTV
2008-08-09 09:57:50.531 Realtime priority would require SUID as root.
2008-08-09 09:57:50.629 Video timing method: USleep with busy wait
2008-08-09 09:57:53.603 XMLParse::LoadTheme using /usr/share/mythtv/themes/Mythbuntu-8.04/ui.xml
2008-08-09 09:59:23.965 NVP: prebuffering pause
2008-08-09 09:59:28.380 WriteAudio: buffer underrun
2008-08-09 09:59:28.398 NVP: prebuffering pause
2008-08-09 11:00:04.293 New DB connection, total: 4
2008-08-09 11:00:04.445 Connected to database 'mythconverg' at host: localhost
2008-08-09 11:00:05.177 NVP: prebuffering pause
2008-08-09 11:00:06.511 NVP: Prebuffer wait timed out 10 times.
2008-08-09 12:28:16.170 NVP: prebuffering pause
2008-08-09 12:28:16.238 WriteAudio: buffer underrun
2008-08-09 12:28:17.889 NVP: Prebuffer wait timed out 10 times.
2008-08-09 12:28:19.444 NVP: Prebuffer wait timed out 10 times.
2008-08-09 12:35:23.691 NVP: prebuffering pause
2008-08-09 12:39:24.727 NVP: prebuffering pause
2008-08-09 12:39:27.618 WriteAudio: buffer underrun
2008-08-09 12:58:58.725 XMLParse::LoadTheme using /usr/share/mythtv/themes/Mythbuntu-8.04/ui.xml
2008-08-09 12:59:01.686 NVP: prebuffering pause
2008-08-09 13:05:55.098 NVP: prebuffering pause
2008-08-09 13:05:57.912 WriteAudio: buffer underrun
2008-08-09 13:05:58.120 WriteAudio: buffer underrun
2008-08-09 13:05:58.124 NVP: prebuffering pause
2008-08-09 13:05:58.585 TV: Attempting to change from WatchingLiveTV to None
2008-08-09 13:05:59.055 TV: Changing from WatchingLiveTV to None
2008-08-09 13:05:59.081 DPMS Reactivated.
2008-08-09 13:06:04.808 TV: Attempting to change from None to WatchingLiveTV
2008-08-09 13:06:04.809 Using protocol version 40
2008-08-09 13:06:06.815 DPMS Deactivated 
2008-08-09 13:06:07.734 AFD: Opened codec 0x8a03a10, id(MPEG2VIDEO) type(Video)
2008-08-09 13:06:07.734 AFD: codec MP2 has 2 channels
2008-08-09 13:06:07.734 AFD: Opened codec 0x85739b0, id(MP2) type(Audio)
2008-08-09 13:06:07.853 Opening audio device 'default'. ch 2(2) sr 48000
2008-08-09 13:06:07.853 Opening ALSA audio device 'default'.
2008-08-09 13:06:07.913 VideoOutputXv: XVideo Adaptor Name: 'NV17 Video Texture'
2008-08-09 13:06:08.000 OSD Theme Dimensions W: 640 H: 480
2008-08-09 13:06:08.434 TV: Changing from None to WatchingLiveTV
2008-08-09 13:06:08.441 Realtime priority would require SUID as root.
2008-08-09 13:06:08.537 Video timing method: USleep with busy wait
2008-08-09 13:06:16.763 NVP: prebuffering pause
2008-08-09 13:06:18.458 NVP: Prebuffer wait timed out 10 times.
2008-08-09 13:09:02.342 NVP: prebuffering pause
2008-08-09 13:09:02.344 WriteAudio: buffer underrun
2008-08-09 13:09:16.094 TV: Attempting to change from WatchingLiveTV to None
2008-08-09 13:09:16.350 TV: Changing from WatchingLiveTV to None
2008-08-09 13:09:16.443 DPMS Reactivated.
2008-08-09 13:09:22.781 XMLParse::LoadTheme using /usr/share/mythtv/themes/Mythbuntu-8.04/ui.xml
2008-08-09 13:12:06.679 Received a remote 'Clear Cache' request
2008-08-09 13:12:25.595 Received a remote 'Clear Cache' request
2008-08-09 13:12:27.695 Unable to parse themeinfo.xml for glass-wide
2008-08-09 13:12:27.696 The theme (glass-wide) is missing a themeinfo.xml file
2008-08-09 13:13:48.274 Received a remote 'Clear Cache' request
2008-08-09 13:16:05.979 Received a remote 'Clear Cache' request
2008-08-09 13:16:33.745 Received a remote 'Clear Cache' request
2008-08-09 13:17:29.837 Received a remote 'Clear Cache' request
2008-08-09 13:17:40.281 Received a remote 'Clear Cache' request
2008-08-09 13:17:49.791 Unable to parse themeinfo.xml for glass-wide
2008-08-09 13:17:49.791 The theme (glass-wide) is missing a themeinfo.xml file
2008-08-09 13:18:30.009 Received a remote 'Clear Cache' request
2008-08-09 13:18:30.051 Primary screen 0.
2008-08-09 13:18:30.052 Using screen 0, 1024x768 at 0,0
2008-08-09 13:18:30.055 Switching to square mode (Mythbuntu-8.04)
2008-08-09 13:18:31.179 Specified base font 'medium' does not exist for font clock
2008-08-09 13:18:31.179 Specified base font 'medium' does not exist for font small
2008-08-09 13:18:31.179 Specified base font 'medium' does not exist for font medium
2008-08-09 13:18:31.179 Specified base font 'medium' does not exist for font large
2008-08-09 13:18:31.182 Loading from: /usr/share/mythtv/themes/Mythbuntu-8.04/base.xml
2008-08-09 13:18:31.269 Loading from: /usr/share/mythtv/themes/default/base.xml
2008-08-09 13:18:40.498 TV: Attempting to change from None to WatchingLiveTV
2008-08-09 13:18:40.500 Using protocol version 40
2008-08-09 13:18:42.544 DPMS Deactivated 
2008-08-09 13:18:43.250 AFD: Opened codec 0x8495bb0, id(MPEG2VIDEO) type(Video)
2008-08-09 13:18:43.250 AFD: codec MP2 has 2 channels
2008-08-09 13:18:43.251 AFD: Opened codec 0x83396f0, id(MP2) type(Audio)
2008-08-09 13:18:43.428 Opening audio device 'default'. ch 2(2) sr 48000
2008-08-09 13:18:43.428 Opening ALSA audio device 'default'.
2008-08-09 13:18:43.487 VideoOutputXv: XVideo Adaptor Name: 'NV17 Video Texture'
2008-08-09 13:18:43.538 OSD Theme Dimensions W: 640 H: 480
2008-08-09 13:18:44.458 TV: Changing from None to WatchingLiveTV
2008-08-09 13:18:44.465 Realtime priority would require SUID as root.
2008-08-09 13:18:44.561 Video timing method: USleep with busy wait
2008-08-09 13:18:56.657 XMLParse::LoadTheme using /usr/share/mythtv/themes/Mythbuntu-8.04/ui.xml
2008-08-09 13:19:43.640 NVP: prebuffering pause
2008-08-09 13:19:43.677 WriteAudio: buffer underrun
2008-08-09 13:19:45.233 NVP: Prebuffer wait timed out 10 times.
2008-08-09 13:19:53.738 XMLParse::LoadTheme using /usr/share/mythtv/themes/Mythbuntu-8.04/ui.xml
2008-08-09 13:19:54.991 NVP: prebuffering pause
2008-08-09 13:21:44.903 NVP: prebuffering pause
2008-08-09 14:01:04.329 NVP: prebuffering pause
2008-08-09 14:01:04.397 WriteAudio: buffer underrun
2008-08-09 14:01:06.048 NVP: Prebuffer wait timed out 10 times.
2008-08-09 14:01:38.829 NVP: prebuffering pause
2008-08-09 14:24:26.857 NVP: prebuffering pause
2008-08-09 14:24:28.295 WriteAudio: buffer underrun
2008-08-09 14:59:40.817 TV: Attempting to change from WatchingLiveTV to None
2008-08-09 14:59:41.316 TV: Changing from WatchingLiveTV to None
2008-08-09 14:59:41.368 DPMS Reactivated.
2008-08-09 15:00:12.788 XMLParse::LoadTheme using /usr/share/mythtv/themes/Mythbuntu-8.04/video-ui.xml
2008-08-09 17:36:46.653 Received a remote 'Clear Cache' request

The front end is running on the master backend.  The other backend functions appear to be unaffected, and there are no unusual looking entries in the backend logs...

Thanks

---

### Post by laga on 2008-08-10
Can you try a different deinterlacer? The bob deinterlacer is known to cause similar problems.

---

### Post by sadale_1270 on 2008-08-10
Under 7.10 I wasn't using a deinterlacer, since I'm displaying this on a TV. In 8.04, I can't even find the deinterlacer option. Can you give me a pointer?

---

### Post by sadale_1270 on 2008-08-10
OK, playback profiles.  That's pretty neat.  Also going to make things nice when I finally get an HDTV, I guess.  

I changed from CPU+ to SLIM and now my problems are gone.  I'll probably go in and edit CPU+ appropriately when and if I get HDTV, but for now I'm lovin' life.

Thanks for the help!

---

### Post by ilcapo09 on 2008-08-10
I was having the same problem with the exact same video card. I changed the playback profile to Slim and it works fine now.

Just a question, what do these playback profiles actually do?

---

### Post by jdeslip on 2009-01-26
I am having the same problem with my hauppauge hvr 1600 in mythbuntu 0.21 weekly-builds box.  The problem exists even after I change to Slim or set it to a new profile with absolutely no deinterlacer at all.

---

### Post by Da_Teach on 2009-01-28
This sounds extremely like my issue:
[http://ubuntuforums.org/showthread.php?t=1004628](http://ubuntuforums.org/showthread.php?t=1004628)

I am not sure if I ever had it at '10-minute slow', it is indeed extremely slow (I never waited 10-minutes and usually killed the frontend).

Upgrading to nvidia drivers v180.22 helped me but not a lot (its still slow, but more seconds rather then completely hanging). The latest idea seems to be refresh-rate combined with v-sync is causing the slowdown, I personally am not convinced yet.

---

