---
title: "how to play WMA and WMX streams?"
date: 2009-12-11
forum: Multimedia Software
---

### Post by ottosykora on 2009-12-11
So far I tried lot, but could not get my favourite radio streaming to play in ubuntu.

I tried vlc, even songbird, but apparently could not find out any useful codes for it.

Is there any chance to find solution?

[http://www.play.cz/listen/listen.php?sh=country&bitrate=32&stype=WMA](http://www.play.cz/listen/listen.php?sh=country&bitrate=32&stype=WMA)

[http://www.countryradio.ch/CRSwindows64.wax](http://www.countryradio.ch/CRSwindows64.wax)

---

### Post by mc4man on 2009-12-11
Can't read anything on the site language wise, the embedded player doesn't seem to work with wma (flash

this would work though (using the 128k aac+
```
vlc http://www.play.cz/radio/countryradio128.aac.m3u

```

or 
```
mplayer -playlist http://www.play.cz/radio/countryradio128.aac.m3u

```

Or make a .m3u file and load/drop it into a player
```
#EXTM3U
#EXTINF:0,Country Radio
http://62.44.1.26:8000/country128aac


```
As far as 2nd link, it plays in vlc, mplayer, ect.
Ex.
```
vlc http://rs3.radiostreamer.com:9330
```

.m3u
```
#EXTM3U
#EXTINF:0,DRS 2006 - Country Radio Switzerland
http://rs3.radiostreamer.com:9330
```

---

### Post by ottosykora on 2009-12-11
many thanks, it works!

---

