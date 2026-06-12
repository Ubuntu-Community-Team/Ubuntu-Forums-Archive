---
title: "Playing VP7 encoded ogg video in 64-bit Kubuntu"
date: 2010-04-30
forum: Multimedia Software
---

### Post by TheSqueak on 2010-04-30
Hi,

I've just installed 64-bit 10.04 on a computer, and I think i've installed all of the codecs that I can find, but mplayer can't find the codec for a selection of my videos. On my 32-bit Karmic machine they play fine.

What have I missed?

relevant outputs :)

```
mediainfo <filename>

{snip irrelevant output}

Video
ID                               : 0 (0x0)
Format                           : VP7
Codec ID                         : VP70
Codec ID/Hint                    : On2

{snip irrelevant output}
```

```
mplayer <filename>

[Ogg] stream 0: video (FOURCC VP70), -vid 0

Ogg file format detected.
VIDEO:  [VP70]  640x352  12bpp  23.976 fps    0.0 kbps ( 0.0 kbyte/s)
.
==========================================================================
Requested video codec family [vp7] (vfm=vfwex) not available.
Enable it at compilation.
Cannot find codec matching selected -vo and video format 0x30375056.

{again, irrelevant output snipped}
```

---

### Post by SpEcIeS on 2010-05-24
It would seem that VP7, and other codecs such as Indeo 5, are not supported on a 64 bit systems yet. You will need to convert them on a 32 bit system.

---

### Post by mc4man on 2010-05-24
As mentioned atm (or forever..?) vp7 decoding is only available thru w32codecs and mplayer,
Saw some mention of it in latest gstreamer release notes but don't see support
> doug@doug-laptop:~$ gst-inspect |grep vp
typefindfunctions: audio/x-wavpack-correction: wvc
typefindfunctions: audio/x-wavpack: wvp, wv
vp8:  vp8enc: On2 VP8 Encoder
vp8:  vp8dec: On2 VP8 Decoder
hdvparse:  hdvparse: HDVParser
wavpack:  wavpackparse: Wavpack parser
wavpack:  wavpackdec: Wavpack audio decoder
wavpack:  wavpackenc: Wavpack audio encoder
rtp:  rtpbvpay: RTP BV Payloader
rtp:  rtpdvpay: RTP DV Payloader
rtp:  rtpmpvpay: RTP MPEG2 ES video payloader
rtp:  rtpmp4vpay: RTP MPEG4 Video payloader
wavparse:  wavparse: WAV audio demuxer
ffmpeg:  ffdec_vp6f: FFmpeg On2 VP6 (Flash version) decoder
ffmpeg:  ffdec_vp6a: FFmpeg On2 VP6 (Flash version, with alpha channel) decoder
ffmpeg:  ffdec_vp6: FFmpeg On2 VP6 decoder
ffmpeg:  ffdec_vp5: FFmpeg On2 VP5 decoder
ffmpeg:  ffdec_vp3: FFmpeg On2 VP3 decoder

Your only hope for future support would lie with ffmpeg (doubtful) and or gstreamer - w64codecs are worthless and will most likely remain so.

If really important you could build yourself a 32 bit mplayer - takes about 20 min.'s or so.

---

### Post by SpEcIeS on 2010-05-24
Using VirtualBox 3.2.0 and a 32 bit virtual install of 10.04, I converted a vp7 codec video to xvid using mencoder. It is a little work, but the end result is videos that I can view. Going to have to try Indeo 5 to xvid next.  :P

---

### Post by andrew.46 on 2010-05-24
Hi,

As always the 32 bit MPlayer rules:

```

andrew@skamandros~$ **[COLOR="Red"]mplayer -vc help | grep -i 'vp7'[/COLOR]**
vp7         vfwex     working   On2 VP7 Personal Codec  [vp7vfw.dll]

andrew@skamandros~$**[COLOR="Red"] mplayer -vc help | grep -i 'indeo'[/COLOR]**
ffindeo3    ffmpeg    working   FFmpeg Intel Indeo 3.1/3.2  [indeo3]
ffindeo2    ffmpeg    working   FFmpeg Indeo 2  [indeo2]
indeo5ds    dshow     working   Intel Indeo 5  [ir50_32.dll]
indeo5      vfwex     working   Intel Indeo 5  [ir50_32.dll]
indeo4      vfw       working   Intel Indeo 4.1  [ir41_32.dll]
indeo3      vfwex     working   Intel Indeo 3.1/3.2  [ir32_32.dll]
indeo5xa    xanim     working   XAnim's Intel Indeo 5  [vid_iv50.xa]
indeo4xa    xanim     working   XAnim's Intel Indeo 4.1  [vid_iv41.xa]
indeo3xa    xanim     working   XAnim's Intel Indeo 3.1/3.2  [vid_iv32.xa]

ffindeo5    ffmpeg    working   FFmpeg Indeo 5  [indeo5]
qtindeo     qtvideo   crashing  Win32/QuickTime Indeo  [QuickTime.qts]

```

Andrew

---

