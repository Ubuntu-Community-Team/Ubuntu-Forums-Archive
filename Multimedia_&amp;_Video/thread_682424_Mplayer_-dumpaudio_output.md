---
title: "Mplayer -dumpaudio output"
date: 2008-01-30
forum: Multimedia &amp; Video
---

### Post by O-pos on 2008-01-30
Hello,

When I extract audio from wmv file, the extracted file is unrecognizable. I use -dumpaudio command. Is there any way to find out what is the output file format? while playing wmv, mplayer says 

Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders
AUDIO: 22050 Hz, 1 ch, s16le, 20.0 kbit/5.67% (ratio: 2501->44100)
Selected audio codec: [ffwmav2] afm: ffmpeg (DivX audio v2 (FFmpeg))

Mediainfo (in Windows) says: 20 Kbps, 22.05 KHz, 1 channel, WMA2

So, after extracting this audio-guy, it is not recognizable. Any idea?

I know about -ao pcm and wav output and then converting it to mp3, but I would like to know if there is direct way without re-re-encoding the audio.

---

