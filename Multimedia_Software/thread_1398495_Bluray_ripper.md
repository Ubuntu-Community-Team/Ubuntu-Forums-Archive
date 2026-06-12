---
title: "Bluray ripper"
date: 2010-02-04
forum: Multimedia Software
---

### Post by AmbiguousOutlier on 2010-02-04
Is it possible to install a bluray ripper via the terminal that can be used via the terminal? 

I'm using xbmc and from what I've read it's not possible in the frontend.

---

### Post by AmbiguousOutlier on 2010-02-04
Will this work in xbmc live?

run this in the terminal;

```

$ sudo apt-get install mencoder mplayer gpac x264 mkvtoolnix

```


then create a file called “encodevideo.sh” with the following;

```

#! /bin/bash

# =====================================================================
# Blu-ray encoding script by HyRax February 2009 http://www.serenux.com
# =====================================================================

# Make sure the user has specified what to work on.
if [ -z "$1" ]; then
  echo "\nBlu-ray movie encoding script\n-----------------------------"
  echo "Written by HyRax February 2009\nhttp://www.serenux.com"
  echo "\nUsage: $0 <m2ts file without extension>"
  echo "\nExample: If your movie file is called TheDarkKnight.m2ts then\nyour usage will be: $0 TheDarkKnight\n"
  exit
fi

# The crf=21 option controls encoding quality, and indirectly the final
# filesize. The higher the value, the more compression and thus smaller
# file size. Reduce the value and file size will go up. A value of 21
# should produce a file of approximately 4GB in size for a typical movie.

# Encode the video using x264, ignore the audio for now.
mencoder $1.m2ts \
-ovc x264 -x264encopts crf=21:frameref=3:bframes=3:b_pyramid:direct_pred=auto:weight_b:partitions=all:8x8dct:me=umh:mixed_refs:trellis=1:nopsnr:nossim:subq=6:level_idc=41:threads=2 \
-nosound \
-of rawvideo \
-o $1.x264

# Dump the first original audio track (should be the English track) but
# don't re-encode it. Ignore the video.
mplayer $1.m2ts -dumpaudio -dumpfile $1.ac3

# Copy the raw x264 encoded video into an MP4 container so we can set
# the correct framerate (generally 23.976 - adjust it if MPlayer or
# MEncoder report something different)
MP4Box -add $1.x264 $1.mp4 -fps 23.976

# Finally, merge everything into a single MKV file
mkvmerge -o $1.mkv $1.mp4 --track-name 0:Eng $1.ac3

# Remove the hash in front of the next command to have the script delete
# your working files when encoding is complete.
# rm $1.m2ts $1.x264 $1.ac3

# Tell the user we're done.
echo "All done! Your final movie file is called $1.mkv - enjoy!"

```

Then copy to home folder.

Change to what ever directory contains the m2ts file;

```

$ cd ~/Videos/BDRips/MyMovie

```


then encode using this code assuming the film is called TheIsland

```

$ sh ~/encodevideo.sh TheIsland

```

Obviously I now need to figure out how to extract the m2ts file. So questions are will this work in xbmc and will xbmc play the mkv file with the relevant codecs installed?

---

