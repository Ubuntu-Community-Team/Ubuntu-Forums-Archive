---
title: "Streaming From RTSP to MP4(h.264+AAC)?"
date: 2014-01-13
forum: Multimedia Software
---

### Post by naviathan on 2014-01-13
I have a client that I've setup with IP cameras streaming RTSP to a Flusonic server setup in Amazon EC2 which then restreams the cams for the flashplayer on their website. They want to start streaming to mobile devices as well. I'm having a hard time figuring out how to get the RTSP to restream as HLS or h.264+AAC packaged in an MP4. Flusonic can do it supposedly, but you must have the paid version which is $2k I don't have. Darwin Streaming Server seems a possible option, but I can't tell whether it will do the conversion or if the feed needs to be converted already. 

Does anyone have any experience with this and maybe know of an open source solution?

---

### Post by FakeOutdoorsman on 2014-01-13
MP4 is not a great choice for live streaming. Standard MP4 files have an index that is required for playback, but the index is generally not created until the file is done being encoded. You would have to use "fragments" if you want to use MP4 for streaming.

Did you see the FFmpeg documentation on [HLS](http://ffmpeg.org/ffmpeg-formats.html#hls-1) and [RTSP](http://ffmpeg.org/ffmpeg-protocols.html#rtsp)? Note that there is a large [HLS patchset](http://thread.gmane.org/gmane.comp.video.ffmpeg.devel/172858) being worked on in FFmpeg so additional improvements are pending. I recommend using a recent FFmpeg build when possible to take advantage of new developments.

You can simply download a [Linux build of ffmpeg](http://ffmpeg.org/download.html#LinuxBuilds), or follow a [step-by-step guide to compile ffmpeg](http://trac.ffmpeg.org/wiki/UbuntuCompilationGuide).

---

### Post by naviathan on 2014-01-13
I know ffmpeg can be used for streaming, but there's no persistence for if the stream drops out and starts up again.

---

