---
title: "How to record tv from command line (without mythtv)"
date: 2007-11-08
forum: Multimedia &amp; Video
---

### Post by Blackie_Chan on 2007-11-08
This is how I record TV without installing mythtv.

1. Get mencoder

```
sudo apt-get install mencoder
```

2. Create the script (record.sh): 
```

#!/bin/sh

# Duration of recording (in seconds)
DURATION=$1

CHANNEL=$2

# Filename (excluding extension)
FILE=$3\.avi

# Record from tv
mencoder tv:// -tv driver=v4l2:device=/dev/video0:channel=$CHANNEL:forceaudio:norm=NTSC-M:chanlist=us-cable:alsa:adevice=hw.0,0:immediatemode=0 \
               -ovc xvid -xvidencopts bitrate=800 \
               -oac pcm \
               -endpos $DURATION -sws 1 -o $FILE


```

3. Make the script executable and run it: 

```
chmod u+x record.sh
./record.sh 3600 3 heroes
```

Cheers.

---

