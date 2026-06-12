---
title: "audio codec problem?"
date: 2010-06-03
forum: Multimedia Software
---

### Post by anystupidname1 on 2010-06-03
Hello, I'm having difficulty trimming some videos that use a certain audio codec. In case the video codec matters, (shouldn't) it is "wmv9". Can anybody please help?

WMSpeech (voice)
FourCC 0x000A
wmas
1 channel - 20kb/s - 22050hz

Codecs installed on the karmic box:
gstreamer0.10-plugins-bad/karmic-updates uptodate 0.10.14-4ubuntu1.1
gstreamer0.10-plugins-base/karmic-updates uptodate 0.10.25-2ubuntu1.2
gstreamer0.10-plugins-base-apps/karmic-updates uptodate 0.10.25-2ubuntu1.2
gstreamer0.10-plugins-good/karmic uptodate 0.10.16-1ubuntu3
gstreamer0.10-plugins-ugly/karmic uptodate 0.10.12-1
gstreamer0.10-plugins-ugly-multiverse/karmic uptodate 0.10.12-0ubuntu1

Simply trying to play it:
On karmic - VLC 1.0.2 - throws error "no suitable decoder module for "wmas"" and proceeds to play video stream only
On win 7 - VLC 1.0.5 - no errors but no sound (and nothing relevant under "messages" debug window)
On karmic - mplayer 4.4.1 - cannot find requested audio codec [wma9spdshow]
on win 7 - windows media player 11? - plays video and audio properly

Trimming failures:
On win 7 - mencoder 0.0.9.0 - resulting video has no audio
On karmic - mencoder 4.4.1 - resulting video has no audio
On win 7 - ffmpeg 4.0 - resulting video has no audio
On karmic - ffmpeg svn r23439 - resulting video has no audio
On win 7 - virtualdub-MPEG2 1.6.19 - resulting video has no audio
On win 7 - video mp3 extractor 1.6.0.35 - extracts audio to an mp3 fine but I can never get audio and video to be in sync again when I recombine them with virtualdubmod

A few of the commands tried: (all with the resulting soundless video)
ffmpeg -i vidin.wmv -vcodec copy -acodec copy -ss 00 -t 4:00 vidout.avi
mencoder -ss 59 -endpos 4 -oac copy -ovc copy vidin.wmv -o vidout.avi
mencoder vidin.wmv -ofps 23.976 -ovc lavc -oac mp3lame -lameopts abr:br=56 -o vidout.avi
mencoder vidin.wmv -ovc lavc -lavcopts vcodec=mpeg4 -oac mp3lame -o vidout.avi

MediaInfo output:
Video
ID                               : 2
Format                           : VC-1
Format profile                   : MP@HL
Codec ID                         : WMV3
Codec ID/Info                    : Windows Media Video 9
Codec ID/Hint                    : WMV3
Description of the codec         : Windows Media Video 9
Duration                         : 56mn 13s
Bit rate mode                    : Variable
Bit rate                         : 213 Kbps
Width                            : 800 pixels
Height                           : 600 pixels
Display aspect ratio             : 4:3
Frame rate                       : 15.000 fps
Resolution                       : 8 bits
Scan type                        : Progressive
Bits/(Pixel*Frame)               : 0.030
Stream size                      : 85.7 MiB (88%)
Language                         : English (US)

Audio
ID                               : 1
Format                           : WMA
Format profile                   : Voice
Codec ID                         : A
Codec ID/Info                    : Windows Media Audio
Description of the codec         : Windows Media Audio 9 Voice -  20 kbps, 22 kHz, mono
Duration                         : 56mn 12s
Bit rate mode                    : Constant
Bit rate                         : 20.0 Kbps
Channel(s)                       : 1 channel
Sampling rate                    : 22.05 KHz
Resolution                       : 16 bits
Stream size                      : 8.04 MiB (8%)
Language                         : English (US)

This post and several others make me think this is definitely possible... [http://lists.mplayerhq.hu/pipermail/ffmpeg-user/2008-February/014226.html](http://lists.mplayerhq.hu/pipermail/ffmpeg-user/2008-February/014226.html)

---

### Post by anystupidname1 on 2010-06-10
I'm very disappointed that I could not find a way to do this open  source... :(

Sony's Vegas Pro app creates an "audio proxy" (their words, not mine)  which is able  to interpret the audio stream and re-encode it?!?

---

