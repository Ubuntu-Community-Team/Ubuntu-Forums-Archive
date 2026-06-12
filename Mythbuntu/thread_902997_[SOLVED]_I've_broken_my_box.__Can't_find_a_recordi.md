---
title: "[SOLVED] I've broken my box.  Can't find a recording"
date: 2008-08-27
forum: Mythbuntu
---

### Post by Meph1st0 on 2008-08-27
So last night, I started fiddling with my box trying to follow a tutorial on mythtv's wiki about streaming to iPod touch or iPhone
[HTML]http://mythtv.org/wiki/index.php/Streaming_to_iPod_touch_or_iPhone[/HTML]

It mentioned that I need to recompile ffmeg to enable libxvid and so I started to follow the following tutorial on ubuntu's wiki found here [HTML]https://wiki.ubuntu.com/ffmpeg[/HTML].  The compile didn't work and in the process I believe I ended up breaking ffmpeg.  Which I also think broke Live TV playback because all of a sudden that doesn't work either.  Also, for some reason there's a recording that it can't seem to find and it's apparently creating duplicate entries of the recording in the database.

Anyway, I've included the only log I can think of to include here:

```
jbrown@mythbuntu:~$ tail -f /var/log/mythtv/mythfrontend.log
2008-08-27 17:52:56.758 Specified base font 'medium' does not exist for font large
2008-08-27 17:52:56.760 Loading from: /usr/share/mythtv/themes/Mythbuntu-8.04-wide/base.xml
2008-08-27 17:52:56.885 Loading from: /usr/share/mythtv/themes/default/base.xml
2008-08-27 17:52:56.976 Registering Internal as a media playback plugin.
2008-08-27 17:52:57.052 MonitorRegisterExtensions(0x100, gif,jpg,png)
2008-08-27 17:52:57.106 Failed to run 'cdrecord --scanbus'
2008-08-27 17:52:57.110 Failed to run 'cdrecord --scanbus -dev=ATA'
2008-08-27 17:52:57.114 Failed to run 'cdrecord --scanbus -dev=ATAPI'
2008-08-27 17:52:57.176 MonitorRegisterExtensions(0x40, ogg,mp3,aac,flac)
2008-08-27 17:52:57.263 NetworkControl: Listening for remote connections on port 6546
2008-08-27 17:53:27.079 Connecting to backend server: 127.0.0.1:6543 (try 1 of 5)
2008-08-27 17:53:27.080 Using protocol version 40
2008-08-27 17:53:27.091 TV: Attempting to change from None to WatchingLiveTV
2008-08-27 17:53:27.092 Using protocol version 40
2008-08-27 17:53:28.228 GetEntryAt(-1) failed.
2008-08-27 17:53:28.229 EntryToProgram(0@Wed Dec 31 17:00:00 1969) failed to get pginfo
2008-08-27 17:53:28.229 TV Error: LiveTV not successfully started
2008-08-27 17:53:28.230 TV Error: LiveTV not successfully started
2008-08-27 17:53:28.299 TV: Deleting TV Chain in destructor
2008-08-27 17:53:28.313 DPMS Deactivated 
2008-08-27 17:53:28.314 DPMS Reactivated.
2008-08-27 17:53:31.114 XMLParse::LoadTheme using /usr/share/mythtv/themes/Mythbuntu-8.04-wide/ui.xml
2008-08-27 17:53:36.194 Error: File 'myth://127.0.0.1:6543/1211_20080827175327.mpg' missing.
2008-08-27 17:53:36.625 Error: File 'myth://127.0.0.1:6543/1211_20080827175327.mpg' missing.
2008-08-27 17:53:37.125 Error: File 'myth://127.0.0.1:6543/1211_20080827175327.mpg' missing.
2008-08-27 17:53:37.626 Error: File 'myth://127.0.0.1:6543/1211_20080827175327.mpg' missing.
2008-08-27 17:53:38.125 Error: File 'myth://127.0.0.1:6543/1211_20080827175327.mpg' missing.
2008-08-27 17:53:38.625 Error: File 'myth://127.0.0.1:6543/1211_20080827175327.mpg' missing.
2008-08-27 17:53:39.125 Error: File 'myth://127.0.0.1:6543/1211_20080827175327.mpg' missing.
2008-08-27 17:53:39.625 Error: File 'myth://127.0.0.1:6543/1211_20080827175327.mpg' missing.
2008-08-27 17:53:40.125 Error: File 'myth://127.0.0.1:6543/1211_20080827175327.mpg' missing.
2008-08-27 17:53:40.625 Error: File 'myth://127.0.0.1:6543/1211_20080827175327.mpg' missing.
2008-08-27 17:53:40.848 Error: File 'myth://127.0.0.1:6543/1211_20080827175327.mpg' missing.
2008-08-27 17:53:41.125 Error: File 'myth://127.0.0.1:6543/1211_20080827175327.mpg' missing.
2008-08-27 17:53:41.625 Error: File 'myth://127.0.0.1:6543/1211_20080827175327.mpg' missing.
2008-08-27 17:53:42.125 Error: File 'myth://127.0.0.1:6543/1211_20080827175327.mpg' missing.
2008-08-27 17:53:43.552 AFD: Opened codec 0x8686ee0, id(MPEG2VIDEO) type(Video)
2008-08-27 17:53:43.552 AFD: codec AC3 has 6 channels
2008-08-27 17:53:43.553 AFD: Opened codec 0x86873d0, id(AC3) type(Audio)
2008-08-27 17:53:44.007 Error: File 'myth://127.0.0.1:6543/1103_20080827100000.mpg' missing.
2008-08-27 17:53:44.041 Error: File 'myth://127.0.0.1:6543/1103_20080827100000.mpg' missing.
2008-08-27 17:53:44.073 Error: File 'myth://127.0.0.1:6543/1103_20080827100000.mpg' missing.
2008-08-27 17:53:44.104 Error: File 'myth://127.0.0.1:6543/1103_20080827100000.mpg' missing.
2008-08-27 17:53:44.137 Error: File 'myth://127.0.0.1:6543/1103_20080827100000.mpg' missing.
2008-08-27 17:53:44.173 Error: File 'myth://127.0.0.1:6543/1103_20080827100000.mpg' missing.
2008-08-27 17:53:44.205 Error: File 'myth://127.0.0.1:6543/1103_20080827100000.mpg' missing.
2008-08-27 17:53:44.237 Error: File 'myth://127.0.0.1:6543/1103_20080827100000.mpg' missing.
2008-08-27 17:53:44.269 Error: File 'myth://127.0.0.1:6543/1103_20080827100000.mpg' missing.
2008-08-27 17:53:44.305 Error: File 'myth://127.0.0.1:6543/1103_20080827100000.mpg' missing.
2008-08-27 17:53:44.337 Error: File 'myth://127.0.0.1:6543/1103_20080827100000.mpg' missing.
2008-08-27 17:53:44.369 Error: File 'myth://127.0.0.1:6543/1103_20080827100000.mpg' missing.
2008-08-27 17:53:44.401 Error: File 'myth://127.0.0.1:6543/1103_20080827100000.mpg' missing.
2008-08-27 17:53:44.438 Error: File 'myth://127.0.0.1:6543/1103_20080827100000.mpg' missing.
2008-08-27 17:53:44.469 Error: File 'myth://127.0.0.1:6543/1103_20080827100000.mpg' missing.
2008-08-27 17:53:44.501 Error: File 'myth://127.0.0.1:6543/1103_20080827100000.mpg' missing.
2008-08-27 17:53:44.533 Error: File 'myth://127.0.0.1:6543/1103_20080827100000.mpg' missing.
2008-08-27 17:53:44.569 Error: File 'myth://127.0.0.1:6543/1103_20080827100000.mpg' missing.
2008-08-27 17:53:44.601 Error: File 'myth://127.0.0.1:6543/1103_20080827100000.mpg' missing.
2008-08-27 17:53:44.637 Error: File 'myth://127.0.0.1:6543/1103_20080827100000.mpg' missing.
2008-08-27 17:53:44.665 Error: File 'myth://127.0.0.1:6543/1103_20080827100000.mpg' missing.
2008-08-27 17:53:44.701 Error: File 'myth://127.0.0.1:6543/1103_20080827100000.mpg' missing.
2008-08-27 17:53:44.733 Error: File 'myth://127.0.0.1:6543/1103_20080827100000.mpg' missing.
2008-08-27 17:53:44.765 Error: File 'myth://127.0.0.1:6543/1103_20080827100000.mpg' missing.
2008-08-27 17:53:44.797 Error: File 'myth://127.0.0.1:6543/1103_20080827100000.mpg' missing.
2008-08-27 17:53:44.833 Error: File 'myth://127.0.0.1:6543/1103_20080827100000.mpg' missing.
2008-08-27 17:53:44.865 Error: File 'myth://127.0.0.1:6543/1103_20080827100000.mpg' missing.
2008-08-27 17:53:44.897 Error: File 'myth://127.0.0.1:6543/1103_20080827100000.mpg' missing.
2008-08-27 17:53:44.929 Error: File 'myth://127.0.0.1:6543/1103_20080827100000.mpg' missing.
2008-08-27 17:53:44.965 Error: File 'myth://127.0.0.1:6543/1103_20080827100000.mpg' missing.
2008-08-27 17:53:44.997 Error: File 'myth://127.0.0.1:6543/1103_20080827100000.mpg' missing.
2008-08-27 17:53:45.029 Error: File 'myth://127.0.0.1:6543/1103_20080827100000.mpg' missing.
2008-08-27 17:53:45.061 Error: File 'myth://127.0.0.1:6543/1103_20080827100000.mpg' missing.
2008-08-27 17:53:52.484 PlaybackBox::showActions(): Error, myth://127.0.0.1:6543/1211_20080827175327.mpg file not found
2008-08-27 17:53:52.674 NVP::OpenFile(): Error, couldn't read file: myth://127.0.0.1:6543/1211_20080827175327.mpg
2008-08-27 17:53:54.501 Error: File 'myth://127.0.0.1:6543/1211_20080827173911.mpg' missing.
2008-08-27 17:53:54.525 Error: File 'myth://127.0.0.1:6543/1211_20080827173911.mpg' missing.
2008-08-27 17:53:54.561 Error: File 'myth://127.0.0.1:6543/1211_20080827173911.mpg' missing.
2008-08-27 17:53:54.594 Error: File 'myth://127.0.0.1:6543/1211_20080827173911.mpg' missing.
2008-08-27 17:53:54.625 Error: File 'myth://127.0.0.1:6543/1211_20080827173911.mpg' missing.
2008-08-27 17:53:54.662 Error: File 'myth://127.0.0.1:6543/1211_20080827173911.mpg' missing.
2008-08-27 17:53:54.693 Error: File 'myth://127.0.0.1:6543/1211_20080827173911.mpg' missing.
2008-08-27 17:53:54.725 Error: File 'myth://127.0.0.1:6543/1211_20080827173911.mpg' missing.
2008-08-27 17:53:54.757 Error: File 'myth://127.0.0.1:6543/1211_20080827173911.mpg' missing.
2008-08-27 17:53:54.789 Error: File 'myth://127.0.0.1:6543/1211_20080827173911.mpg' missing.
2008-08-27 17:53:54.833 Error: File 'myth://127.0.0.1:6543/1211_20080827173911.mpg' missing.
2008-08-27 17:53:54.857 Error: File 'myth://127.0.0.1:6543/1211_20080827173911.mpg' missing.
2008-08-27 17:53:54.889 Error: File 'myth://127.0.0.1:6543/1211_20080827173911.mpg' missing.
2008-08-27 17:53:54.921 Error: File 'myth://127.0.0.1:6543/1211_20080827173911.mpg' missing.
2008-08-27 17:53:54.957 Error: File 'myth://127.0.0.1:6543/1211_20080827173911.mpg' missing.
2008-08-27 17:53:54.995 Error: File 'myth://127.0.0.1:6543/1211_20080827173911.mpg' missing.
2008-08-27 17:53:55.022 Error: File 'myth://127.0.0.1:6543/1211_20080827173911.mpg' missing.
2008-08-27 17:53:55.053 Error: File 'myth://127.0.0.1:6543/1211_20080827173911.mpg' missing.
2008-08-27 17:53:55.089 Error: File 'myth://127.0.0.1:6543/1211_20080827173911.mpg' missing.
2008-08-27 17:53:55.121 Error: File 'myth://127.0.0.1:6543/1211_20080827173911.mpg' missing.
2008-08-27 17:53:55.156 Error: File 'myth://127.0.0.1:6543/1211_20080827173911.mpg' missing.
2008-08-27 17:53:55.185 Error: File 'myth://127.0.0.1:6543/1211_20080827173911.mpg' missing.
2008-08-27 17:53:55.221 Error: File 'myth://127.0.0.1:6543/1211_20080827173911.mpg' missing.
2008-08-27 17:53:55.250 Error: File 'myth://127.0.0.1:6543/1211_20080827173911.mpg' missing.
2008-08-27 17:53:55.285 Error: File 'myth://127.0.0.1:6543/1211_20080827173911.mpg' missing.
2008-08-27 17:53:55.317 Error: File 'myth://127.0.0.1:6543/1211_20080827173911.mpg' missing.
2008-08-27 17:53:55.353 Error: File 'myth://127.0.0.1:6543/1211_20080827173911.mpg' missing.
2008-08-27 17:53:55.385 Error: File 'myth://127.0.0.1:6543/1211_20080827173911.mpg' missing.
2008-08-27 17:53:55.417 Error: File 'myth://127.0.0.1:6543/1211_20080827173911.mpg' missing.
2008-08-27 17:53:55.449 Error: File 'myth://127.0.0.1:6543/1211_20080827173911.mpg' missing.
2008-08-27 17:53:55.485 Error: File 'myth://127.0.0.1:6543/1211_20080827173911.mpg' missing.
2008-08-27 17:53:55.517 Error: File 'myth://127.0.0.1:6543/1211_20080827173911.mpg' missing.
2008-08-27 17:53:55.549 Error: File 'myth://127.0.0.1:6543/1211_20080827173911.mpg' missing.
2008-08-27 17:53:55.581 Error: File 'myth://127.0.0.1:6543/1211_20080827173911.mpg' missing.
2008-08-27 17:53:55.617 Error: File 'myth://127.0.0.1:6543/1211_20080827173911.mpg' missing.
2008-08-27 17:53:55.649 Error: File 'myth://127.0.0.1:6543/1211_20080827173911.mpg' missing.
2008-08-27 17:53:55.682 Error: File 'myth://127.0.0.1:6543/1211_20080827173911.mpg' missing.
2008-08-27 17:53:55.713 Error: File 'myth://127.0.0.1:6543/1211_20080827173911.mpg' missing.
2008-08-27 17:53:55.756 Error: File 'myth://127.0.0.1:6543/1211_20080827173911.mpg' missing.
2008-08-27 17:53:55.781 Error: File 'myth://127.0.0.1:6543/1211_20080827173911.mpg' missing.
2008-08-27 17:53:55.813 Error: File 'myth://127.0.0.1:6543/1211_20080827173911.mpg' missing.
2008-08-27 17:53:55.845 Error: File 'myth://127.0.0.1:6543/1211_20080827173911.mpg' missing.
2008-08-27 17:53:55.881 Error: File 'myth://127.0.0.1:6543/1211_20080827173911.mpg' missing.
2008-08-27 17:53:55.913 Error: File 'myth://127.0.0.1:6543/1211_20080827173911.mpg' missing.
2008-08-27 17:53:55.945 Error: File 'myth://127.0.0.1:6543/1211_20080827173911.mpg' missing.
2008-08-27 17:53:55.977 Error: File 'myth://127.0.0.1:6543/1211_20080827173911.mpg' missing.
2008-08-27 17:53:56.030 Error: File 'myth://127.0.0.1:6543/1211_20080827173911.mpg' missing.
2008-08-27 17:53:56.045 Error: File 'myth://127.0.0.1:6543/1211_20080827173911.mpg' missing.
2008-08-27 17:53:56.078 Error: File 'myth://127.0.0.1:6543/1211_20080827173911.mpg' missing.
2008-08-27 17:53:56.110 Error: File 'myth://127.0.0.1:6543/1211_20080827173911.mpg' missing.
2008-08-27 17:53:56.145 Error: File 'myth://127.0.0.1:6543/1211_20080827173911.mpg' missing.
2008-08-27 17:53:56.178 Error: File 'myth://127.0.0.1:6543/1211_20080827173911.mpg' missing.
2008-08-27 17:53:56.209 Error: File 'myth://127.0.0.1:6543/1211_20080827173911.mpg' missing.
2008-08-27 17:53:56.241 Error: File 'myth://127.0.0.1:6543/1211_20080827173911.mpg' missing.
2008-08-27 17:53:56.277 Error: File 'myth://127.0.0.1:6543/1211_20080827173911.mpg' missing.
2008-08-27 17:53:56.309 Error: File 'myth://127.0.0.1:6543/1211_20080827173911.mpg' missing.
2008-08-27 17:53:56.341 Error: File 'myth://127.0.0.1:6543/1211_20080827173911.mpg' missing.
2008-08-27 17:53:56.374 Error: File 'myth://127.0.0.1:6543/1211_20080827173911.mpg' missing.
2008-08-27 17:53:56.410 Error: File 'myth://127.0.0.1:6543/1211_20080827173911.mpg' missing.
2008-08-27 17:53:56.441 Error: File 'myth://127.0.0.1:6543/1211_20080827173911.mpg' missing.
2008-08-27 17:53:56.474 Error: File 'myth://127.0.0.1:6543/1211_20080827173911.mpg' missing.
2008-08-27 17:53:56.505 Error: File 'myth://127.0.0.1:6543/1211_20080827173911.mpg' missing.
2008-08-27 17:53:56.541 Error: File 'myth://127.0.0.1:6543/1211_20080827173911.mpg' missing.
2008-08-27 17:53:56.573 Error: File 'myth://127.0.0.1:6543/1211_20080827173911.mpg' missing.
2008-08-27 17:53:56.606 Error: File 'myth://127.0.0.1:6543/1211_20080827173911.mpg' missing.
2008-08-27 17:53:56.641 Error: File 'myth://127.0.0.1:6543/1211_20080827173911.mpg' missing.
2008-08-27 17:53:56.678 Error: File 'myth://127.0.0.1:6543/1211_20080827173911.mpg' missing.
2008-08-27 17:53:56.705 Error: File 'myth://127.0.0.1:6543/1211_20080827173911.mpg' missing.
2008-08-27 17:53:56.737 Error: File 'myth://127.0.0.1:6543/1211_20080827173911.mpg' missing.
2008-08-27 17:53:56.770 Error: File 'myth://127.0.0.1:6543/1211_20080827173911.mpg' missing.
2008-08-27 17:53:56.805 Error: File 'myth://127.0.0.1:6543/1211_20080827173911.mpg' missing.
2008-08-27 17:53:56.837 Error: File 'myth://127.0.0.1:6543/1211_20080827173911.mpg' missing.
2008-08-27 17:53:56.869 Error: File 'myth://127.0.0.1:6543/1211_20080827173911.mpg' missing.
2008-08-27 17:53:56.901 Error: File 'myth://127.0.0.1:6543/1211_20080827173911.mpg' missing.
2008-08-27 17:53:56.937 Error: File 'myth://127.0.0.1:6543/1211_20080827173911.mpg' missing.
2008-08-27 17:53:56.969 Error: File 'myth://127.0.0.1:6543/1211_20080827173911.mpg' missing.
2008-08-27 17:53:57.001 Error: File 'myth://127.0.0.1:6543/1211_20080827173911.mpg' missing.
2008-08-27 17:53:57.033 Error: File 'myth://127.0.0.1:6543/1211_20080827173911.mpg' missing.
2008-08-27 17:53:57.069 Error: File 'myth://127.0.0.1:6543/1211_20080827173911.mpg' missing.
2008-08-27 17:53:57.105 Error: File 'myth://127.0.0.1:6543/1211_20080827173911.mpg' missing.
2008-08-27 17:53:57.113 Error: File 'myth://127.0.0.1:6543/1211_20080827173911.mpg' missing.
2008-08-27 17:53:57.137 Error: File 'myth://127.0.0.1:6543/1211_20080827173911.mpg' missing.
2008-08-27 17:53:57.165 Error: File 'myth://127.0.0.1:6543/1211_20080827173911.mpg' missing.
2008-08-27 17:53:57.202 Error: File 'myth://127.0.0.1:6543/1211_20080827173911.mpg' missing.
2008-08-27 17:53:57.233 Error: File 'myth://127.0.0.1:6543/1211_20080827173911.mpg' missing.
2008-08-27 17:53:57.265 Error: File 'myth://127.0.0.1:6543/1211_20080827173911.mpg' missing.
2008-08-27 17:53:57.297 Error: File 'myth://127.0.0.1:6543/1211_20080827173911.mpg' missing.
2008-08-27 17:53:57.333 Error: File 'myth://127.0.0.1:6543/1211_20080827173911.mpg' missing.
2008-08-27 17:53:57.365 Error: File 'myth://127.0.0.1:6543/1211_20080827173911.mpg' missing.
2008-08-27 17:53:57.397 Error: File 'myth://127.0.0.1:6543/1211_20080827173911.mpg' missing.
2008-08-27 17:53:57.432 Error: File 'myth://127.0.0.1:6543/1211_20080827173911.mpg' missing.
2008-08-27 17:53:57.465 Error: File 'myth://127.0.0.1:6543/1211_20080827173911.mpg' missing.
2008-08-27 17:53:57.497 Error: File 'myth://127.0.0.1:6543/1211_20080827173911.mpg' missing.
2008-08-27 17:53:57.529 Error: File 'myth://127.0.0.1:6543/1211_20080827173911.mpg' missing.
2008-08-27 17:53:57.561 Error: File 'myth://127.0.0.1:6543/1211_20080827173911.mpg' missing.
2008-08-27 17:53:57.586 Error: File 'myth://127.0.0.1:6543/1211_20080827173620.mpg' missing.
2008-08-27 17:53:57.596 Error: File 'myth://127.0.0.1:6543/1211_20080827173620.mpg' missing.
2008-08-27 17:53:57.630 Error: File 'myth://127.0.0.1:6543/1211_20080827173620.mpg' missing.
2008-08-27 17:53:57.662 Error: File 'myth://127.0.0.1:6543/1211_20080827173620.mpg' missing.
2008-08-27 17:53:57.696 Error: File 'myth://127.0.0.1:6543/1211_20080827173620.mpg' missing.
2008-08-27 17:53:57.726 Error: File 'myth://127.0.0.1:6543/1211_20080827173620.mpg' missing.
2008-08-27 17:53:57.762 Error: File 'myth://127.0.0.1:6543/1211_20080827173620.mpg' missing.
2008-08-27 17:53:57.781 Error: File 'myth://127.0.0.1:6543/1211_20080827173617.mpg' missing.
2008-08-27 17:53:57.794 Error: File 'myth://127.0.0.1:6543/1211_20080827173617.mpg' missing.
2008-08-27 17:53:57.825 Error: File 'myth://127.0.0.1:6543/1211_20080827173617.mpg' missing.
2008-08-27 17:53:57.857 Error: File 'myth://127.0.0.1:6543/1211_20080827173617.mpg' missing.
2008-08-27 17:53:57.893 Error: File 'myth://127.0.0.1:6543/1211_20080827173617.mpg' missing.
2008-08-27 17:53:57.929 Error: File 'myth://127.0.0.1:6543/1211_20080827173617.mpg' missing.
2008-08-27 17:53:57.957 Error: File 'myth://127.0.0.1:6543/1211_20080827173617.mpg' missing.
2008-08-27 17:53:57.993 Error: File 'myth://127.0.0.1:6543/1211_20080827173617.mpg' missing.
2008-08-27 17:53:58.025 Error: File 'myth://127.0.0.1:6543/1211_20080827173617.mpg' missing.
2008-08-27 17:53:58.057 Error: File 'myth://127.0.0.1:6543/1211_20080827173617.mpg' missing.
2008-08-27 17:53:58.089 Error: File 'myth://127.0.0.1:6543/1211_20080827173617.mpg' missing.
2008-08-27 17:53:58.125 Error: File 'myth://127.0.0.1:6543/1211_20080827173617.mpg' missing.
2008-08-27 17:53:58.158 Error: File 'myth://127.0.0.1:6543/1211_20080827173617.mpg' missing.
2008-08-27 17:53:58.197 Error: File 'myth://127.0.0.1:6543/1211_20080827173000.mpg' missing.
2008-08-27 17:53:58.200 Error: File 'myth://127.0.0.1:6543/1211_20080827173000.mpg' missing.
2008-08-27 17:53:58.221 Error: File 'myth://127.0.0.1:6543/1211_20080827173000.mpg' missing.
2008-08-27 17:53:58.257 Error: File 'myth://127.0.0.1:6543/1211_20080827173000.mpg' missing.
2008-08-27 17:53:58.289 Error: File 'myth://127.0.0.1:6543/1211_20080827173000.mpg' missing.
2008-08-27 17:53:58.321 Error: File 'myth://127.0.0.1:6543/1211_20080827173000.mpg' missing.
2008-08-27 17:53:58.353 Error: File 'myth://127.0.0.1:6543/1211_20080827173000.mpg' missing.
2008-08-27 17:53:58.389 Error: File 'myth://127.0.0.1:6543/1211_20080827173000.mpg' missing.
2008-08-27 17:53:58.421 Error: File 'myth://127.0.0.1:6543/1211_20080827173000.mpg' missing.
2008-08-27 17:53:58.453 Error: File 'myth://127.0.0.1:6543/1211_20080827173000.mpg' missing.
2008-08-27 17:53:58.485 Error: File 'myth://127.0.0.1:6543/1211_20080827173000.mpg' missing.
2008-08-27 17:53:59.216 AFD: Opened codec 0x862bb60, id(MPEG2VIDEO) type(Video)
2008-08-27 17:53:59.217 AFD: codec AC3 has 2 channels
2008-08-27 17:53:59.217 AFD: Opened codec 0x862c1a0, id(AC3) type(Audio)
2008-08-27 17:54:00.093 TV: Attempting to change from None to WatchingPreRecorded
2008-08-27 17:54:00.115 DPMS Deactivated 
2008-08-27 17:54:00.320 AFD: Opened codec 0x86a56b0, id(MPEG2VIDEO) type(Video)
2008-08-27 17:54:00.320 AFD: codec AC3 has 2 channels
2008-08-27 17:54:00.321 AFD: Opened codec 0x830c070, id(AC3) type(Audio)
2008-08-27 17:54:00.329 Opening audio device 'default'. ch 6(2) sr 48000
2008-08-27 17:54:00.329 Opening ALSA audio device 'default'.
2008-08-27 17:54:02.647 VideoOutputXv: XVideo Adaptor Name: 'NV17 Video Texture'
2008-08-27 17:54:02.820 OSD Theme Dimensions W: 640 H: 480
2008-08-27 17:54:04.312 TV: Changing from None to WatchingPreRecorded
2008-08-27 17:54:04.316 FilterManager: failed to load filter 'none', no such filter exists
2008-08-27 17:54:04.316 Couldn't load deinterlace filter none
2008-08-27 17:54:04.319 Realtime priority would require SUID as root.
2008-08-27 17:54:04.414 Video timing method: USleep with busy wait
2008-08-27 17:54:15.317 TV: Attempting to change from WatchingPreRecorded to None
2008-08-27 17:54:15.412 TV: Changing from WatchingPreRecorded to None
2008-08-27 17:54:15.761 DPMS Reactivated.
2008-08-27 17:54:16.750 AFD: Opened codec 0x96231d0, id(MPEG2VIDEO) type(Video)
2008-08-27 17:54:16.750 AFD: codec AC3 has 2 channels
2008-08-27 17:54:16.751 AFD: Opened codec 0x9623540, id(AC3) type(Audio)
2008-08-27 17:54:17.611 AFD: Opened codec 0x8967eb0, id(MPEG2VIDEO) type(Video)
2008-08-27 17:54:17.611 AFD: codec AC3 has 2 channels
2008-08-27 17:54:17.612 AFD: Opened codec 0x96231d0, id(AC3) type(Audio)
2008-08-27 17:54:18.493 [mpeg2video @ 0xb73e3b88]invalid mb type in P Frame at 60 42
2008-08-27 17:54:18.494 [mpeg2video @ 0xb73e3b88]Warning MVs not available
2008-08-27 17:54:20.205 TV: Attempting to change from None to WatchingLiveTV
2008-08-27 17:54:20.206 Using protocol version 40
2008-08-27 17:54:21.334 GetEntryAt(-1) failed.
2008-08-27 17:54:21.336 EntryToProgram(0@Wed Dec 31 17:00:00 1969) failed to get pginfo
2008-08-27 17:54:21.336 TV Error: LiveTV not successfully started
2008-08-27 17:54:21.336 TV Error: LiveTV not successfully started
2008-08-27 17:54:21.414 TV: Deleting TV Chain in destructor
2008-08-27 17:54:21.428 DPMS Deactivated 
2008-08-27 17:54:21.428 DPMS Reactivated.
2008-08-27 17:54:25.053 XMLParse::LoadTheme using /usr/share/mythtv/themes/Mythbuntu-8.04-wide/ui.xml
2008-08-27 17:54:26.061 Error: File 'myth://127.0.0.1:6543/1211_20080827175420.mpg' missing.
2008-08-27 17:54:26.481 Error: File 'myth://127.0.0.1:6543/1211_20080827175420.mpg' missing.
2008-08-27 17:54:26.981 Error: File 'myth://127.0.0.1:6543/1211_20080827175420.mpg' missing.
2008-08-27 17:54:27.482 Error: File 'myth://127.0.0.1:6543/1211_20080827175420.mpg' missing.
2008-08-27 17:54:27.981 Error: File 'myth://127.0.0.1:6543/1211_20080827175420.mpg' missing.
2008-08-27 17:54:28.481 Error: File 'myth://127.0.0.1:6543/1211_20080827175420.mpg' missing.
2008-08-27 17:54:28.981 Error: File 'myth://127.0.0.1:6543/1211_20080827175420.mpg' missing.
2008-08-27 17:54:29.481 Error: File 'myth://127.0.0.1:6543/1211_20080827175420.mpg' missing.
2008-08-27 17:54:29.981 Error: File 'myth://127.0.0.1:6543/1211_20080827175420.mpg' missing.
2008-08-27 17:54:30.481 Error: File 'myth://127.0.0.1:6543/1211_20080827175420.mpg' missing.
2008-08-27 17:54:30.981 Error: File 'myth://127.0.0.1:6543/1211_20080827175420.mpg' missing.
2008-08-27 17:54:31.481 Error: File 'myth://127.0.0.1:6543/1211_20080827175420.mpg' missing.
2008-08-27 17:54:31.981 Error: File 'myth://127.0.0.1:6543/1211_20080827175420.mpg' missing.
2008-08-27 17:54:32.481 Error: File 'myth://127.0.0.1:6543/1211_20080827175420.mpg' missing.
2008-08-27 17:54:32.981 Error: File 'myth://127.0.0.1:6543/1211_20080827175420.mpg' missing.
2008-08-27 17:54:33.546 Error: File 'myth://127.0.0.1:6543/1211_20080827175420.mpg' missing.
2008-08-27 17:54:33.981 Error: File 'myth://127.0.0.1:6543/1211_20080827175420.mpg' missing.
2008-08-27 17:54:34.481 Error: File 'myth://127.0.0.1:6543/1211_20080827175420.mpg' missing.
2008-08-27 17:54:34.981 Error: File 'myth://127.0.0.1:6543/1211_20080827175420.mpg' missing.
2008-08-27 17:54:35.481 Error: File 'myth://127.0.0.1:6543/1211_20080827175420.mpg' missing.
2008-08-27 17:54:35.982 Error: File 'myth://127.0.0.1:6543/1211_20080827175420.mpg' missing.
2008-08-27 17:54:36.481 Error: File 'myth://127.0.0.1:6543/1211_20080827175420.mpg' missing.
2008-08-27 17:54:36.981 Error: File 'myth://127.0.0.1:6543/1211_20080827175420.mpg' missing.
2008-08-27 17:54:37.481 Error: File 'myth://127.0.0.1:6543/1211_20080827175420.mpg' missing.
2008-08-27 17:54:37.981 Error: File 'myth://127.0.0.1:6543/1211_20080827175420.mpg' missing.
2008-08-27 17:54:38.481 Error: File 'myth://127.0.0.1:6543/1211_20080827175420.mpg' missing.
2008-08-27 17:54:38.981 Error: File 'myth://127.0.0.1:6543/1211_20080827175420.mpg' missing.
2008-08-27 17:54:39.481 Error: File 'myth://127.0.0.1:6543/1211_20080827175420.mpg' missing.
2008-08-27 17:54:39.981 Error: File 'myth://127.0.0.1:6543/1211_20080827175420.mpg' missing.
2008-08-27 17:54:40.481 Error: File 'myth://127.0.0.1:6543/1211_20080827175420.mpg' missing.
2008-08-27 17:54:40.982 Error: File 'myth://127.0.0.1:6543/1211_20080827175420.mpg' missing.
2008-08-27 17:54:41.482 Error: File 'myth://127.0.0.1:6543/1211_20080827175420.mpg' missing.
2008-08-27 17:54:41.982 Error: File 'myth://127.0.0.1:6543/1211_20080827175420.mpg' missing.
2008-08-27 17:54:42.482 Error: File 'myth://127.0.0.1:6543/1211_20080827175420.mpg' missing.
2008-08-27 17:54:42.982 Error: File 'myth://127.0.0.1:6543/1211_20080827175420.mpg' missing.
2008-08-27 17:54:43.481 Error: File 'myth://127.0.0.1:6543/1211_20080827175420.mpg' missing.
2008-08-27 17:54:43.981 Error: File 'myth://127.0.0.1:6543/1211_20080827175420.mpg' missing.
2008-08-27 17:54:44.481 Error: File 'myth://127.0.0.1:6543/1211_20080827175420.mpg' missing.
2008-08-27 17:54:44.981 Error: File 'myth://127.0.0.1:6543/1211_20080827175420.mpg' missing.
2008-08-27 17:54:45.481 Error: File 'myth://127.0.0.1:6543/1211_20080827175420.mpg' missing.
2008-08-27 17:54:45.981 Error: File 'myth://127.0.0.1:6543/1211_20080827175420.mpg' missing.
2008-08-27 17:54:46.481 Error: File 'myth://127.0.0.1:6543/1211_20080827175420.mpg' missing.
2008-08-27 17:54:46.981 Error: File 'myth://127.0.0.1:6543/1211_20080827175420.mpg' missing.
2008-08-27 17:54:47.481 Error: File 'myth://127.0.0.1:6543/1211_20080827175420.mpg' missing.
2008-08-27 17:54:47.981 Error: File 'myth://127.0.0.1:6543/1211_20080827175420.mpg' missing.
2008-08-27 17:54:48.481 Error: File 'myth://127.0.0.1:6543/1211_20080827175420.mpg' missing.
2008-08-27 17:54:48.981 Error: File 'myth://127.0.0.1:6543/1211_20080827175420.mpg' missing.
2008-08-27 17:54:49.481 Error: File 'myth://127.0.0.1:6543/1211_20080827175420.mpg' missing.
2008-08-27 17:54:49.981 Error: File 'myth://127.0.0.1:6543/1211_20080827175420.mpg' missing.
2008-08-27 17:54:50.185 Error: File 'myth://127.0.0.1:6543/1211_20080827175420.mpg' missing.
2008-08-27 17:54:50.481 Error: File 'myth://127.0.0.1:6543/1211_20080827175420.mpg' missing.
2008-08-27 17:54:50.981 Error: File 'myth://127.0.0.1:6543/1211_20080827175420.mpg' missing.
2008-08-27 17:54:51.481 Error: File 'myth://127.0.0.1:6543/1211_20080827175420.mpg' missing.
2008-08-27 17:54:57.788 Deleting UPnP client...

```

In my attempts to fix it I deleted any precompiled ffmpeg files and folders in the home directory and then I went into Mythbuntu Control Center and removed the proprietary codecs and then reinstalled them.  But that didn't seem to fix it.

When I try to watch live tv the screen goes blank for a second and then returns back to the mythfrontend.

I don't know what else to do now.

---

### Post by Meph1st0 on 2008-08-27
Update:  I went into backend setup and looked around but didn't change anything.  Upon leaving it gave me a warning saying that /var/lib/mythtv/recordings is not writable.  I checked this folder out and noticed that the owner of the folder was www-data.

Now this reminds me of something I had done about 2 days ago.  I tried to follow a tutorial at [http://www.chiefhacker.com](http://www.chiefhacker.com) on how to enable Streaming Mythtv from Mythweb Using Flash.  I didn't finish this tutorial because I realized later that the Mythtv wiki states:

> This article will be OUTDATED because this facility is now being built into MythTV. See MythWeb

This is from this article: [http://www.mythtv.org/wiki/index.php/Stream_mythtv_recordings_from_mythweb_using_flash_video](http://www.mythtv.org/wiki/index.php/Stream_mythtv_recordings_from_mythweb_using_flash_video)

Well as part of the tutorial on chiefhacker.com it says to run the following command:

```
Add www-data or apache to mythtv group so it can write to the mythtv data store

chown www-data:www-data * or whichever user runs apache
```

I ran this code and must have changed the owner of the /var/lib/mythtv/recordings folder to www-data.

I don't remember which user should be the owner of /var/lib/mythtv/recordings.  I believe I'm running mythtv as jbrown (at least that's the  username that I'm currently logged in as).  Do I need to change the owner back to jbrown?  or is there some other mythtv user I need to change the owner of that folder to?

---

### Post by Meph1st0 on 2008-08-27
okay, so I changed the owner of /var/lib/mythtv/* (I noticed that all folders under this directory had had their owners changed to www-data) back to jbrown:jbrown.  I went back into Myth Backend and then exited just to see if it'd give me the error again stating that the recordings folder was unwriteable.  Well it didn't give me the error message this time so I assume the folder is writeable again.  However, I haven't solved the problem of live tv not working properly.  Next I'm going to run tail -f mythfrontend.log command again and see what happens.

---

### Post by anonymousdog on 2008-08-27
It's the backend that opens the file, so chown mythtv:mythtv.

In situations where you're trying to give access to another user than the one originally intended, I find it's safer to add users to the owning group (as long as the group has the needed permissions [or even expand them]) rather than seizing ownership.  There's just much less fallout from unintended consequences.

---

### Post by Meph1st0 on 2008-08-27
Fixed!!!! You were right anonymousdog.  I had to change the ownership of the folders in /var/lib/mythtv to mythtv:mythtv.  Thanks again.

---

