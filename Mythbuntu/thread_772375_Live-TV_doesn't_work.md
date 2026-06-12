---
title: "Live-TV doesn't work"
date: 2008-04-28
forum: Mythbuntu
---

### Post by the[V]oid on 2008-04-28
Hello!

I installed Mythbuntu yesterday and configured MythTV by following certain guides. Channel search went well and the first thing I wanted to test was the Live-TV Mode. Unfortunately there is neither video nor audio output, the screen just stays black, only an OSD is shown and by using the arrow keys I'm able to zap through the channel list. When leaving the Live-TV Mode I keep getting the following message:```
An error occured during the video playback.
```I had to translate this message from German, so it's possible that it sounds somehow different in original.
The log files don't tell me anything that could help me / I could understand, here they are:
[mythfrontend.log](http://evoid.de/mythfrontend.log) [mythbackend.log](http://evoid.de/mythbackend.log)
The last one was created with "--verbose most" parameter.

There's something really strange, but I don't know whether it has something to do with my problem: There are two files in /var/lib/mythtv/recordings although I'm sure I did record anything yet.

I have also tried to perform a video playback with MPlayer:```
user@host # mplayer dvb://SAT.1
```
This works great.

Please help!

---

### Post by the[V]oid on 2008-04-28
I think that is the error (from frontend-log) that occurs when I try to watch TV:

```
2008-04-28 17:54:39.374 TV: Attempting to change from None to WatchingLiveTV
2008-04-28 17:54:39.376 Using protocol version 40
2008-04-28 17:54:41.314 NVP: Disabling Audio, params(-1,2,44100)
2008-04-28 17:54:41.325 DPMS Deactivated 
2008-04-28 17:54:41.426 VideoOutputXv: XVideo Adaptor Name: 'XV_SWOV'
2008-04-28 17:54:41.520 OSD Theme Dimensions W: 640 H: 480
2008-04-28 17:54:42.530 TV: Changing from None to WatchingLiveTV
2008-04-28 17:54:42.569 Realtime priority would require SUID as root.
2008-04-28 17:54:42.654 Video timing method: DRM
[b]2008-04-28 17:54:43.614 NVP: Couldn't find a matching decoder for: /var/lib/mythtv/recordings/1012_20080428175441.mpg
2008-04-28 17:54:43.614 NVP, Error: JumpToProgram failed.
2008-04-28 17:54:43.614 NVP, Error: Unknown error, exiting decoder[/b]
2008-04-28 17:54:43.615 TV: Attempting to change from WatchingLiveTV to None
2008-04-28 17:54:47.794 TV: Changing from WatchingLiveTV to None
```


***EDIT:** I deactivated the setting "Wait for SEQ-Start Header" in mythtv-setup for my DVB-Device, because I have read somewhere that it might help. It didn't at all, nothing changed. **Here are my updated logfiles:***

Frontend: [http://pastebin.com/f315ad95f](http://pastebin.com/f315ad95f)
Backend: [http://pastebin.com/m6a3de970](http://pastebin.com/m6a3de970)

---

### Post by monir81 on 2009-03-09
I had the same issue using mythbuntu 8.10 and a hvr-1800 card.  I only noticed the error when the capture card type (in mythtv-setup) was set as MPEG-2.  If capture card is set as MPEG-4 or V4L I do not see the error.  My video is still far from perfect while watching live tv, but it does display live tv.

---

