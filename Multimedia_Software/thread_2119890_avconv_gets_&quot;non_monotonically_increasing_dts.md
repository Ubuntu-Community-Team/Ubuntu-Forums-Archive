---
title: "avconv gets &quot;non monotonically increasing dts&quot; failure with simple subtitle copy"
date: 2013-02-25
forum: Multimedia Software
---

### Post by MisterPi on 2013-02-25
I'm using avconv 0.8.5-4 on 12.04 to rearrange streams in VOB's without transcoding.  When I try to work with subtitle streams, I keep running into the failure

Application provided invalid, non monotonically increasing dts to muxer in stream XXX: YYY >= YYY
av_interleaved_write_frame(): Invalid argument

(XXX and YYY are numbers that vary depending on the file).  For instance, on a file with 1 video stream, 2 audio and 2 subtitle, I try

avconv -i foo.vob -map 0 -c: test.vob

and it aborts with the above msg after only a few seconds of video time (I can get it to work if I add '-t 4' but '-t 5' leads to failure).  In this case it complains about stream 4, the second subtitle; I can work around this by adding '-map -0:4' but then I lose the second subtitle stream.  Nor does separating the stream into a separate file (with -map 0:4 and no other map) work.  Sometimes it's the first subtitle stream that causes the failure, sometimes it's both, sometimes there's only one subtitle stream and that fails.

Googling the error msg shows it popping up all over the place, but I only get it for the subtitles, never the audio or video streams.

Anyone know of a workaround, or a different tool that can do the same thing?  I want to do something like

avconv -i foo.vob -map 0:0 -map 0:2 -map 0:4 -map 0:3 -c: bar.vob

That is (in this example), take the video stream, the second audio stream, and both subtitle streams, reversing the order of the subtitle streams.

---

### Post by evilsoup on 2013-02-25
'-c:' isn't a valid avconv/ffmpeg command, I suspect you mean '-c copy' (copy all streams).

---

### Post by MisterPi on 2013-02-25
Sorry, I manually typed it (was on a different machine).  Should've been '-c: copy' (though '-c copy' does the same thing apparently).

---

### Post by gravey on 2013-04-01
Hi MisterPi -

I was getting a similar error with avconv, but the problem appears to be fixed in FFmpeg.  See here:  [http://ubuntuforums.org/showthread.php?t=2127620](http://ubuntuforums.org/showthread.php?t=2127620)

Hope that helps.

---

