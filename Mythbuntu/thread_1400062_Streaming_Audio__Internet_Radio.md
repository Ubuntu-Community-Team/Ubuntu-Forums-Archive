---
title: "Streaming Audio / Internet Radio"
date: 2010-02-06
forum: Mythbuntu
---

### Post by johnlatz on 2010-02-06
Looking for advice:  where we live, we get no TV reception and only one local AM radio station.  Because of that, we'd become dependent on the MythStream plugin under 0.21-fixes to listen to radio.

Fully know that under 0.22, MythStream has been banished due to bugs.  However, for all I need (radio streams) it always worked fine.  I know the developer has committed to a port to Qt4, but until then I appear to be stuck.  I've looked into MythVodka, I've actually compiled and installed MythFeed - both of those tools appear focused on streaming Video, not Audio.

Does anyone have any thoughts that would let me load & listen to such streams as 
<[http://media.kcrw.com/live/kcrwlive.pls]("http://ubuntuforums.org/view-source:http://media.kcrw.com/live/kcrwlive.pls")> or <http://kpcc.streamguys.com:80/>
???

Thanks

---

### Post by azmyth on 2010-02-06
You can compile mythstream from the sources for 0.22. Shoutcast works but I'm not sure about the video side. It's actually fairly painless compiling mythstream.

---

### Post by gamerchick02 on 2010-02-06
Can you open the .pls file in Rhythmbox or Banshee and play it that way?

I easily play DI.fm and somafm.com stations through Rhythmbox.  There should be a window that opens up when you click on the link that asks if you want to open it in Rhythmbox.

Amy

---

### Post by johnlatz on 2010-02-06
I'll look into trying to get MythStream to compile first...

I've got a single backend/frontend sat underneath the TV that is the HTPC solution for the house - we've got a whole bunch of kiddie shows archived, all of our audio files, etc.  Telling my wife to exit the Myth environment, to right click and launch another app - it may not sound like much, but my kids are 1 and 3, and after getting them down for a nap, having her dinking with a system that is not push button easy is more than I want to ask.

---

### Post by rzlist1 on 2010-02-23
> **azmyth said:**
> You can compile mythstream from the sources for 0.22. Shoutcast works but I'm not sure about the video side. It's actually fairly painless compiling mythstream.


Compiling and adding it to Mythtv is fairly painless. But does it work? I tried is last week and did not seem to play internet radio. When viewing movie trailers, I get the movie title without actually being played. Here's the log from one of the streamed radio sessions, it seems that mythstream generates the mplayer command but nothing gets played (hangs). The same generated mplayer command works fine from the shell. Any ideas?



***mythstream: starting 80s, 80s, 80s! - S K Y . F M - Hear your classic favorit
es right here! ([www.sky.fm](www.sky.fm)) - [SHOUTcast.com], [http://yp.shoutcast.com/sbin/tune](http://yp.shoutcast.com/sbin/tune)
in-station.pls?id=7022***

MPlayer SVN-r29237-4.4.1 (C) 2000-2009 MPlayer Team
Terminal type `unknown' is not defined.
Playing [http://yp.shoutcast.com/sbin/tunein-station.pls?id=7022](http://yp.shoutcast.com/sbin/tunein-station.pls?id=7022).
Resolving yp.shoutcast.com for AF_INET6...
Couldn't resolve name for AF_INET6: yp.shoutcast.com
Resolving yp.shoutcast.com for AF_INET...
Connecting to server yp.shoutcast.com[207.200.98.25]: 80...
Cache size set to 1024 KBytes
Unknown entry type Version=2
Playing [http://scfire-dtc-aa01.stream.aol.com:80/stream/1013](http://scfire-dtc-aa01.stream.aol.com:80/stream/1013).
Resolving scfire-dtc-aa01.stream.aol.com for AF_INET6...
Couldn't resolve name for AF_INET6: scfire-dtc-aa01.stream.aol.com
Resolving scfire-dtc-aa01.stream.aol.com for AF_INET...
Connecting to server scfire-dtc-aa01.stream.aol.com[205.188.234.1]: 80...
Name   : 80s, 80s, 80s! - S K Y . F M - Hear your classic favorites right here! 
([www.sky.fm](www.sky.fm))
Genre  : 80s Pop Rock Decades
Website: [http://www.sky.fm/the80s/](http://www.sky.fm/the80s/)
Public : yes
Bitrate: 64kbit/s
Cache size set to 1024 KBytes
Cache fill:  0.00% (0 bytes)   
ICY Info: StreamTitle='Kool & The Gang - Fresh';StreamUrl='';
Cache fill:  2.34% (24576 bytes)   
Cache fill:  4.69% (49152 bytes)   
Cache fill:  7.81% (81920 bytes)   
Cache fill:  9.38% (98304 bytes)   
Cache fill: 13.28% (139264 bytes)   
Cache fill: 15.62% (163840 bytes)   
Cache fill: 18.75% (196608 bytes)   
ID_AUDIO_ID=0
Audio only file format detected.
ID_FILENAME=http://scfire-dtc-aa01.stream.aol.com:80/stream/1013
ID_DEMUXER=audio
ID_AUDIO_FORMAT=85
ID_AUDIO_BITRATE=64000
ID_AUDIO_RATE=44100
ID_AUDIO_NCH=0
ID_LENGTH=-0.01
ID_SEEKABLE=0
ID_CHAPTERS=0
==========================================================================
Opening audio decoder: [mp3lib] MPEG layer-2, layer-3
mpg123: Can't rewind stream by 891 bits!
AUDIO: 44100 Hz, 2 ch, s16le, 64.0 kbit/4.54% (ratio: 8000->176400)
ID_AUDIO_BITRATE=64000
ID_AUDIO_RATE=44100
ID_AUDIO_NCH=2
Selected audio codec: [mp3] afm: mp3lib (mp3lib MPEG layer-2, layer-3)
==========================================================================
xport] Buffer size must be between 1 and 2048
xport] Exporting to file: /tmp/mplayer-af_export_tv
xport] Memory mapped to file: /tmp/mplayer-af_export_tv (0xb7881000)
xport] Exporting to file: /tmp/mplayer-af_export_tv
xport] Memory mapped to file: /tmp/mplayer-af_export_tv (0xb7881000)
ulse] working around probably broken pause functionality,
        see [http://www.pulseaudio.org/ticket/440](http://www.pulseaudio.org/ticket/440)
AO: [pulse] 44100Hz 2ch s16le (2 bytes per sample)
xport] Exporting to file: /tmp/mplayer-af_export_tv
xport] Memory mapped to file: /tmp/mplayer-af_export_tv (0xb7881000)
xport] Exporting to file: /tmp/mplayer-af_export_tv
xport] Memory mapped to file: /tmp/mplayer-af_export_tv (0xb7881000)
ID_AUDIO_CODEC=mp3
Video: no video
Starting playback...
A:   0.0 (00.0) of -0.0 (unknown) ??,?% 21%                                     

***mythstream: stream playing***



----------------------------------------


ps -ef | grep mplayer
tv        4492     1  0 18:45 ?        00:00:00 mplayer -wid 56627410 -cache 102
4 -framedrop -identify -mc 1 -nolirc -nomouseinput -slave -user-agent QuickTime/
0 -vo xv, -zoom -af export=/tmp/mplayer-af_export_tv [http://yp.shoutcast.com/sbi](http://yp.shoutcast.com/sbi)
n/tunein-station.pls?id=7022

---

### Post by azmyth on 2010-02-23
Apple Trailers didn't work for me but Shoutcast radio streams work as I'm listening to them right now on my compiled svn. There was some code changes at google codes that I used but I believe I tried the latest one from the mythstream site and it worked for Shoutcast internet radio that is.

As for last.fm etc you'll have to look at something like Boxee. I couldn't get beta to work on 64 bit Ubuntu but alpha works somewhat.

---

### Post by nickrout on 2010-02-23
> **azmyth said:**
> Apple Trailers didn't work for me but Shoutcast radio streams work as I'm listening to them right now on my compiled svn. There was some code changes at google codes that I used but I believe I tried the latest one from the mythstream site and it worked for Shoutcast internet radio that is.

As for last.fm etc you'll have to look at something like Boxee. I couldn't get beta to work on 64 bit Ubuntu but alpha works somewhat.

create a file in your videos filetree, call it KCRW.netradio. In it put one line:

```
http://media.kcrw.com/live/kcrwlive.pls
```

Set up the new filetype .netradio in mythvideo setup and make the custom player command something like ```
mplayer -cache 1024 -playlist $(cat %s)

```

When you attempt to play KCRW.netradio mplayer should play your stream.

---

