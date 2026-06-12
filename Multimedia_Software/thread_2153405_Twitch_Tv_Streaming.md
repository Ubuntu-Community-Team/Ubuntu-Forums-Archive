---
title: "Twitch Tv Streaming"
date: 2013-06-11
forum: Multimedia Software
---

### Post by sci4me on 2013-06-11
Hey guys. So I have a script that I regularly stream to twitch tv with and I just tried to use it and it started giving this error:
```

[x11grab @ 0xf3ef20] Could not open X display.
:0.0+,: Input/output error

```
I haven't been able to fix it at all. Here is the script:
```

#!/bin/bash
INRES="1600x900" 
OUTRES="1280x720" 
FPS="60" 
QUAL="fast" 
STREAM_KEY=$(cat ~/.twitch_key) 


avconv -f x11grab -s "$INRES" -r "$FPS" -i :0.0 -ab 192k \
	-f alsa -ac 2 -i pulse -vcodec libx264 -crf 30 -preset "$QUAL" -s "1280x720" \
	-vol 11200 -acodec libmp3lame -ar 44100 -threads 0 \
	-f flv "$URL"

```
Why would a script randomly stop working??? And more importantly, how can I fix it?

---

