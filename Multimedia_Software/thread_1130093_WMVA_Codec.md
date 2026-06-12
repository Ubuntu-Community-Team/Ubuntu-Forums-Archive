---
title: "WMVA Codec?"
date: 2009-04-19
forum: Multimedia Software
---

### Post by coldReactive on 2009-04-19
is there a package that allows Ubuntu to play WMVA Encoded files? Or no?

---

### Post by coldReactive on 2009-04-20
So I guess that's a no?

---

### Post by andrew.46 on 2009-04-20
Hi coldReactive,

> **coldReactive said:**
> is there a package that allows Ubuntu to play WMVA Encoded files? Or no?

Can you provide a link to such a file? Some can be found here:

[http://wiki.multimedia.cx/index.php?title=WMVA](http://wiki.multimedia.cx/index.php?title=WMVA)

but you will see there is a plethora of naming conventions and container formats :-).

Andrew

---

### Post by coldReactive on 2009-04-20
That would be the S/M Porn video included in the link you provided ( [http://samples.mplayerhq.hu/V-codecs/WMVA/](http://samples.mplayerhq.hu/V-codecs/WMVA/) )

Just so you're aware, w64codecs will not play this type of file according to several WMVA files I had once (which are now all encoded in mpeg2video)

---

### Post by andrew.46 on 2009-04-20
Hi coldReactive,

> **coldReactive said:**
> That would be the S/M Porn video included in the link you provided ( [http://samples.mplayerhq.hu/V-codecs/WMVA/](http://samples.mplayerhq.hu/V-codecs/WMVA/) )

Hmmm.... yes I saw that one but I was a little wary of quoting it directly so as not to offend anybody :-). Looks like the svn MPlayer and FFplay will play this file but I am not sure if the quality of the file is really bad, perhaps it is damaged, or both of these are playing it back poorly! Anyway I attach a screenshot of SMPLayer playing a little piece of it. To play the file MPlayer used the following:

```

Selected video codec: [wmvadmo] vfm: dmo (Windows Media Video Adv DMO)
Selected audio codec: [ffwmav2] afm: ffmpeg (DivX audio v2 (FFmpeg))

```

> Just so you're aware, w64codecs will not play this type of file according to several WMVA files I had once (which are now all encoded in mpeg2video)

Unfortunately I have tested this file with the 32 bit MPlayer and codec pack, I have no experience with 64 bit MPlayer. Perhaps someone cleverer than me might also have a look at this particular file?

All the best,

Andrew

---

### Post by coldReactive on 2009-04-20
I don't like using players that I need to install extra. I use totem to play everything.

---

### Post by andrew.46 on 2009-04-20
Hi coldReactive,

> **coldReactive said:**
> I don't like using players that I need to install extra. I use totem to play everything.

Fair enough. But I opened up Totem (for the first time ever!) and after a few downloads it managed to scrape enough codecs together to play this file so you might be in luck after all :-). This was under Jaunty and again a screenshot.

All the best,

Andrew

---

### Post by coldReactive on 2009-04-20
So what codecs did you use, if I may ask?

---

### Post by andrew.46 on 2009-04-20
Hi coldReactive,

> **coldReactive said:**
> So what codecs did you use, if I may ask?

I blindly accepted a series of gstreamer plugins (bad + ffmpeg) and whatever else Jaunty decreed was necessary. This did not work for your own copy of Totem?

Andrew

---

### Post by coldReactive on 2009-04-20
> **andrew.46 said:**
> Hi coldReactive,



I blindly accepted a series of gstreamer plugins (bad + ffmpeg) and whatever else Jaunty decreed was necessary. This did not work for your own copy of Totem?

Andrew

No, it merely said (for the WMVA files I owned at the time) that the file was corrupt or it could not play that type of file. That was with Hardy and Intrepid. With w64 codecs, ffmpeg, gstreamer (bad, etc.).

---

### Post by andrew.46 on 2009-04-21
Hi coldReactive,

> **coldReactive said:**
> No, it merely said (for the WMVA files I owned at the time) that the file was corrupt or it could not play that type of file. That was with Hardy and Intrepid. With w64 codecs, ffmpeg, gstreamer (bad, etc.).

Perhaps try this particular file which I have demonstrated as working successfully on Jaunty with the Totem player? I have a feeling that this file is damaged but still playback is possible.

All the best,

Andrew

---

### Post by mc4man on 2009-04-21
I happened to be fooling around with a live cd of 8.10 64 bit.
Your sample has wma2 audio so...
Mplayer will play that format of video and audio fine with nothing additional other than install deps installed. (certainly if you build mplayer, probably with the repo version.

From the totem side, **totem-xine** will also play it no problem with nothing other than install deps.

The reason they can play is because both use an internal libavcodec

I don't believe totem can in 64 bit because it's looking for the proper codec(s) in /usr/lib/codecs, (w64codecs) and it's not there (and may never be for 64 bit


> Clip info:
 name: Slavegirl of ZOR
 author: 
 copyright: 2004
 comments: xxx bdsm story

==========================================================================
**Requested video codec family [wmvadmo] (vfm=dmo) not available.**
Enable it at compilation.
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Selected video codec: [ffvc1] vfm: ffmpeg (FFmpeg WVC1)
==========================================================================
==========================================================================
Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders
AUDIO: 48000 Hz, 2 ch, s16le, 96.0 kbit/6.25% (ratio: 12000->192000)
**Selected audio codec: [ffwmav2] afm: ffmpeg (DivX audio v2 (FFmpeg))**
==========================================================================
AO: [alsa] 48000Hz 2ch s16le (2 bytes per sample)
Starting playback...

---

### Post by andrew.46 on 2009-04-21
Hi mc4man,

> **mc4man said:**
> 
```
Selected video codec: [ffvc1] vfm: ffmpeg (FFmpeg WVC1)
```


I forced this video codec (-vc ffvc1) and to my tired old eyes it performed better than my *default* codec:

```
Selected video codec: [wmvadmo] vfm: dmo (Windows Media Video Adv DMO)

```

Another point for those FFmpeg guys...

Andrew

---

### Post by deanjm1963 on 2009-04-21
If you really need to play those formats, do as I did, I bought the codecs from Canonical. You can check them out at the [Canonical Shop]("https://shop.canonical.com/"). I also purchased the ones from [Fluendo]("http://www.fluendo.com") which the Canonical ones are based on. From Canonical you need to purchase 32 & 64 bit codecs separately, but from Fluendo you have the option to download either format whenever required.

They work great.

You might not like the idea of having to pay for them, but when I looked back on the thousands of dollars I've spent on windows software over the last 10 or so years, it's a small price to pay.

---

### Post by mc4man on 2009-04-21
> I forced this video codec (-vc ffvc1) and to my tired old eyes it performed better than my default codec:

It seems on the 64 bit because mplayer can't find any [wma9dmo] then it 'looks' to see what it has itself and can do fairly well in 64 bit

> mplayer wma32.wmv (wmv3, wma2)
VIDEO:  [WMV3]  854x480  24bpp  1000.000 fps  2048.0 kbps (250.0 kbyte/s)
Requested video codec family [wmvdmo] (vfm=dmo) not available.
Enable it at compilation.
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family

Selected video codec: [ffwmv3] vfm: ffmpeg (FFmpeg WMV3/WMV9)
opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders
AUDIO: 48000 Hz, 2 ch, s16le, 192.0 kbit/12.50% (ratio: 24000->192000)
Selected audio codec: [ffwmav2] afm: ffmpeg (DivX audio v2 (FFmpeg))

> mplayer WMVHDsplash.wmv (wmv3, wma3)
Requested video codec family [wmvdmo] (vfm=dmo) not available.
Enable it at compilation.
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Selected video codec: [ffwmv3] vfm: ffmpeg (FFmpeg WMV3/WMV9)
==========================================================================
Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders
[wmapro @ 0xd6d6a0][18] [0] [3f] [0] [0] [0] [0] [0] [0] [0] [0] [0] [0] [0] [e0] [0] [0] [0] 
[wmapro @ 0xd6d6a0] ed sample bit depth = 16
[wmapro @ 0xd6d6a0] ed decode flags = e0
[wmapro @ 0xd6d6a0] samples per frame = 2048
[wmapro @ 0xd6d6a0] log2 frame size = 17
[wmapro @ 0xd6d6a0] max num subframes = 16
[wmapro @ 0xd6d6a0] len prefix = 1
[wmapro @ 0xd6d6a0] num channels = 6
[wmapro @ 0xd6d6a0] lossless = 0
AUDIO: 48000 Hz, 6 ch, s16le, 384.0 kbit/8.33% (ratio: 48000->576000)
Selected audio codec: [ffwmapro] afm: ffmpeg (FFmpeg WMA Pro audio)
==========================================================================[/QU

The not so good

 with wmal 
> Playing wmal.wma.
Requested audio codec family [wma9dmo] (afm=dmo) not available.
Enable it at compilation.
Requested audio codec family [wmadmo] (afm=dmo) not available.
Enable it at compilation.
Cannot find codec for audio format 0x163.
Read DOCS/HTML/en/codecs.html!
Audio: no sound

While the same wmal on 32 bit

> Playing wmal.wma.
==========================================================================
Opening audio decoder: [dmo] Win32/DMO decoders
AUDIO: 88200 Hz, 2 ch, s16le, 1152.0 kbit/40.82% (ratio: 144000->352800)
Selected audio codec: [wma9dmo] afm: dmo (Windows Media Audio 9 DMO)



Note: totem-xine can also handle wmv3 but only with wma2 audio


Edit:
> I bought the codecs from Canonical......

I think that if I had a 64 bit install and wanted to use gstreamer players I'd do exactly that, small price to pay really vs. potential aggravation / non function
Do the codecs allow wmal? (wma lossless

---

### Post by deanjm1963 on 2009-04-21
These are the details from the Fluendo website

> This package contains all of Fluendo's GStreamer plugins which are:

    * Windows Media Audio Decoder (Windows Media 7, 8, 9, 10, Pro, Lossless and Speech)
    * Windows Media Video Decoder (Windows Media 7, 8, 9 and VC1)
    * Windows Media ASF Demuxer
    * Windows Media MMS Networking
    * MPEG2 Video Decoder
    * MPEG4 Part 2 Video Decoder
    * DivX 3.11 Alpha ;-) Video Decoder
    * H.264/AVC Video Decoder
    * MPEG2 Program Stream and Transport Stream demuxer
    * MPEG4 ISO Demuxer
    * MP3 Audio Decoder
    * AAC Audio Decoder
    * LPCM Audio Decoder

Hope this helps.

---

### Post by coldReactive on 2009-04-21
> **deanjm1963 said:**
> These are the details from the Fluendo website

I see they don't have the Indeo 5+ codecs. Needed for some AVIs.

---

### Post by andrew.46 on 2009-04-21
Hi coldReactive,

> **coldReactive said:**
> I see they don't have the Indeo 5+ codecs. Needed for some AVIs.

The MPlayer codec pack has these:

```

andrew@skamandros~$ mplayer -vc help | grep -i indeo
ffindeo3    ffmpeg    working   FFmpeg Intel Indeo 3.1/3.2  [indeo3]
ffindeo2    ffmpeg    working   FFmpeg Indeo 2  [indeo2]
indeo5ds    dshow     working   Intel Indeo 5  [ir50_32.dll]
indeo5      vfwex     working   Intel Indeo 5  [ir50_32.dll]
indeo4      vfw       working   Intel Indeo 4.1  [ir41_32.dll]
indeo3      vfwex     working   Intel Indeo 3.1/3.2  [ir32_32.dll]
indeo5xa    xanim     working   XAnim's Intel Indeo 5  [vid_iv50.xa]
indeo4xa    xanim     working   XAnim's Intel Indeo 4.1  [vid_iv41.xa]
indeo3xa    xanim     working   XAnim's Intel Indeo 3.1/3.2  [vid_iv32.xa]
qtindeo     qtvideo   crashing  Win32/QuickTime Indeo  [QuickTime.qts]

```

But I guess Fluendo pack is about buying a 'legal' copy for those countries that the MPlayer codecs are not allowed.

Andrew

---

### Post by mc4man on 2009-04-21
Keeping this solely to the 64 bit install the fluendo codecs allow gstreamer playback of some of the formats that are otherwise not possible  (in gstreamer only

As far as a 64 bit mplayer then any format supported by ffmpeg (built-in) is possible, plus the couple afforded by w64codecs (or any mplayer set for 64 bit 

So in the case of indeo a 64 bit mplayer can do indeo 3,but not indeo 5 (unless there is a comparable codec pack for 64 bit like 32 bit  ....??

So it would seem (on a 64 bit mplayer) that Indeo 3.1/3.2 is supported (thru it's built in), but Indeo 4/5 aren't (not built-in, not available in /usr/lib/codecs

Indeo3.x sample (works
> ==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Selected video codec: [ffindeo3] vfm: ffmpeg (FFmpeg Intel Indeo 3.1/3.2)

Indeo5 sample (no go
(I put the xanimdlls-alpha-.. in ...codecs, didn't work, though not rejected for elf

> Requested video codec family [indeo5ds] (vfm=dshow) not available.
Enable it at compilation.
................clipped
Opening video decoder: [xanim] XAnim codecs
xacodec: failed to dlopen /usr/lib/codecs/vid_iv50.xa while /usr/lib/codecs/vid_iv50.xa

---

