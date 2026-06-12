---
title: "asx audio live stream not playing"
date: 2010-04-02
forum: Multimedia Software
---

### Post by psz21 on 2010-04-02
Hi, my problem is regarding .asx live streams. Up till 2-3 weeks ago I was able to listen to [http://www.hitradio.hu/webcast/radio.asx](http://www.hitradio.hu/webcast/radio.asx) perfectly well with Totem under Ubuntu 9.10.

Since then whenever I want to start the stream, Totem darkens and nothing happens. I've tried Mplayer and VLC as well but neither of them work (but that's not news because they didn't work when Totem did either).

I had a look at the recent package updates in Synaptic to see if any audio-related ones had been changed and I have downgraded libaudiofile0 (to version 0.2.6-7ubuntu2) and gstreamer0.10-plugins-bad (to version 0.10.14-4ubuntu1). The problem still remained, so I updated them again.

The radio chanel works perfectly under Windows, and other .asx streams (for example [http://glz.co.il/media/glz.asx](http://glz.co.il/media/glz.asx)) are working fine with Totem in Ubuntu.

Any suggestions?

Thanks.

---

### Post by mc4man on 2010-04-02
Not sure why it doesn't work - there seems to be some advanced content available, maybe a factor..?

Anyway here, karmic 32 bit, the station plays in various players, - totem, vlc,  totem-xine, pana, ect. using the mms directly

mms://live2.hit.hu/hitradio

somewhat easier is creating a .m3u and using that - pana loads the quickest, the rest take about 6 -8 secs or so.

```
#EXTM3U
#EXTINF:0,Hit Gyülekezete - Hit Rádió - A jöv&#337; zenéje
mms://live2.hit.hu/hitradio

```

(note - on our 64 bit install all play except totem which chokes on for some reason

---

### Post by psz21 on 2010-04-02
Thanks, the m3u file worked with VLC (but didn't with Totem or Mplayer). Anyway, it's good enough for me for the moment.

---

### Post by mc4man on 2010-04-02
If you where using mplayer from the cli you'd need to go either 
```
mplayer mms://live2.hit.hu/hitradio
```

or for .m3u
mplayer -playlist /path/to/.m3u

( though atm there seems to be an issue on 64 bit with totem - you never said there..

---

