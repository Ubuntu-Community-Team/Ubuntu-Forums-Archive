---
title: "stream webm?"
date: 2012-06-14
forum: Multimedia Software
---

### Post by Socomate on 2012-06-14
Hi I'm tryint to stream some live video with ffmpeg; my ffserver.conf is like:
...cut...
<Stream live.webm>
Feed feed1.ffm
Format webm
NoAudio
VideoCodec libvpx
VideoSize vga
VideoFrameRate 25
AVOptionVideo flags +global_header
PreRoll 15
StartSendOnKey
VideoBitRate 400
</Stream>
...cut...


then I start my server and ffmeg (ffmpeg -f video4linux2 -i /dev/video0 http:/localhost:8090/feed1.ffm) everything is working but I demand some live video I'm get the next message in the browser: can not play video, data is corrupt.  and in server side the next warning: "Codec for stream 0 does not use       global headers but container format requires global headers" and that's all.

would some one share his working ffserver.conf (x264 or webm) or could offer a solution about this issue?

My final goal is embebded the stream in a http server win html5.

---

### Post by Derek Karpinski on 2012-06-15
I'm having trouble with ffserver on all formats. VLC plays fine,  but no browser does.  Must be a bug.

---

