---
title: "ffserver causing poor picture quality (caused by transcoding?)"
date: 2016-03-29
forum: Multimedia Software
---

### Post by Andrew_Wood on 2016-03-29
[COLOR=#333333][FONT=Lucida Grande]Im trying to use ffserver to re-stream an H264 stream from an IP CCTV camera. The camera only supports one user at a time so I want to re-stream it so I can use ffmpeg to record and VLC to view simultaneously. Im using ffmpeg to capture the RTSP stream from the camera and pass it to ffserver like this:

```
[/FONT][/COLOR][COLOR=#2E8B57][FONT=Monaco]ffmpeg -i rtsp://cameraip/src/MediaInput/h264/stream_1 -acodec copy -vcodec copy http://127.0.0.1:8090/stream1.ffm[/FONT][/COLOR][COLOR=#333333][FONT=Lucida Grande]
```

[/FONT][/COLOR][COLOR=#333333][FONT=Lucida Grande]But from the Googling Ive done it seems its not possible to likewise configure ffserver to just copy through the data without doing any transcoding?[/FONT][/COLOR]

[COLOR=#333333][FONT=Lucida Grande]I can get an H264 stream by putting the following in ffserver.conf[/FONT][/COLOR]


```
[COLOR=#2E8B57][FONT=Monaco]<Feed stream1.ffm>[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]        File /tmp/stream1.ffm[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]        FileMaxSize 2G[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]        ACL allow 127.0.0.1[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]</Feed>[/FONT][/COLOR]

[COLOR=#2E8B57][FONT=Monaco]<Stream stream1.flv>[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]        Format flv[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]        Feed stream1.ffm[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]        NoAudio[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]        VideoCodec libx264[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]        VideoFrameRate 30[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]        VideoBitRate 4096[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]        VideoSize 600x800[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]        AVOptionVideo crf 23[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]        AVOptionVideo preset medium[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]        # for more info on crf/preset options, type: x264 --help[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]        AVOptionVideo flags +global_header[/FONT][/COLOR]

[COLOR=#2E8B57][FONT=Monaco]</Stream>[/FONT][/COLOR]
```

[COLOR=#333333][FONT=Lucida Grande]But the resulting picture quality its far too blurry and there is a 30 second+ delay between the camera seeing something and it appearing on screen. I can only assume this is due to the transcoding.[/FONT][/COLOR]

[COLOR=#333333][FONT=Lucida Grande]Is there a way round this? There is still no equivalent of -vcodec copy for ffserver? Many thanks[/FONT][/COLOR]

---

