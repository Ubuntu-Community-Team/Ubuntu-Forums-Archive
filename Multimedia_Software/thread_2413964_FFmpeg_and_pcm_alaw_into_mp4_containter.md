---
title: "FFmpeg and pcm_alaw into mp4 containter"
date: 2019-03-04
forum: Multimedia Software
---

### Post by foxs2 on 2019-03-04
Hello, i'm trying to record my camera ip with ffmpeg but since it has a (damn) pcm_alaw audio codec it cant be recorded straight into mp4 container - or am i wrong?

But looks like when i record stream into .ts and then remux it to the mp4 everything works well, is there any way to do that while recording instead of record a file in .ts and then remux to mp4?

This is my command: 
```
ffmpeg -use_wallclock_as_timestamps 1 -rtsp_transport tcp -i rtsp://... -c:a aac -c:v copy -flags +global_header -strftime 1 -f segment -map 0 -segment_time 3600 -reset_timestamps 1 file.ts
```

---

### Post by TheFu on 2019-03-04
I can't help with your specific stuff, but I can show how I do something similar.

You can transcode in real-time with ffmpeg, but you'll need specific settings and/or a beefy CPU to do it.

OTOH, mkv containers can hold pretty much any video codec and any audio codec, so using that container might be the easier answer, if you can.  There are some streaming capabilities that only mp4 supports, I think, so if you are using those, then you'll need to transcode.

I can show my live-tv recordings -to- h.264 transcode stuff:
```

#!/bin/bash

CH="$1"   # digital channel 2.1, 2.2, etc...

# Run for 60 minutes
# use wget to grab the specific channnel - this is using DLNA server URLs
# transcode stdin
/usr/bin/timeout 60m \
wget -q -O - http://hdhr4:5004/auto/v$CH | \
nice ffmpeg -i - -c:v libx264 -crf 19.5 \
         -vf scale=-1:720 \
         -preset veryfast \
         -c:a libvorbis -q:a 6 "$out.mkv"
``` 

This is how I live-transcode TV recordings from an HDHR4 TV tuner in real-time from mpeg2/AC3 audio to h.264/vorbis into an mkv container. If I wanted to stream it, the output would to a streaming server directly, not to a file.

---

### Post by mc4man on 2019-03-04
Your posted command encoded the audio to aac (for the .ts
Did you initially do that for .mp4?
Otherwise as mentioned use .mkv or .mov would also work.

---

### Post by foxs2 on 2019-03-05
> Stream #0:0: Video: hevc (Main), yuvj420p(pc, bt709), 1920x1080, 30 fps, 30 tbr, 90k tbn, 30 tbc
    Stream #0:1: Audio: pcm_alaw, 8000 Hz, mono, s16, 64 kb/s
    Stream #0:2: Data: none

[mp4 @ 0xdbb230] Could not find tag for codec none in stream #2, codec not currently supported in container
Could not write header for output file #0 (incorrect codec parameters ?): Invalid argumentStream mapping:
  Stream #0:0 -> #0:0 (copy)
  Stream #0:1 -> #0:1 (pcm_alaw (native) -> aac (native))
  Stream #0:2 -> #0:2 (copy)




Ok so looks like you helped me a little but now there is a problem with that third stream 0:2 which contain none data. Any further tips?

Thats my command for now:
> ffmpeg -use_wallclock_as_timestamps 1 -rtsp_transport tcp -i rtsp://-map 0 -c:a aac -c:v copy -strict -2 -crf 19.5 -preset veryfast -q:a 6 -f segment -segment_time 30 -reset_timestamps 1 file_%03d.mp4

EDIT:
Ok got it worked with this command:
> ffmpeg -use_wallclock_as_timestamps 1 -rtsp_transport tcp -i rtsp:// -c:a aac -c:v copy -flags +global_header -strftime 1 -f segment -map 0:0 -map 0:1 -segment_time 30 -reset_timestamps 1 file.mp4

Just getting some errors: SEI type 5 size 2200 truncated at 1944
And the video is flickering a little. Something wrong with bitrates?

---

