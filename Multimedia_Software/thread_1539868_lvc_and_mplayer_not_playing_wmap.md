---
title: "lvc and mplayer not playing wmap"
date: 2010-07-27
forum: Multimedia Software
---

### Post by illi11 on 2010-07-27
so all attempts to find a suitable fix to my vlc player have failed i am having a problem with wmap. i have got the ubuntu-restricted packager or whatever its called and i still have no sound over my network and i can play them fine on y 8.05 thats been upgraded to 10.04. i find it funny that the driver have disappeared. please help me i have searched and now im pissed that i cant find anything that works for me.

---

### Post by sml on 2010-07-27
good question ... i would love to get wmap going on ubuntu!

no luck with vlc and mplayer :(

---

### Post by luigi_mb on 2010-07-27
> **sml said:**
> good question ... i would love to get wmap going on ubuntu!

no luck with vlc and mplayer :(

Have you tried with smplayer or songbird ? 

/luigi

---

### Post by andrew.46 on 2010-07-27
Hi illi,

A recent enough copy of MPlayer will play wmapro files with a native decoder:

```

andrew@skamandros~$ mplayer -ac help | grep -i 'wmap'
ffwmapro    ffmpeg    untested  WMA Pro audio (FFmpeg)  [wmapro]

```

A sample file here:

```
wget http://samples.mplayerhq.hu/A-codecs/WMA9/WMAPro_5dot1/newOrleans_192_mulitchannel.wma

```

Plays as follows with the svn MPlayer:

```

andrew@skamandros~/Desktop$ mplayer newOrleans_192_mulitchannel.wma 
**[COLOR="Red"]MPlayer SVN-r31834-4.4.4 (C) 2000-2010 MPlayer Team[/COLOR]**

Playing newOrleans_192_mulitchannel.wma.
ASF file format detected.
[asfheader] Audio stream found, -aid 1
Clip info:
 title: 
 author: 
 copyright: 
 comments: 
==========================================================================
Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders
AUDIO: 48000 Hz, 6 ch, floatle, 192.0 kbit/2.08% (ratio: 24000->1152000)
**[COLOR="Red"]Selected audio codec: [ffwmapro] afm: ffmpeg (WMA Pro audio (FFmpeg))[/COLOR]**
==========================================================================
AO: [oss] 48000Hz 6ch s16le (2 bytes per sample)
Video: no video
Starting playback...
A:  60.9 (01:00.8) of 58.7 (58.6)  1.8% 


Exiting... (End of file)

```

Mind you if your copy of vlc is compiled against a recent libavcodec it will have no trouble with this file also, I attach a screenshot to demonstrate this.

Andrew

---

### Post by mc4man on 2010-07-27
to sort of complete things - for gstreamer this ppa will boost your gstreamer plugins, especially for lucid and  karmic
[https://launchpad.net/~gstreamer-developers/+archive/ppa?field.series_filter=](https://launchpad.net/~gstreamer-developers/+archive/ppa?field.series_filter=)


on lucid (edit: and karmic)
> doug@doug-desktop:~$ gst-inspect plugins ffmpeg | grep wma
  ffenc_wmav1: FFmpeg Windows Media Audio 1 encoder
  ffenc_wmav2: FFmpeg Windows Media Audio 2 encoder
  ffdec_wmapro: FFmpeg Windows Media Audio 9 Professional decoder
  ffdec_wmav1: FFmpeg Windows Media Audio 1 decoder
  ffdec_wmav2: FFmpeg Windows Media Audio 2 decoder
  ffdec_wmavoice: FFmpeg Windows Media Audio Voice decode

---

