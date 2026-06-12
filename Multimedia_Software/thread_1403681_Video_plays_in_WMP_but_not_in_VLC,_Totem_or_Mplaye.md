---
title: "Video plays in WMP but not in VLC, Totem or Mplayer"
date: 2010-02-10
forum: Multimedia Software
---

### Post by Rmantingh on 2010-02-10
I hope there's someone out there who can help me with a problem I have.
My partner is a teacher and has downloaded some videos from a teacher's resource site but can't seem to play them in Ubuntu.
They play fine in Windows XP using Windows Media Player but they only play a few seconds in VLC or Totem and then freeze.
The files in question seem to be normal MPG (MPEG-1) video files but somehow VLC and Totem choke on them.
I have installed all restricted video formats including w32codecs but still no joy.
Anybody have any ideas or what I should check for.
Please help. My partner is threatening to go back to Windows! :-(

---

### Post by mc4man on 2010-02-10
Use a terminal and look at/post output, mplayer may get to the point a bit quicker

mplayer /path/to/filename 
or if need be 
mplayer -v /path/to/filename

or

vlc -vv /path/to/filename
(or just open vlc with vlc -vv and then drop file onto vlc

---

### Post by Rmantingh on 2010-02-10
Thanks for the reply.
I'm a bit shamefaced at the moment because it seems to work in Totem now.
What I did was do a fresh install of Ubuntu 9.10 on a different machine and after installing ubuntu-restricted-extras and other codecs from medibuntu (a.o. w32codecs) the video played fine in Totem.
However when I installed VLC as well and tried to play it in there it still wouldn't play. The following is a snippet of its output using vlc -v

> VLC media player 1.0.3 Goldeneye
[0x99cba18] main demux warning: no access_demux module matching "file" could be loaded
[0x99e1e70] main interface error: no interface module matched "globalhotkeys,none"
[0x99e1e70] main interface error: no suitable interface module
[0x9935140] main libvlc error: interface "globalhotkeys,none" initialization failed
[0x9935140] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
[0x9d40338] ps demux warning: garbage at input, trying to resync...
[0x9d40338] ps demux warning: found sync code
[0x9d8b3b8] pulse audio output: No. of Audio Channels: 2
[0x9da2e68] scaletempo audio filter warning: bad input or output format
[0x9da2e68] main audio filter warning: no audio filter module matching "scaletempo" could be loaded
[0x9d489d8] main decoder warning: dts != current_pts (-306710)
[0x9d489d8] main decoder warning: backward_pts != current_pts (-40000)
QPainter::begin: Paint device returned engine == 0, type: 1
QPainter::begin: Paint device returned engine == 0, type: 1
[0x9d8b3b8] main audio output warning: output date isn't PTS date, requesting resampling (69953)
[0x9d8b3b8] main audio output warning: buffer is 69958 late, triggering upsampling
[0x9d8b3b8] main audio output warning: PTS is out of range (-37967), dropping buffer
[0x9d8b3b8] main audio output warning: buffer is 43610 late, triggering upsampling
[0x9d8b3b8] main audio output warning: output date isn't PTS date, requesting resampling (80081)
[0x9d8b3b8] main audio output warning: PTS is out of range (-35805), dropping buffer
[0x9d8b3b8] main audio output warning: buffer is 97388 late, triggering upsampling
[0x9da6010] main video output warning: late picture skipped (15627 > -137)
[0x9d8b3b8] main audio output warning: PTS is out of range (5864), dropping buffer
[0x9d8b3b8] main audio output warning: PTS is out of range (-20215), dropping buffer
[0x9d8b3b8] main audio output warning: buffer is 44962 late, triggering upsampling
[0x9d8b3b8] main audio output warning: output date isn't PTS date, requesting resampling (80100)
[0x9d8b3b8] main audio output warning: PTS is out of range (34163), dropping buffer
[0x9d8b3b8] main audio output warning: PTS is out of range (8084), dropping buffer
[0x9d8b3b8] main audio output warning: PTS is out of range (-18018), dropping buffer
[0x9da6010] main video output warning: late picture skipped (42146 > -166)
[0x9d8b3b8] main audio output warning: PTS is out of range (9116), dropping buffer
[0x9d8b3b8] main audio output warning: PTS is out of range (-16964), dropping buffer
[0x9d8b3b8] main audio output warning: output date isn't PTS date, requesting resampling (160027)
[0x9da6010] main video output warning: late picture skipped (42122 > -175)
[0x9d8b3b8] main audio output warning: PTS is out of range (37500), dropping buffer
[0x9d8b3b8] main audio output warning: PTS is out of range (11410), dropping buffer
[0x9d8b3b8] main audio output warning: PTS is out of range (-14691), dropping buffer

I think the message about PTS may be a hint but I don't know what it means.

Apparently VLC's own codecs are not as good in handling certain videos as Totem/Gstreamer is (which surprises me as usually it's the other way around).
In the mean time I will 'repair' the other machine to have a clean Totem install and that should help the missus to continue her work on Ubuntu (phew).


Thanks for your help :-)

---

