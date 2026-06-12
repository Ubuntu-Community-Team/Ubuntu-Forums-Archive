---
title: "FFMPEG Streaming to Twitch"
date: 2014-02-18
forum: Multimedia Software
---

### Post by dswanson32 on 2014-02-18
Hey all, I'm getting FFMPEG set up so I can stream to Twitch.tv and I think I'm really close, just getting an error when I try to start streaming.  The error I get is
```
/usr/share/avconv/libx264-medium.avpreset: Invalid option or argument: 'preset=medium', parsed as 'preset' = 'medium'
```

The code I'm using to set up FFMPEG is
```
ffmpeg -f x11grab -s "$INRES" -r "$FPS" -i :0.0+0,0 -itsoffset 00:00:01 -f alsa -ac 2 -i pulse  -vcodec libx264 -vpre "$QUAL" -s "$OUTRES" -acodec libmp3lame -ab 96k -threads 2 -qscale 5 -b 1024kb -f flv "rtmp://live.justin.tv/app/$STREAM_KEY"
```

I'm following this tutorial on youtube. [http://www.youtube.com/watch?v=whRvUrEWA34](http://www.youtube.com/watch?v=whRvUrEWA34)

I think I'm really close but there's an issue with the preset.  I'm fairly new to Linux and any help would be great.  Also if there's a better way to stream please point me in the right direction.  Thanks!

---

### Post by dswanson32 on 2014-02-19
Ok so using another script I was able to get the stream to run but now I can't actually see the stream on Twitch.  It says it's live but nothing loads.  Here's the script.
```
#! /bin/bash

# streaming on Ubuntu via ffmpeg.
# see http://ubuntuguide.org/wiki/Screencasts for full documentation

# input resolution, currently fullscreen.
# you can set it manually in the format "WIDTHxHEIGHT" instead.
INRES="1680x1050"

# output resolution.
# keep the aspect ratio the same or your stream will not fill the display.
OUTRES="1280x720"

# input audio. You can use "/dev/dsp" for your primary audio input.
INAUD="pulse"

# target fps
FPS="30"

# video preset quality level.
# more FFMPEG presets avaiable in /usr/share/ffmpeg
QUAL="medium"

# stream key. You can set this manually, or reference it from a hidden file like what is done here.
STREAM_KEY="my stream key here"

# stream url. Note the formats for twitch.tv and justin.tv
# twitch:"rtmp://live.twitch.tv/app/$STREAM_KEY"
# justin:"rtmp://live.justin.tv/app/$STREAM_KEY"
STREAM_URL="rtmp://live.twitch.tv/app/$STREAM_KEY"

ffmpeg \
-f alsa -ac 2 -i "$INAUD" \
-f x11grab -s "$INRES" -r "$FPS" -i :0.0 \
-vcodec libx264 -s "$OUTRES" -vpre "$QUAL" \
-acodec libmp3lame -threads 6 -qscale 5 -b 64KB \
-f flv -ar 44100 "$STREAM_URL"

```

UPDATE:  My broadcast even shows up in the recent broadcasts on Twitch, it just doesnt stream live.

---

