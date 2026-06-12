---
title: "RealPlayer (Medibuntu)"
date: 2009-09-07
forum: Multimedia Software
---

### Post by luigi_mb on 2009-09-07
I have installed RealPlayer 11 from the Medibuntu repo. Now, when I click on a ram file (e.g.  [http://www.rootsworld.com/audio/freereed.ram](http://www.rootsworld.com/audio/freereed.ram) ), Realplay starts, but after a few seconds it disappears. If invoked from a terminal, e.g.

```

realplay http://www.rootsworld.com/audio/nordic.ram

```

I get

```

** (realplay.bin:5645): WARNING **: Couldn't find pixmap file: track.png

** (realplay.bin:5645): WARNING **: Couldn't find pixmap file: nonsuperb.png

** (realplay.bin:5645): WARNING **: Couldn't find pixmap file: superbuffer.png

** (realplay.bin:5645): WARNING **: Couldn't find pixmap file: superbufferlive.png

** (realplay.bin:5645): CRITICAL **: file superbufhscale.cpp: line 493 (void hx_superbuf_hscale_init(HXSuperbufHScale*)): assertion `superbuf_hscale->tile_graphics[HX_SUPERB_MODE_BG].pixbuf' failed

(realplay.bin:5645): Pango-CRITICAL **: pango_layout_set_text: assertion `layout != NULL' failed

(realplay.bin:5645): Pango-CRITICAL **: pango_layout_get_pixel_extents: assertion `PANGO_IS_LAYOUT (layout)' failed

(realplay.bin:5645): Pango-CRITICAL **: pango_layout_set_text: assertion `layout != NULL' failed

(realplay.bin:5645): Pango-CRITICAL **: pango_layout_get_pixel_extents: assertion `PANGO_IS_LAYOUT (layout)' failed

(realplay.bin:5645): Pango-CRITICAL **: pango_layout_set_text: assertion `layout != NULL' failed

(realplay.bin:5645): Pango-CRITICAL **: pango_layout_get_pixel_extents: assertion `PANGO_IS_LAYOUT (layout)' failed

(realplay.bin:5645): Pango-CRITICAL **: pango_layout_set_text: assertion `layout != NULL' failed

(realplay.bin:5645): Pango-CRITICAL **: pango_layout_get_pixel_extents: assertion `PANGO_IS_LAYOUT (layout)' failed

(realplay.bin:5645): Pango-CRITICAL **: pango_layout_set_text: assertion `layout != NULL' failed

(realplay.bin:5645): Pango-CRITICAL **: pango_layout_get_pixel_extents: assertion `PANGO_IS_LAYOUT (layout)' failed

(realplay.bin:5645): Pango-CRITICAL **: pango_layout_set_text: assertion `layout != NULL' failed

(realplay.bin:5645): Pango-CRITICAL **: pango_layout_get_pixel_extents: assertion `PANGO_IS_LAYOUT (layout)' failed

(realplay.bin:5645): Pango-CRITICAL **: pango_layout_set_text: assertion `layout != NULL' failed

(realplay.bin:5645): Pango-CRITICAL **: pango_layout_get_pixel_extents: assertion `PANGO_IS_LAYOUT (layout)' failed

(realplay.bin:5645): Pango-CRITICAL **: pango_layout_set_text: assertion `layout != NULL' failed

(realplay.bin:5645): Pango-CRITICAL **: pango_layout_get_pixel_extents: assertion `PANGO_IS_LAYOUT (layout)' failed

(realplay.bin:5645): Pango-CRITICAL **: pango_layout_set_text: assertion `layout != NULL' failed

(realplay.bin:5645): Pango-CRITICAL **: pango_layout_get_pixel_extents: assertion `PANGO_IS_LAYOUT (layout)' failed

(realplay.bin:5645): Pango-CRITICAL **: pango_layout_set_text: assertion `layout != NULL' failed

(realplay.bin:5645): Pango-CRITICAL **: pango_layout_get_pixel_extents: assertion `PANGO_IS_LAYOUT (layout)' failed

(realplay.bin:5645): Pango-CRITICAL **: pango_layout_set_text: assertion `layout != NULL' failed

(realplay.bin:5645): Pango-CRITICAL **: pango_layout_get_pixel_extents: assertion `PANGO_IS_LAYOUT (layout)' failed

(realplay.bin:5645): Pango-CRITICAL **: pango_layout_set_text: assertion `layout != NULL' failed

(realplay.bin:5645): Pango-CRITICAL **: pango_layout_get_pixel_extents: assertion `PANGO_IS_LAYOUT (layout)' failed

(realplay.bin:5645): Pango-CRITICAL **: pango_layout_set_text: assertion `layout != NULL' failed

(realplay.bin:5645): Pango-CRITICAL **: pango_layout_get_pixel_extents: assertion `PANGO_IS_LAYOUT (layout)' failed

(realplay.bin:5645): Pango-CRITICAL **: pango_layout_set_text: assertion `layout != NULL' failed

(realplay.bin:5645): Pango-CRITICAL **: pango_layout_get_pixel_extents: assertion `PANGO_IS_LAYOUT (layout)' failed

(realplay.bin:5645): Pango-CRITICAL **: pango_layout_set_text: assertion `layout != NULL' failed

(realplay.bin:5645): Pango-CRITICAL **: pango_layout_get_pixel_extents: assertion `PANGO_IS_LAYOUT (layout)' failed

(realplay.bin:5645): Pango-CRITICAL **: pango_layout_set_text: assertion `layout != NULL' failed

(realplay.bin:5645): Pango-CRITICAL **: pango_layout_get_pixel_extents: assertion `PANGO_IS_LAYOUT (layout)' failed

(realplay.bin:5645): Pango-CRITICAL **: pango_layout_set_text: assertion `layout != NULL' failed

(realplay.bin:5645): Pango-CRITICAL **: pango_layout_get_pixel_extents: assertion `PANGO_IS_LAYOUT (layout)' failed

(realplay.bin:5645): Pango-CRITICAL **: pango_layout_set_text: assertion `layout != NULL' failed

(realplay.bin:5645): Pango-CRITICAL **: pango_layout_get_pixel_extents: assertion `PANGO_IS_LAYOUT (layout)' failed

(realplay.bin:5645): Pango-CRITICAL **: pango_layout_set_text: assertion `layout != NULL' failed

(realplay.bin:5645): Pango-CRITICAL **: pango_layout_get_pixel_extents: assertion `PANGO_IS_LAYOUT (layout)' failed

(realplay.bin:5645): Pango-CRITICAL **: pango_layout_set_text: assertion `layout != NULL' failed

(realplay.bin:5645): Pango-CRITICAL **: pango_layout_get_pixel_extents: assertion `PANGO_IS_LAYOUT (layout)' failed

(realplay.bin:5645): Pango-CRITICAL **: pango_layout_set_text: assertion `layout != NULL' failed

(realplay.bin:5645): Pango-CRITICAL **: pango_layout_get_pixel_extents: assertion `PANGO_IS_LAYOUT (layout)' failed

(realplay.bin:5645): Pango-CRITICAL **: pango_layout_set_text: assertion `layout != NULL' failed

(realplay.bin:5645): Pango-CRITICAL **: pango_layout_get_pixel_extents: assertion `PANGO_IS_LAYOUT (layout)' failed

(realplay.bin:5645): Pango-CRITICAL **: pango_layout_set_text: assertion `layout != NULL' failed

(realplay.bin:5645): Pango-CRITICAL **: pango_layout_get_pixel_extents: assertion `PANGO_IS_LAYOUT (layout)' failed

(realplay.bin:5645): Pango-CRITICAL **: pango_layout_set_text: assertion `layout != NULL' failed

(realplay.bin:5645): Pango-CRITICAL **: pango_layout_get_pixel_extents: assertion `PANGO_IS_LAYOUT (layout)' failed

(realplay.bin:5645): Pango-CRITICAL **: pango_layout_set_text: assertion `layout != NULL' failed

(realplay.bin:5645): Pango-CRITICAL **: pango_layout_get_pixel_extents: assertion `PANGO_IS_LAYOUT (layout)' failed

(realplay.bin:5645): Pango-CRITICAL **: pango_layout_set_text: assertion `layout != NULL' failed

(realplay.bin:5645): Pango-CRITICAL **: pango_layout_get_pixel_extents: assertion `PANGO_IS_LAYOUT (layout)' failed

(realplay.bin:5645): Pango-CRITICAL **: pango_layout_set_text: assertion `layout != NULL' failed

(realplay.bin:5645): Pango-CRITICAL **: pango_layout_get_pixel_extents: assertion `PANGO_IS_LAYOUT (layout)' failed

(realplay.bin:5645): Pango-CRITICAL **: pango_layout_set_text: assertion `layout != NULL' failed

(realplay.bin:5645): Pango-CRITICAL **: pango_layout_get_pixel_extents: assertion `PANGO_IS_LAYOUT (layout)' failed

(realplay.bin:5645): Pango-CRITICAL **: pango_layout_set_text: assertion `layout != NULL' failed

(realplay.bin:5645): Pango-CRITICAL **: pango_layout_get_pixel_extents: assertion `PANGO_IS_LAYOUT (layout)' failed

(realplay.bin:5645): Pango-CRITICAL **: pango_layout_set_text: assertion `layout != NULL' failed

(realplay.bin:5645): Pango-CRITICAL **: pango_layout_get_pixel_extents: assertion `PANGO_IS_LAYOUT (layout)' failed

(realplay.bin:5645): Pango-CRITICAL **: pango_layout_set_text: assertion `layout != NULL' failed

(realplay.bin:5645): Pango-CRITICAL **: pango_layout_get_pixel_extents: assertion `PANGO_IS_LAYOUT (layout)' failed

(realplay.bin:5645): Pango-CRITICAL **: pango_layout_set_text: assertion `layout != NULL' failed

(realplay.bin:5645): Pango-CRITICAL **: pango_layout_get_pixel_extents: assertion `PANGO_IS_LAYOUT (layout)' failed

(realplay.bin:5645): Pango-CRITICAL **: pango_layout_set_text: assertion `layout != NULL' failed

(realplay.bin:5645): Pango-CRITICAL **: pango_layout_get_pixel_extents: assertion `PANGO_IS_LAYOUT (layout)' failed

(realplay.bin:5645): Pango-CRITICAL **: pango_layout_set_text: assertion `layout != NULL' failed

(realplay.bin:5645): Pango-CRITICAL **: pango_layout_get_pixel_extents: assertion `PANGO_IS_LAYOUT (layout)' failed

(realplay.bin:5645): Pango-CRITICAL **: pango_layout_set_text: assertion `layout != NULL' failed

(realplay.bin:5645): Pango-CRITICAL **: pango_layout_get_pixel_extents: assertion `PANGO_IS_LAYOUT (layout)' failed

(realplay.bin:5645): Pango-CRITICAL **: pango_layout_set_text: assertion `layout != NULL' failed

(realplay.bin:5645): Pango-CRITICAL **: pango_layout_get_pixel_extents: assertion `PANGO_IS_LAYOUT (layout)' failed

(realplay.bin:5645): Pango-CRITICAL **: pango_layout_set_text: assertion `layout != NULL' failed

(realplay.bin:5645): Pango-CRITICAL **: pango_layout_get_pixel_extents: assertion `PANGO_IS_LAYOUT (layout)' failed
Opening ALSA PCM device default
/usr/bin/realplay: line 57:  5645 Floating point exception$HELIX_LIBS/realplay.bin "$@"


```

An interesting, possibly related, observation. When I use Google Chrome v4.0.206.0, the ram file above does play, but thanks to Totem, not realplay.  Firefox and Seamonkey, don't seem able to do the same. 

Any suggestions? I have read the various how-to's in these forums, and while they are veru useful, do not seem to address this particular quirk.

Thank you in advance.

---

### Post by andrew.46 on 2009-09-08
Hi luigi_mb,

This is quite an odd one as the stream is actually an mp3 stream :-). I opened the stream with MPlayer and I outline the identification of the stream:

```

andrew@skamandros~$ [COLOR="Red"]**mplayer -playlist http://www.rootsworld.com/audio/nordic.ram**[/COLOR]
Resolving www.rootsworld.com for AF_INET6...
Couldn't resolve name for AF_INET6: www.rootsworld.com
Resolving www.rootsworld.com for AF_INET...
Connecting to server www.rootsworld.com[24.248.89.164]: 80...
Cache size set to 320 KBytes
Resolving www.rootsworld.com for AF_INET6...
Couldn't resolve name for AF_INET6: www.rootsworld.com
Resolving www.rootsworld.com for AF_INET...
Connecting to server www.rootsworld.com[24.248.89.164]: 80...
Cache size set to 320 KBytes
MPlayer SVN-r29655-4.3.3 (C) 2000-2009 MPlayer Team

**[COLOR="Red"]Playing http://www.weltmusik.com/xyz/foogy-rain.mp3.[/COLOR]**
Resolving www.weltmusik.com for AF_INET6...
Couldn't resolve name for AF_INET6: www.weltmusik.com
Resolving www.weltmusik.com for AF_INET...
Connecting to server www.weltmusik.com[67.139.134.212]: 80...
Cache size set to 320 KBytes
Cache fill: 17.50% (57344 bytes)   
Resolving www.weltmusik.com for AF_INET6...
Couldn't resolve name for AF_INET6: www.weltmusik.com
Resolving www.weltmusik.com for AF_INET...
Connecting to server www.weltmusik.com[67.139.134.212]: 80...
Resolving www.weltmusik.com for AF_INET6...
Couldn't resolve name for AF_INET6: www.weltmusik.com
Resolving www.weltmusik.com for AF_INET...
Connecting to server www.weltmusik.com[67.139.134.212]: 80...
Audio only file format detected.
==========================================================================
[B][COLOR="Red"]Opening audio decoder: [mp3lib] MPEG layer-2, layer-3
AUDIO: 44100 Hz, 2 ch, s16le, 96.0 kbit/6.80% (ratio: 12000->176400)
Selected audio codec: [mp3] afm: mp3lib (mp3lib MPEG layer-2, layer-3)[/COLOR][/B]
==========================================================================
AO: [oss] 44100Hz 2ch s16le (2 bytes per sample)
Video: no video
Starting playback...
A:  16.0 (15.9) of 470.0 (07:50.0)  0.7% 45% 

```

I don't know much about the RealPlayer but I suspect it does not actually play mp3 streams?

All the best,

Andrew

---

### Post by jrusso2 on 2009-09-08
It should mine does, granted its not from Ubuntu but it plays MP3 streams for me every weekend

---

### Post by andrew.46 on 2009-09-08
Hi jrusso,

> **jrusso2 said:**
> It should mine does, granted its not from Ubuntu but it plays MP3 streams for me every weekend

Oops, wrong again :(. Does your copy of RealPlayer play this particular stream?

Andrew

---

### Post by mc4man on 2009-09-08
I wondering if the op wanted to listen to that site - as in continuing songs.

If so the mplayer plugin seems to be the way if realplayer can't work, see screens,

---

### Post by luigi_mb on 2009-09-08
> **jrusso2 said:**
> It should mine does, granted its not from Ubuntu but it plays MP3 streams for me every weekend

First of all, thank you all for your help.

Yes, in a terminal I tried

```

$ mplayer -playlist http://www.rootsworld.com/audio/nordic.ram

```

and mplayer started going through the plalist and playing the mp3's. 

As to Seamonkey, Firefox v3.5.2, and Google Chrome, I have the distinct feeling there may be conflicts between plugins with similar functions. The problem seems to be that what works, say, for Seamonkey, does not work, say, with Chrome, etc.  For example, mozilla-plugin-vlc works well with Seamonkey, but it crashes Chrome. I wonder whether anybody has found a combination of plugins that works with all the GUI browsers. 

In this moment I have a blank: is there a way to disable a given plugin in a browser other than Firefox? I know I can easily do that in Firefox.

---

### Post by andrew.46 on 2009-09-08
Hi luigi_mb,

> **luigi_mb said:**
> Yes, in a terminal I tried

```

$ mplayer -playlist http://www.rootsworld.com/audio/nordic.ram

```

and mplayer started going through the plalist and playing the mp3's. 

Great news :-). I cannot answer your subsequent question about browser plugins as I will admit that frustration with the various plugins lead me for the most part to abandon them a while back and rely on MPlayer to playback Internet streaming audio. Or vlc if I am feeling a little lazy :). But I suspect many will want the stream playing in a browser window...

Andrew

Andrew

---

### Post by luigi_mb on 2009-09-09
> **andrew.46 said:**
> 

Great news :-). I cannot answer your subsequent question about browser plugins as I will admit that frustration with the various plugins lead me for the most part to abandon them a while back and rely on MPlayer to playback Internet streaming audio. Or vlc if I am feeling a little lazy :). But I suspect many will want the stream playing in a browser window...



I am beginning to see your point, Andrew.  I have already uninstalled those plugins which seem to duplicate the functions of others. For the moment I am keeping mozilla-mplayer (mplayerplug-in) and realplayer, and Seamonkey/Firefox + Google Chrome seem fairly happy. I have uninstalled Totem and plugins, which I found a bit too intrusive. Maybe I will take the plunge, and, as you suggest, use only MPlayer and VLC. Thank you for the good advice.

---

