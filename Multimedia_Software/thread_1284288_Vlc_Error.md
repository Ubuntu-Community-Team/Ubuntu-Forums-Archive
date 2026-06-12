---
title: "Vlc Error"
date: 2009-10-06
forum: Multimedia Software
---

### Post by plutonium45 on 2009-10-06
> VLC does not support the audio or video format "samr". Unfortunately there is no way for you to fix this.kind of weired error ..
please help :D 

:guitar:

---

### Post by mc4man on 2009-10-06
I've got to run, but there are numerous threads concerning this, if you can't find maybe someone can post some links for you.

The error message would be a bit more accurate if it stated this

VLC does not support the audio or video format "samr". Unfortunately there is no way for you to fix this with your currently installed vlc **and **libavcodecXX packages.

Vlc can, just not the repo one 

> [0x939b9e0] avcodec decoder debug: libavcodec already initialized
[0x939b9e0] avcodec decoder debug: ffmpeg codec (AMR narrow band) started
[0x939b9e0] avcodec decoder debug: Using 192000 bytes output buffer
[0x939b9e0] main decoder debug: using decoder module "avcodec"




Mplayer should play these for you

Edit: as in mplayer, not MoviePlayer (totem

---

### Post by plutonium45 on 2009-10-06
yes..mplayer plays the file..but I wanted it on vlc :D
thanks for fast response :D

---

### Post by jhahoneyk on 2009-12-19
> **mc4man said:**
> 
Mplayer should play these for you

Edit: as in mplayer, not MoviePlayer (totem

For me even mplayer doesn't play the sound. The output is-

```
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family          
Selected video codec: [ffh263] vfm: ffmpeg (FFmpeg H.263+)                
==========================================================================
==========================================================================
Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders          
Cannot find codec 'libamr_nb' in libavcodec...                            
ADecoder init failed :(                                                   
ADecoder init failed :(                                                   
Cannot find codec for audio format 0x726D6173.                            
Read DOCS/HTML/en/codecs.html!                                            
Audio: no sound
```

---

### Post by mc4man on 2009-12-19
> For me even mplayer doesn't play the sound

That's because starting in karmic, the karmic repo mplayer has been stripped of it's ffmpeg lib support (built-in) and now depends on the installed shared ffmpeg libs which don't support amr ( libavcodec in this case

You can either build your own mplayer or see here, section C

[http://ubuntuforums.org/showthread.php?t=1117283](http://ubuntuforums.org/showthread.php?t=1117283)

if mplayer still can't decode after adding medibuntu to your sources and upgrading libavcodec (which will add add. libs) then build your own

[http://ubuntuforums.org/showthread.php?t=1305181](http://ubuntuforums.org/showthread.php?t=1305181)

---

### Post by jhahoneyk on 2009-12-19
Ok, thanks for the information. Will try that.

---

