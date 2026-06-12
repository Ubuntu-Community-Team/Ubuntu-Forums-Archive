---
title: "ffmpeg won't read AAC -- or, how to use mencoder on audio-only input"
date: 2011-12-03
forum: Multimedia Software
---

### Post by w9wi on 2011-12-03
I've got a smartphone that records audio notes in AAC files.  I'd like to be able to convert them to something I can edit with Audacity/post on sites where people who can't read AAC hang out/etc...

Not having any luck.

mplayer will *play* the files just fine.  However, mencoder won't transcode them.  I get "Video stream is mandatory!".  The -novideo, -vo null, and -vc null options don't matter, it still demands a video stream.  (or are those functions for if I don't want audio in the *output* file?)

ffmpeg yields "Unsupported codec (id=86018) for input stream #0.0".  But the faad codec *is* installed according to Synaptic.  (it *isn't* installed, according to "ffmpeg -formats".)  How do I convince ffmpeg this codec actually exists?

I've tried ["FakeOutdoorsman"'s solution]("http://ubuntuforums.org/showthread.php?t=1117283&highlight=convert+aac+file+mp3"), step C (I'm using Hardy); there are no errors, everything appears to install -- but ffmpeg still doesn't see the codec.

It's sounding like if I want to take audio notes in the future, I should use the camcorder function & hold my finger over the lens:)

Thanks!

---

### Post by andrew.46 on 2011-12-04
> **w9wi said:**
> mplayer will *play* the files just fine.  However, mencoder won't transcode them.  I get "Video stream is mandatory!".  The -novideo, -vo null, and -vc null options don't matter, it still demands a video stream.  (or are those functions for if I don't want audio in the *output* file?)

The source code of MPlayer ships with a small script called aconvert.sh which might help out here:

```

#!/bin/sh

# Author: Jonas Jermann
# Description: A hack to allow mencoder to encode from an audio only file

if [ "$1" = "" ]; then
    echo "Usage: $0 <\"input file\"> <\"output file\"> <\"options\">"
    exit 0
fi

options=${3:-"-oac mp3lame"}

mencoder -demuxer rawvideo -rawvideo w=1:h=1 -ovc copy -of rawaudio -endpos `mplayer -identify $1 -frames 0 2>&1 | grep ID_LENGTH | cut -d "=" -f 2` -audiofile $1 -o $2 $options $1

```

> ffmpeg yields "Unsupported codec (id=86018) for input stream #0.0".  But the faad codec *is* installed according to Synaptic.  (it *isn't* installed, according to "ffmpeg -formats".)  How do I convince ffmpeg this codec actually exists?

Sounds a little odd, can you post the full command and uncut terminal output?

---

### Post by MoreOrLess on 2011-12-04
[http://readlist.com/lists/mplayerhq.hu/ffmpeg-user/1/6263.html](http://readlist.com/lists/mplayerhq.hu/ffmpeg-user/1/6263.html)

---

