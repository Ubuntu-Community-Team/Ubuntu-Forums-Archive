---
title: "Encoding video with ffmpeg &amp; mplayer"
date: 2006-08-03
forum: Multimedia &amp; Video
---

### Post by encho on 2006-08-03
Is it possible to pipe mplayer's output to ffmpeg in order to encode video? I know, you will say just use mencoder, but it is not that simple. I never had luck with mencoder when making dvd-compliant videos (needed to do remuxing) and also ffmpeg gives me better results and more compatible streams. Just sometimes (for some videos) it would be fine to use some mplayer filters and such. 
Command
> mplayer -ao pcm:waveheader:file=x.audio -vo yuv4mpeg:file=x.video inputfile.avi
gives me two nice decompressed streams, which are unfortunately too big.
Encoding those two with something like
> ffmpeg -i x.video -i x.audio -target dvd output.mpg
is no problem at all, but piping is real pain. I've tryed | & mkfifo, nothing helps. Anyone?

---

### Post by encho on 2006-08-04
I guess noone knows the answer :(

---

### Post by nakko on 2008-03-10
Mplayer can pipe raw video out, and ffmpeg can accept it. However, being as it is raw, you'll have to tell them what format to use in the pipe. First, make a named pipe to use:
> mkfifo stream.yuv
Here's an example command to give mplayer:
> mplayer inputfile.avi -vo yuv4mpeg:file=stream.yuv -ao null -nosound -noframedrop
And here's an example of how you tell ffmpeg to accept the piped stream:
> ffmpeg -f yuv4mpegpipe -i stream.yuv output.avi

Here's another more complex example to burn subtitles into the video for a portable device that does not accept a separate subtitle stream:
> #!/bin/bash
mkfifo stream.yuv &&
mkfifo stream.wav &&
mplayer -sid 1 video_with_subtitles.mkv -vf scale=480:272 -vo yuv4mpeg:file=stream.yuv -ao null -nosound -noframedrop -quiet -msglevel all=-1 &
mplayer -aid 1 video_with_subtitles.mkv -ao pcm:file=stream.wav -vo null -noframedrop -quiet -msglevel all=-1 &
ffmpeg -f yuv4mpegpipe -i stream.yuv -i stream.wav -acodec libfaac -ac 2 -ab 64 -ar 44100 -vcodec h264 -b 320 -t 30 -flags +loop -cmp +chroma  -partitions +parti4x4+partp8x8+partb8x8 -me umh -subq 5 -trellis 1 -refs 1 -coder 0 -me_range 16 -g 300 -keyint_min 25 -sc_threshold 40 -i_qfactor 0.71 -bt 640 -bufsize 10M -rc_eq 'blurCplx^(1-qComp)' -qcomp 0.6 -qmin 10 -qmax 51 -level 30 -f mp4 -author "Anonymous" -title "Super Cool Video" -aspect 16:9 output.mp4

Which I think will work with iPhone/iPod Touch, but don't hold me to it.

---

