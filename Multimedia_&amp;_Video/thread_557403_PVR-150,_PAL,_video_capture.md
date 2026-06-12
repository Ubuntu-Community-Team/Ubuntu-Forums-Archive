---
title: "PVR-150, PAL, video capture"
date: 2007-09-22
forum: Multimedia &amp; Video
---

### Post by gheywood on 2007-09-22
Hello,

This works fine if I do **CAT /dev/video0 > file.mpg **but I would like to extend this by setting bit rates, aspect, and putting a time limit on the capture. 

I thought **mencoder** would be the solution, but while Ubuntu may "just work", I am not having the same luck getting mencoder to work. The resulting capture is grey, and grainy. Bascially I think mencoder is still capturing in NTSC no matter what switches I try. 

Can anyone help me out? Has anyone got a working .CONF file for doing something similar to what I have? 

I have been working on a couple of profiles shown here:


[ivtv]
tv=normid=10:norm=PAL:device=/dev/video0:width=720:height=576
pvr=abitrate=192:vbitrate=2200000:vpeak=2600000:fmt=ps:aspect=2:arate=32000
of=mpeg=1
mpegopts=format=dvd
ofps=25
ovc=copy=1
oac=copy=1 
vf=harddup=1

[ivtv2]
tv=norm=PAL:device=/dev/video0:width=720:height=576
pvr=abitrate=192:vbitrate=2200000:vpeak=2600000:fmt=DVD:aspect=2:arate=32000
of=mpeg=1
mpegopts=format=dvd
ofps=25
ovc=copy=1 
oac=copy=1
vf=harddup=1 

And using this command line:

mencoder pvr:// -profile ivtv -o encode.mpg -endpos 20



IF mencoder doesn't work, can anyone suggest a better method??

---

### Post by gheywood on 2007-09-22
OK, got it working (kind of). 

I have the following in my ~\.mplayer\mencoder.conf file (hope I got that path right):

[ivtv]
tv=norm=0:device=/dev/video0:width=720:height=576
pvr=abitrate=192:vbitrate=2200000:vpeak=2600000:fmt=ps:aspect=2:arate=32000 
of=mpeg=1
mpegopts=format=dvd
ofps=25
ovc=copy=1
oac=copy=1
vf=harddup=1

Then on the command line, run:

mencoder pvr:// -profile ivtv -of mpeg -o encode.mpg -endpos 20


Only problem now, is that the audio is out of sync... Any suggestions??

---

### Post by gheywood on 2007-09-23
OK, has anyone done this with VLC?

I was led to believe that ripping from my Sky box to a Linux box would be easy. 

How can it be so hard to copy a stream from my TV, in PAL, with audio and video in sync, and to record for a set period of time (ie two hours). 

I have been trying to get this working for weeks and at the moment, am wondering why I bothered to be honest. There are loads of extra's that an ubuntu box can do, but if it cannot even do the basics, it is useless to me..

So if mencoder can't do it, does anyone know either:

1) A command line to get VLC to only record for a set amount of time (I couldn't find one)
2) A different way which works) which would allow VLC to stop or be terminated after a certain period of time but still create a valid file?

I thought that recording from a TV source for a certain period of time would be a common thing to do? :confused:

---

### Post by benow on 2007-11-27
Well, I came upon this thread checking for a way to ensure encoded is MPEG2 compliant, and will modify your suggestion.

Currently, I cap with ```
cat /dev/video0 > file.mpeg
```, and I've written a script which bg's the cat, sleeps for a period of time then does a ```
killall cat
```.  It works well and might suit your needs.  

```

# directory to capture to
CAP="/archive/incoming/cap"

# final output directory
OUT="/archive/incoming"

CHAN=$1
FILE=$2
DURATION=$3
DATE=`date +%d-%m-%y`

if [ -z $3 ]; then
  echo "Usage: $0 <channel> <filename> <duration in s>"
  exit -1
fi;

mkdir -p $CAP 2> /dev/null

BASENAME=$CAP/$FILE.$DATE
if [ -e "$BASENAME.mpeg" ]; then
   DATE=`date +%d-%m-%y.%H:%M`
fi;
BASENAME=$CAP/$FILE.$DATE

# set input (0=tuner, 1=svideo, 2=composite)
v4l2-ctl --set-input 1

# change channel
#bin/chchan $CHAN

# stop captures 
killall -9 cat 2> /dev/null

# begin capture
cat /dev/video0 > $BASENAME.mpeg &
echo Recording $DURATION minutes from $CHAN to $BASENAME.mpeg

# wait
sleep ${DURATION}m

# end capture
killall -9 cat 2> /dev/null

# trim commercials
#bin/comdel $BASENAME.mpeg

# reencode
#bin/enc $BASENAME.mpeg $OUT/$FILE.$DATE.mp4

```

As you can see, it relies on v4l2-ctl to set the input... you might want to put something in to ensure it's capping in PAL.  I use (the commented) bin/chchan to change channel via lirc, bin/comdel to trim commercials and bin/enc to encode to mp4.  If you want the source to those, reply.  I've built up a decent pvr around these scripts.

Hope this helps... better late than never.

---

### Post by gheywood on 2007-12-09
That looks great! How well does the commercial trimming work? Is that included, or something that needs to be dowloaded?

---

### Post by benow on 2007-12-09
this is bin/comdel:
```

#!/bin/bash

VID=$1
if [ -z $VID ]; then
  echo "Usage: $0 <mpeg_video>"
  echo "Deletes commecials from mpeg_video, overwriting original"
  exit -1
fi;

BASE=${VID%.*}
DESC=`file "$VID"`
if [ 1 -eq `echo "$DESC" | grep "MPEG sequence" | wc -l` ]; then 
  echo is mpeg video, generating skip list
  bin/comskip "$VID"

else 
  echo isnt mpeg video
  echo $DESC
  if [ 1 -eq `echo "$DESC" | grep "video:" | wc -l` ]; then

    echo re-encoding... 
    mencoder -of mpeg -oac lavc -ovc lavc -lavcopts vcodec=mpeg2video:vbitrate=500 -o "$BASE.mpeg" "$VID"
    echo "Generating skiplist of reencoded: $BASE.mpeg"
    bin/comskip "$BASE.mpeg"
    echo "Removing reencoded"
    rm "$BASE.mpeg"
    
  else
    echo "Doesn't seem to be a video file."
    exit -1
  fi;
fi;

echo "Trimming $VID"
mencoder -of mpeg -oac copy -ovc copy -edl $BASE.edl -o "$VID.trim" "$VID" && \
mv "$VID.trim" "$VID"

```

and the bin/comskip wrapper script

```

#!/bin/bash
wine var/applications/comskip/comskip.exe --ini etc/comskip.ini $*

```

It works with [comskip](http://www.kaashoek.com/comskip/) under wine to spit out an edl (Edit Descision List) which is then used by mencoder to recombine without commercials.  It works very well... atached is my comskip ini (zipped due to attachment restrictions), which is about 95% effective at junk trimming with the stuff I've captured.  Comdel also re-encodes to mpeg if the source file is not an mpeg.  Because mencoder trims and does not re-encode, there is no loss in fidelity, which is quite awesome.

My only current irritation with the cat recording method is that the mpeg is not dvd complient... meaning that a re-encode is needed to convert the captured video to something that can be read from a standalone dvd player... ie sharing with or recording for friends.  There might be a way around that by using mplayer's new pvr:// recording mode to record with dvd complience.  If so, then the [tovid](http://tovid.wikia.com/wiki/Main_Page) scripts could be used to master a dvd, and the system ([jivo](http://benow.ca/admin/project/index.page?op=view&key=12), my own homebrew listings/pvr thing) could lightscribe a description.  I'm sure I'll sort it eventually.

If you're not overly concerned with mpeg complience or would like to save space, the cat captured mpeg can be re-encoded to mp4 without much loss of fidelity, but with quite a savings in space.  Here's the bin/enc script I use to do that:
```

#!/bin/bash

IN=$1
OUT=$2

if [ -z $OUT ]; then
  echo "Usage: $0 <infile> <outfile>"
  echo "Reencodes a given file to mp4"
  exit -1
fi;

echo "Encoding: $IN to: $OUT"

mencoder "$IN" \
        -really-quiet -fps 30000/1001 \
        -ovc x264 -x264encopts pass=1:bitrate=1500:turbo=1:threads=2\
        -oac copy\
        -o /dev/null

mencoder "$IN" \
        -really-quiet -fps 30000/1001 \
        -ovc x264 -x264encopts pass=2:bitrate=1500:threads=2\
        -vf harddup \
        -oac mp3lame \
        -o "$OUT" 

```

Lemme know of issues or questions.

---

### Post by gheywood on 2007-12-10
Well I did get mencoder working with the PVR thing (apart from AV sync). Maybe I can modify your script to incorporate it. Most of it is way, way, way over my head, but I will try it and see how I get on.


Cheers

---

