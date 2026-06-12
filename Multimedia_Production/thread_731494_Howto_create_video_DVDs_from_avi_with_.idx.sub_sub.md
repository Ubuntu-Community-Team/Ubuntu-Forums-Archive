---
title: "Howto: create video DVDs from avi with .idx/.sub subtitles"
date: 2008-03-21
forum: Multimedia Production
---

### Post by diagonallemma on 2008-03-21
I recently found myself trying to burn a DVD from an avi file with subtitles in vobsub format (.idx/.sub). The question has come up a few times here and elsewhere, but I couldn't find an easy solution. So I spent a few hours taking cues from different places and came up with the following. Perhaps it's of some use to somebody else.

mencoder doesn't support the -vobsub option yet, which is why neither mencoder nor frontends such as DeVeDe will help us. We have to first play the movie with mplayer, setting the -vobsub flag, and record the output with mencoder, via a named pipe. Then we convert the resulting mpeg file to a DVD iso with dvdauthor and mkisofs.

Unfortunately, it seems that the mplayer => mencoder transfer doesn't work with the current version of mplayer, 1.0rc2. You'll get an error message about a missing dll, but that's a red herring. The easiest workaround is to install 1.0rc1, which you can get from [http://www.mplayerhq.hu/MPlayer/releases/]("http://www.mplayerhq.hu/MPlayer/releases/"): Extract the source code to some folder and run "./configure" and "make" from there. This will give you a file in the same folder called mplayer.

I wrote a little script to automatize the remaining steps. You can save this as dvdiso and call it e.g. with

 ```
dvdiso low 3000 movie
```

where "movie" is the filename of your avi, idx and sub files, without the suffix. "low" stands for lower quality and faster encoding (alternative: "high"), "3000" is the video bitrate, which determines the size of the iso. While mencoder runs, you can see a file called tmp_video.mpeg growing: if that grows beyond DVD size, you might cancel the script and start over with a lower bitrate. (Or use DeVeDe first to find a suitable bitrate.)

Here's the script. Hope it comes across okay, otherwise I've also uploaded it to here: [http://www.umsu.de/misc/dvdiso]("http://www.umsu.de/misc/dvdiso")

```

#!/bin/bash

# create dvd-iso from avi with .idx/.sub subtitles
# requires: ffmpeg, dvdauthor, mkisofs, mencoder, mplayer
USAGE="Usage: dvdiso [hi|low] <bitrate (e.g. 3000)> <input filename without suffix>"

# This script doesn't work with MPlayer 1.0rc2! 1.0rc1 is fine, and can be installed locally:
MPLAYER=~/install/MPlayer-1.0rc1/mplayer

if [ $# -ne 3 ]; then
  echo $USAGE
  exit 1
fi

QUALI=$1
BITRATE=$2
INFILE=$3

# detect movie aspect:
aspect=`ffmpeg -i $INFILE.avi 2>&1 | grep "Stream\ #0.0"`
aspect=`echo "$aspect" | sed "s/.* \([1-9][0-9]*\)x\([0-9]*\).*/\10000 \/ \2/"`
aspect=$(( $aspect ))
if [ $aspect -gt 20639 ]; then
  echo ">>> padding panavision to widescreen"
  aspect="16/9"
  scale="scale=720:432,expand=720:576"
elif [ $aspect -lt 15555 ]; then
  aspect="4/3"
  scale="scale=720:576"
else
  scale="scale=720:576"
  aspect="16/9"
fi
echo ">>> aspect: $aspect"

# mencoder options:
DVDFORMAT="-ovc lavc -of mpeg -mpegopts format=dvd:tsaf -vf $scale,harddup -ofps 25"
AUDIO2CHAN="-srate 48000 -af lavcresample=48000 -oac lavc -lavcopts acodec=ac3:abitrate=192"
if [ $QUALI = 'hi' ]; then
  QUAL="-lavcopts vcodec=mpeg2video:vrc_buf_size=1835:vrc_maxrate=9800:vbitrate=$BITRATE:keyint=15:aspect=$aspect:trell:mbd=2:precmp=2:subcmp=2:cmp=2:dia=-10:predia=-10:cbp:mv0:vqmin=1:lmin=1:dc=10:vstrict=0"
else
  QUAL="-lavcopts vcodec=mpeg2video:vrc_buf_size=1835:vrc_maxrate=9800:vstrict=0:vbitrate=$BITRATE:keyint=15:aspect=$aspect:vstrict=0"
fi

# create named pipe and convert avi to mpeg with subtitles:
if [ -e stream.yuv ]; then
  rm stream.yuv
fi
mkfifo stream.yuv
echo '>>> creating audio track tmp_audio.wav'
$MPLAYER "$INFILE.avi" -dumpaudio -dumpfile tmp_audio.wav
echo '>>> converting avi to mpeg with vobsub subtitles'
$MPLAYER "$INFILE.avi" -vobsub "$INFILE" -nosound -noframedrop -vo yuv4mpeg </dev/null & 
sleep 10
mencoder stream.yuv -audiofile tmp_audio.wav $DVDFORMAT $QUAL $AUDIO2CHAN -o tmp_video.mpeg
jobs
sleep 20
rm tmp_audio.wav
rm stream.yuv

# create iso:
if [ -e tmp_video.mpeg ]; then
  echo ">>> something went wrong: no tmp_video.mpeg found. Try a different MPlayer version?"
  exit
fi
echo ">>> creating dvd iso"
dvdauthor -o ./tmp_dvd/ -t tmp_video.mpeg
dvdauthor -o ./tmp_dvd/ -T
rm tmp_video.mpeg
mkisofs -dvd-video -o "$INFILE.iso" ./tmp_dvd
rm -r ./tmp_dvd

echo ">>> done."

```

I'm an amateur about all this, so there are probably much better ways to go about it, but at least this works for me (on Ubuntu 7.10).

---

