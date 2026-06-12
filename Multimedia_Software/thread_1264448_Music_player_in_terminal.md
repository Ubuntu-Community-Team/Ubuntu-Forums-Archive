---
title: "Music player in terminal"
date: 2009-09-12
forum: Multimedia Software
---

### Post by knepig91 on 2009-09-12
Can someone tell me the name of the music player that you use in the terminal?

---

### Post by SuperSonic4 on 2009-09-12
There are many but **mpd**, **mocp** and **mp3blaster** come to mind

---

### Post by knepig91 on 2009-09-12
k thx

---

### Post by andrew.46 on 2009-09-12
Hi knepig91,

> **knepig91 said:**
> Can someone tell me the name of the music player that you use in the terminal?

If you want an application that will not only play music but just about *every* type of media file known you could try MPlayer. Below is MPlayer playing an ogg file:

```

andrew@skamandros~/music/iRiver$ **[COLOR="Red"]mplayer rococo_variations.ogg [/COLOR]**
MPlayer SVN-r29672-4.3.3 (C) 2000-2009 MPlayer Team

Playing rococo_variations.ogg.
[Ogg] stream 0: audio (Vorbis), -aid 0
Ogg file format detected.
Clip info:
 Title: Rococo Variations
 Artist: Mstislav Rostropovich : BBC Symphony Orchestra
 Album: Tchaikovsky: Rococo Variations
 Genre: Classical
==========================================================================
Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders
AUDIO: 44100 Hz, 2 ch, s16le, 192.0 kbit/13.61% (ratio: 24000->176400)
Selected audio codec: [ffvorbis] afm: ffmpeg (FFmpeg Vorbis)
==========================================================================
AO: [oss] 44100Hz 2ch s16le (2 bytes per sample)
Video: no video
Starting playback...
A:   3.5 (03.5) of 1109.4 (18:29.4)  0.6% 

```

Mind you if you prefer really *minimal* a simple application such as ogg123 will play the same file just as well:

```

andrew@skamandros~/music/iRiver$ **[COLOR="Red"]ogg123 rococo_variations.ogg [/COLOR]**

Audio Device:   Advanced Linux Sound Architecture (ALSA) output

Playing: rococo_variations.ogg
Ogg Vorbis stream: 2 channel, 44100 Hz
Title: Rococo Variations
Artist: Mstislav Rostropovich : BBC Symphony Orchestra
Album: Tchaikovsky: Rococo Variations
Genre: Classical
Encoded-by: Andrew Strong
Time: 01:04.54 [17:24.90] of 18:29.44  (197.9 kbps)  Output Buffer 100.0% 

```

Lots of choices :).

Andrew

---

