---
title: "WRC TV mplayer plugin"
date: 2009-05-27
forum: Multimedia Software
---

### Post by fillintheblanks on 2009-05-27
has anybody managed to get this to work?

[http://wrc.com/jsp/index.jsp?lnk=300](http://wrc.com/jsp/index.jsp?lnk=300)

I am using both the latest mplayer svn 29324 and mozilla-mplayerplugin in Opera, and its a no go. I know mplayer and the plugin works fine because I am able to get streaming on many sites, just not this one

it seems its not picking up the stream maybe I don't whats wrong with it

> mplayer -msglevel all=9 -playlist "http://demand.global-mix.net/?o=gmuk-n.one-vod/WRC1145.wmv&.wvxgg"


---

### Post by fillintheblanks on 2009-05-29
hmmm World rally radio works. this is the output I get

> mplayer -playlist "http://broadcast.global-mix.net/?m=gmuk-n.one-fm&.wvx"

Resolving broadcast.global-mix.net for AF_INET...
Connecting to server broadcast.global-mix.net[91.193.244.62]: 80...
Cache size set to 320 KBytes
MPlayer SVN-r29328-4.3.3 (C) 2000-2009 MPlayer Team
137 audio & 297 video codecs

Playing [http://o-lon-03.global-mix.net/custplayout/gmuk-n.one-fm/WRCAudio.wma?request=1243614607](http://o-lon-03.global-mix.net/custplayout/gmuk-n.one-fm/WRCAudio.wma?request=1243614607).
Resolving o-lon-03.global-mix.net for AF_INET...
Connecting to server o-lon-03.global-mix.net[193.27.42.194]: 80...
STREAM_ASF, URL: [http://o-lon-03.global-mix.net/custplayout/gmuk-n.one-fm/WRCAudio.wma?request=1243614607](http://o-lon-03.global-mix.net/custplayout/gmuk-n.one-fm/WRCAudio.wma?request=1243614607)
Resolving o-lon-03.global-mix.net for AF_INET...
Connecting to server o-lon-03.global-mix.net[193.27.42.194]: 80...
Resolving o-lon-03.global-mix.net for AF_INET...
Connecting to server o-lon-03.global-mix.net[193.27.42.194]: 80...
Cache size set to 320 KBytes
Cache fill: 17.50% (57344 bytes)   
ASF file format detected.
[asfheader] Audio stream found, -aid 1
Clip info:
 name: 
 author: 
 copyright: 
 comments: 
==========================================================================
Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders
AUDIO: 44100 Hz, 2 ch, s16le, 64.0 kbit/4.54% (ratio: 8003->176400)
Selected audio codec: [ffwmav2] afm: ffmpeg (DivX audio v2 (FFmpeg))
==========================================================================
AO: [oss] 44100Hz 2ch s16le (2 bytes per sample)
Video: no video
Starting playback...



but when I play a video clip it gives me this. endless connecting and never actually connects....

> mplayer -playlist "http://demand.global-mix.net/?o=gmuk-n.one-vod/WRC1154.wmv&.wvxgg"

Resolving demand.global-mix.net for AF_INET...
Connecting to server demand.global-mix.net[91.193.244.62]: 80...
Cache size set to 320 KBytes
MPlayer SVN-r29328-4.3.3 (C) 2000-2009 MPlayer Team
137 audio & 297 video codecs

Playing [http://o-lon-01.global-mix.net/gmuk-n.one-vod/wrc1154.wmv?request=1243614814](http://o-lon-01.global-mix.net/gmuk-n.one-vod/wrc1154.wmv?request=1243614814).
Resolving o-lon-01.global-mix.net for AF_INET...
Connecting to server o-lon-01.global-mix.net[193.27.42.186]: 80...
Cache size set to 320 KBytes


Playing [http://o-lon-01.global-mix.net/gmuk-n.one-vod/wrc1154.wmv?request=1243614814&MSWMExt=.asf](http://o-lon-01.global-mix.net/gmuk-n.one-vod/wrc1154.wmv?request=1243614814&MSWMExt=.asf).
Resolving o-lon-01.global-mix.net for AF_INET...
Connecting to server o-lon-01.global-mix.net[193.27.42.186]: 80...
Cache size set to 320 KBytes


Playing [http://o-lon-01.global-mix.net/gmuk-n.one-vod/wrc1154.wmv?request=1243614814&MSWMExt=.asf](http://o-lon-01.global-mix.net/gmuk-n.one-vod/wrc1154.wmv?request=1243614814&MSWMExt=.asf).
Resolving o-lon-01.global-mix.net for AF_INET...
Connecting to server o-lon-01.global-mix.net[193.27.42.186]: 80...
Cache size set to 320 KBytes


Playing [http://o-lon-01.global-mix.net/gmuk-n.one-vod/wrc1154.wmv?request=1243614814&MSWMExt=.asf](http://o-lon-01.global-mix.net/gmuk-n.one-vod/wrc1154.wmv?request=1243614814&MSWMExt=.asf).
Resolving o-lon-01.global-mix.net for AF_INET...
Connecting to server o-lon-01.global-mix.net[193.27.42.186]: 80...
Cache size set to 320 KBytes


Playing [http://o-lon-01.global-mix.net/gmuk-n.one-vod/wrc1154.wmv?request=1243614814&MSWMExt=.asf](http://o-lon-01.global-mix.net/gmuk-n.one-vod/wrc1154.wmv?request=1243614814&MSWMExt=.asf).
Resolving o-lon-01.global-mix.net for AF_INET...
Connecting to server o-lon-01.global-mix.net[193.27.42.186]: 80...
Cache size set to 320 KBytes


Playing [http://o-lon-01.global-mix.net/gmuk-n.one-vod/wrc1154.wmv?request=1243614814&MSWMExt=.asf](http://o-lon-01.global-mix.net/gmuk-n.one-vod/wrc1154.wmv?request=1243614814&MSWMExt=.asf).
Resolving o-lon-01.global-mix.net for AF_INET...
Connecting to server o-lon-01.global-mix.net[193.27.42.186]: 80...
Cache size set to 320 KBytes


Playing [http://o-lon-01.global-mix.net/gmuk-n.one-vod/wrc1154.wmv?request=1243614814&MSWMExt=.asf](http://o-lon-01.global-mix.net/gmuk-n.one-vod/wrc1154.wmv?request=1243614814&MSWMExt=.asf).
Resolving o-lon-01.global-mix.net for AF_INET...
Connecting to server o-lon-01.global-mix.net[193.27.42.186]: 80...
Cache size set to 320 KBytes


Playing [http://o-lon-01.global-mix.net/gmuk-n.one-vod/wrc1154.wmv?request=1243614814&MSWMExt=.asf](http://o-lon-01.global-mix.net/gmuk-n.one-vod/wrc1154.wmv?request=1243614814&MSWMExt=.asf).
Resolving o-lon-01.global-mix.net for AF_INET...
Connecting to server o-lon-01.global-mix.net[193.27.42.186]: 80...
Cache size set to 320 KBytes


Playing [http://o-lon-01.global-mix.net/gmuk-n.one-vod/wrc1154.wmv?request=1243614814&MSWMExt=.asf](http://o-lon-01.global-mix.net/gmuk-n.one-vod/wrc1154.wmv?request=1243614814&MSWMExt=.asf).
Resolving o-lon-01.global-mix.net for AF_INET...
Connecting to server o-lon-01.global-mix.net[193.27.42.186]: 80...
Cache size set to 320 KBytes


Playing [http://o-lon-01.global-mix.net/gmuk-n.one-vod/wrc1154.wmv?request=1243614814&MSWMExt=.asf](http://o-lon-01.global-mix.net/gmuk-n.one-vod/wrc1154.wmv?request=1243614814&MSWMExt=.asf).
Resolving o-lon-01.global-mix.net for AF_INET...
Connecting to server o-lon-01.global-mix.net[193.27.42.186]: 80...
Cache size set to 320 KBytes


Playing [http://o-lon-01.global-mix.net/gmuk-n.one-vod/wrc1154.wmv?request=1243614814&MSWMExt=.asf](http://o-lon-01.global-mix.net/gmuk-n.one-vod/wrc1154.wmv?request=1243614814&MSWMExt=.asf).
Resolving o-lon-01.global-mix.net for AF_INET...
Connecting to server o-lon-01.global-mix.net[193.27.42.186]: 80...
Cache size set to 320 KBytes


Playing [http://o-lon-01.global-mix.net/gmuk-n.one-vod/wrc1154.wmv?request=1243614814&MSWMExt=.asf](http://o-lon-01.global-mix.net/gmuk-n.one-vod/wrc1154.wmv?request=1243614814&MSWMExt=.asf).
Resolving o-lon-01.global-mix.net for AF_INET...
Connecting to server o-lon-01.global-mix.net[193.27.42.186]: 80...
Cache size set to 320 KBytes


Playing [http://o-lon-01.global-mix.net/gmuk-n.one-vod/wrc1154.wmv?request=1243614814&MSWMExt=.asf](http://o-lon-01.global-mix.net/gmuk-n.one-vod/wrc1154.wmv?request=1243614814&MSWMExt=.asf).
Resolving o-lon-01.global-mix.net for AF_INET...
Connecting to server o-lon-01.global-mix.net[193.27.42.186]: 80...




I tested the video clip and it works in Totem-Xine, but not in mplayer how come :?

---

