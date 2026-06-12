---
title: "I'm finding a GUI for NeroAacEnc"
date: 2009-02-21
forum: Multimedia Software
---

### Post by psychok9 on 2009-02-21
After a lot of days and tries, I've found a great encoder AAC Plus (for low bitrates).
I've modified a script for take the mp3 and convert it to wav and to m4a.
```
#!/bin/bash
TEMPFILE=/tmp/neroaac-$RANDOM
## sox -x -s -w -t raw -r 44100 -c 2 "$1" -w $TEMPFILE.wav
ffmpeg -i "$1" $TEMPFILE.wav -ar 44100 -ac 2
neroAacEnc -br 56000 -if $TEMPFILE.wav -of $TEMPFILE.mp4
neroAacTag $TEMPFILE.mp4 -meta:title="$3" -meta:artist="$4" -meta:comment="$5" -meta:track="$6" -meta:album="$7" -meta:year="$8"
mv $TEMPFILE.mp4 "$2"
rm $TEMPFILE.wav
```

Now the problem is that u'm finding a GUI for this script or neroAacEnc... because It work 1 file at time...
It's better if can set the correct tag from mp3: on wave conversion I lost the mp3 tag!.

---

