---
title: "Windows Media RTP depayloader plugin"
date: 2008-04-22
forum: Multimedia Software
---

### Post by revelationman on 2008-04-22
I do have Helix installed but I do think this is more related to Windows Media player 11 

Is there a way to get around this issue I have all the plugins installed install Windows Media Player 10 

Any suggestions

---

### Post by olskar on 2008-06-12
I have this problem too, any solution?

---

### Post by Nawaf on 2008-07-30
Same problem here, too.
I can't watch a video stream. Firefox says a plugin is required but it doesn't specify which one. When I try to open the video with an external player (totem), it says Windows Media RTP depayloader plugin is required to play video.
Does any one now how to fix this?

---

### Post by David Oxland on 2008-08-24
same here

---

### Post by nedkelly on 2008-09-05
I have the same problem in totem, is there any solution to this?

---

### Post by samima on 2008-11-13
same here

---

### Post by nedkelly on 2009-01-03
Have the same problem, is there a solution?

---

### Post by RonB123123 on 2009-02-06
I'm having the same issue. There is a bug report filed but there doesn't seem to be any solution yet.

[https://bugs.launchpad.net/ubuntu/+source/totem/+bug/265017](https://bugs.launchpad.net/ubuntu/+source/totem/+bug/265017)

---

### Post by siabost on 2009-11-14
Me too - Songbird 1.2/BirdTune Nostagie Internet radio.

Hopefully a fix coming soon.

---

### Post by andrew.46 on 2009-11-14
Hi siabost,

> **siabost said:**
> Me too - Songbird 1.2/BirdTune Nostagie Internet radio.

Do you have a link for this radio stream?

Andrew

---

### Post by siabost on 2009-12-08
Hi andrew.46,

Sorry, been away from this thread for a while.

I'm on my works-Windows machine at the minute but it has Songbird on it too.
The link this gives me (on the Win machine) for Nostalgie seems to be: [HTML]mms://vipnrj.yacast.net/nostalgie_webradio02[/HTML]though this gives me a > no uri handler implemented for "mms" error in Windows. In Ubuntu/Songbird I get > Windows Media RTP depayloader plugin required

Hope this helps.

---

### Post by andrew.46 on 2009-12-08
Hi siabost,

This plays well enough for me from the commandline with MPlayer:

```

andrew@skamandros~$ **[COLOR="Red"]mplayer mms://vipnrj.yacast.net/nostalgie_webradio02[/COLOR]**
MPlayer SVN-r29976-4.3.3 (C) 2000-2009 MPlayer Team

Playing mms://vipnrj.yacast.net/nostalgie_webradio02.
STREAM_ASF, URL: mms://vipnrj.yacast.net/nostalgie_webradio02
Resolving vipnrj.yacast.net for AF_INET6...
Couldn't resolve name for AF_INET6: vipnrj.yacast.net
Resolving vipnrj.yacast.net for AF_INET...
Connecting to server vipnrj.yacast.net[213.205.99.101]: 1755...
connect error: Connection refused
Resolving vipnrj.yacast.net for AF_INET6...
Couldn't resolve name for AF_INET6: vipnrj.yacast.net
Resolving vipnrj.yacast.net for AF_INET...
Connecting to server vipnrj.yacast.net[213.205.97.101]: 80...
Resolving vipnrj.yacast.net for AF_INET6...
Couldn't resolve name for AF_INET6: vipnrj.yacast.net
Resolving vipnrj.yacast.net for AF_INET...
Connecting to server vipnrj.yacast.net[213.205.99.101]: 80...
Cache size set to 110 KBytes
Cache fill: 14.55% (16384 bytes)   
ASF file format detected.
[asfheader] Audio stream found, -aid 1
Clip info:
 title: Rock Legend
 author: Rock Legend
 copyright: Rock Legend
 comments: Rock Legend
==========================================================================
Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders
AUDIO: 48000 Hz, 2 ch, s16le, 128.0 kbit/8.33% (ratio: 16002->192000)
Selected audio codec: [ffwmav2] afm: ffmpeg (DivX audio v2 (FFmpeg))
==========================================================================
AO: [oss] 48000Hz 2ch s16le (2 bytes per sample)
Video: no video
Starting playback...
A:2409222.5 (669:13:42.5) of 1844674428928.0 (-24.-8)  0.5% 23% 

```

and also with vlc if a commandline player is more to your taste :).

All the best,

Andrew

---

### Post by mc4man on 2009-12-08
There are actually 2 streams available for 'Rock Legends', a wma2 you're trying to play and a mp3. you may find the mp3 more useful for other players, though as mentioned mplayer ( or smplayer) and vlc will play the wma2 one fine.

for the .mp3 you could make a m3u file and just load/drop it into just about any player

```
#EXTM3U
#EXTINF:-1,NOSTALGIE ROCK LEGEND
http://stream5.nrj.yacast.net/nostalgie_rock_legend

```

For the wma2 a .m3u could also be used ( maybe there's an alternate http address?

```
#EXTM3U
#EXTINF:0,Rock Legend - Rock Legend
mms://vipnrj.yacast.net/nostalgie_webradio02
```

As is, the wma2 .m3u can be loaded/dropped onto vlc and smplayer or command lined in mplayer or vlc

mplayer -playlist rock_legend.m3u


( myself use a little script in ~/bin for a cli playlist mplayer, so just d. left click on or r.click -> open with mplayl for .m3u's, .pls's, or text lists

```
#!/bin/bash
gnome-terminal -e "mplayer -playlist "$1""
```

---

### Post by siabost on 2009-12-09
Hi guys,

Thanks. That webstream does indeed play perfectly in mplayer.

Question is: can I give Songbird media player access to the required plugin cos there are a few other web-radios listed in Songbird's "BirdTune" add-on that it wont play for the same reason?
If I knew which plugin that would be a start.

Thanks again.

:D

---

### Post by mc4man on 2009-12-09
If there is a plugin that will help you it would probably be the gstreamer bad one
> doug@doug-laptop:~$ gst-inspect-0.10 mmssrc
Factory Details:
  Long name:	MMS streaming source
  Class:	Source/Network
  Description:	Receive data streamed via MSFT Multi Media Server protocol
  Author(s):	Maciej Katafiasz <mathrick@users.sourceforge.net>
  Rank:		none (0)

Plugin Details:
  Name:			mms
  Description:		Microsoft Multi Media Server streaming protocol support
  Filename:		/usr/lib/gstreamer-0.10/libgstmms.so
  Version:		0.10.14
  License:		LGPL
  Source module:	gst-plugins-bad
  Binary package:	GStreamer Bad Plugins (Ubuntu)
  Origin URL:		[https://launchpad.net/distros/ubuntu/+source/gst-plugins-bad0.10](https://launchpad.net/distros/ubuntu/+source/gst-plugins-bad0.10)
ect.,ect


Edit:
If you're inclined to use songbird (which I'm not) then as far as that radio site I'd think only the .mp3 streams will work right, which they do - see screen ( overall songbird seems to have gst plugin issues anyway

---

### Post by okbar on 2010-03-08
can not stream real or media player ,any solution?

---

