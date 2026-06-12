---
title: "mplayer won't play mp4, vlc will play in Xine/VLC"
date: 2013-11-02
forum: Multimedia Software
---

### Post by pickarooney on 2013-11-02
I have a number of mp4 files which play perfectly in VLC and Xine but not in (s)mplayer. I'd rather use SMplayer because of its subtitle handling so this is a bit of a kicker.

When running mplayer from the command line with the files I get

[I]Playing myfile.mp4.
MOV: missing data (mdat) chunk! Maybe broken file...
Failed to recognize file format.
[/I]

Mediainfo gives the following:

[I]Complete name                            : myfile.mp4
Format                                   : MPEG-4
Format profile                           : Base Media
Codec ID                                 : isom
File size                                : 293 MiB
Duration                                 : 46mn 22s
Overall bit rate mode                    : Variable
Overall bit rate                         : 882 Kbps
Writing application                      : Larry Sanders

Video
ID                                       : 1
Format                                   : AVC
Format/Info                              : Advanced Video Codec
Format profile                           : High@L3.1
Format settings, CABAC                   : Yes
Format settings, ReFrames                : 5 frames
Codec ID                                 : avc1
Codec ID/Info                            : Advanced Video Coding
Duration                                 : 46mn 22s
Bit rate                                 : 756 Kbps
Width                                    : 720 pixels
Height                                   : 404 pixels
Display aspect ratio                     : 16:9
Frame rate mode                          : Constant
Frame rate                               : 25.000 fps
Color space                              : YUV
Chroma subsampling                       : 4:2:0
Bit depth                                : 8 bits
Scan type                                : Progressive
Bits/(Pixel*Frame)                       : 0.104
Stream size                              : 251 MiB (86%)
Writing library                          : x264 core 138 r2358 9e941d1
Encoding settings                        : cabac=1 / ref=5 / deblock=1:0:0 / analyse=0x3:0x113 / me=umh / subme=8 / psy=1 / psy_rd=1.00:0.00 / mixed_ref=1 / me_range=16 / chroma_me=1 / trellis=1 / 8x8dct=1 / cqm=0 / deadzone=21,11 / fast_pskip=1 / chroma_qp_offset=-2 / threads=6 / lookahead_threads=1 / sliced_threads=0 / nr=0 / decimate=1 / interlaced=0 / bluray_compat=0 / constrained_intra=0 / bframes=3 / b_pyramid=2 / b_adapt=2 / b_bias=0 / direct=3 / weightb=1 / open_gop=0 / weightp=2 / keyint=250 / keyint_min=25 / scenecut=40 / intra_refresh=0 / rc_lookahead=50 / rc=crf / mbtree=1 / crf=19.0 / qcomp=0.60 / qpmin=0 / qpmax=69 / qpstep=4 / ip_ratio=1.40 / aq=1:1.00
Language                                 : English
Matrix coefficients                      : BT.709-5, BT.1361, IEC 61966-2-4 709, SMPTE RP177

Audio
ID                                       : 2
Format                                   : AAC
Format/Info                              : Advanced Audio Codec
Format profile                           : LC
Codec ID                                 : 40
Duration                                 : 46mn 22s
Bit rate mode                            : Variable
Bit rate                                 : 118 Kbps
Maximum bit rate                         : 143 Kbps
Channel(s)                               : 2 channels
Channel positions                        : Front: L R
Sampling rate                            : 48.0 KHz
Compression mode                         : Lossy
Stream size                              : 39.2 MiB (13%)
[/I]

---

### Post by pickarooney on 2013-11-02
The version I have of mplayer (from the standard repositories) is UNKNOWN.
Is there a PPA with a better version?

---

### Post by mc4man on 2013-11-02
You can try the mplayer I have here - if it works out, great, if not then just disable the ppa, remove mplayer, ect.
These are relatively recent builds I update once or twice a month or so, the main difference is they use an internal, current FFmpeg, not the system libav libraries.

Please note that I don't include mencoder so if that's something you want then don't use

Also on ppa page is a link to smplayer ppa for latest smplayer builds, recommended
[https://launchpad.net/~mc3man/+archive/mplayer-test](https://launchpad.net/~mc3man/+archive/mplayer-test)

these mplayer builds also depend on libopus, for precise it is inc. in ppa

---

### Post by warp99 on 2013-11-02
If you enable the universe repository that version will player mp4:

[http://askubuntu.com/questions/148638/how-do-i-enable-the-universe-repository](http://askubuntu.com/questions/148638/how-do-i-enable-the-universe-repository)

---

### Post by pickarooney on 2013-11-03
Unfortunately, neither of those worked. I can't play any files at all now - no video, just audio.

---

### Post by mc4man on 2013-11-03
> **pickarooney said:**
> Unfortunately, neither of those worked. I can't play any files at all now - no video, just audio.

Then change your video output, if mplayer from cli thru -vo , if smplayer in preferences. smplayer also produces an mplayer log you can review & or post

---

### Post by pickarooney on 2013-11-03
I got back to the  original mplayer installation and it works again on 'normal' files but it just doesn't seem to be able to play this file/codec/container type at all unfortunately.

---

