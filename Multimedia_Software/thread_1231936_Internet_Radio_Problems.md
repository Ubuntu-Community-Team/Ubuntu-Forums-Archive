---
title: "Internet Radio Problems"
date: 2009-08-05
forum: Multimedia Software
---

### Post by chome4 on 2009-08-05
Trying to get access to this site:

[http://ukreggaeguide.co.uk/radio/index.htm](http://ukreggaeguide.co.uk/radio/index.htm)

But when attempting to search for suitable plugins, I get:

No packages with the requested plugins found

The requested plugins are:

text/html decoder
=================================

Where/how can I get the suitable plugins?

---

### Post by andrew.46 on 2009-08-05
Hi,

MPlayer can access this stream directly if you are interested in doing it that way:

```

andrew@skamandros~$ **[COLOR="Red"]mplayer -cache 2048 -cache-min 80 http://87.117.193.143:9442/[/COLOR]**
MPlayer SVN-r29476-4.2.4 (C) 2000-2009 MPlayer Team

Playing http://87.117.193.143:9442/.
Resolving 87.117.193.143 for AF_INET6...
Couldn't resolve name for AF_INET6: 87.117.193.143
Connecting to server 87.117.193.143[87.117.193.143]: 9442...
Name   : UKRG Radio
Genre  : Reggae
Website: http://www.ukreggaeguide.co.uk
Public : yes
Bitrate: 96kbit/s
Cache size set to 2048 KBytes
Cache fill:  0.00% (0 bytes)   
ICY Info: StreamTitle='Ras Michael & The Sons Of Neg 
         - A Weh Dem A Go Do Wid It? ';StreamUrl='';
Cache fill: 74.22% (1556480 bytes)   
ICY Info: StreamTitle='Lyrical Benjie - Jah the Conqueror ';StreamUrl='';
Cache fill: 79.69% (1671168 bytes)   
Audio only file format detected.
==========================================================================
Opening audio decoder: [mp3lib] MPEG layer-2, layer-3
mpg123: Can't rewind stream by 566 bits!
AUDIO: 22050 Hz, 2 ch, s16le, 96.0 kbit/13.61% (ratio: 12000->88200)
Selected audio codec: [mp3] afm: mp3lib (mp3lib MPEG layer-2, layer-3)
==========================================================================
AO: [oss] 22050Hz 2ch s16le (2 bytes per sample)
Video: no video
Starting playback...
A:  16.3 (16.2) of -0.0 (unknown)  0.5% 79% 

```

It is much cooler from the commandline as well :-).

Andrew

---

### Post by chome4 on 2009-08-05
Works fine now.

Thanks very much

---

