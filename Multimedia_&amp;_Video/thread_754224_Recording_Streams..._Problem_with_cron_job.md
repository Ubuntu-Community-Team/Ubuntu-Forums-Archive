---
title: "Recording Streams... Problem with cron job"
date: 2008-04-13
forum: Multimedia &amp; Video
---

### Post by lambono on 2008-04-13
Hi guys,
I really hope someone can help me out with this...

I have a script to record radio streams from the net. It dumps the streams using mplayer then converts it to MP3 using LAME.
I can invoke this script as follows and it works fine 

./script.sh name3 15 [http://mediasrv.musicradio.com/Chill](http://mediasrv.musicradio.com/Chill) ""
or
./script.sh radio 15 [http://www.bbc.co.uk/radio1/realaudio/media/r1live.ram](http://www.bbc.co.uk/radio1/realaudio/media/r1live.ram) "-playlist"

however if I try to run this as a cron job it dumps the stream but the conversion fails!
I set the permissions of the recording directory to 777.

Any ideas!? 


Script 
```

#!/bin/bash

SHOWNAME=$1
DURATION=$2
STREAMADDRESS=$3
PLAYLISTOPTION=$4

RECORDINGPATH=/home/recordings/


mplayer -dumpstream "$PLAYLISTOPTION" "$STREAMADDRESS" -dumpfile "$RECORDINGPATH$SHOWNAME".dump -vc dummy -vo null &
MPLAYPROCESS=$!
sleep $DURATION
kill $MPLAYPROCESS

echo "Finished Recording. Start Conversion..."

mkfifo "$RECORDINGPATH$SHOWNAME.pipe"
lame "$RECORDINGPATH$SHOWNAME".pipe "$RECORDINGPATH$SHOWNAME".mp3 & mplayer -quiet -vc dummy -vo null -ao pcm:file="$RECORDINGPATH$SHOWNAME".pipe "$RECORDINGPATH$SHOWNAME".dump

rm "$SHOWNAME".pipe
rm "$SHOWNAME".dump

```

---

### Post by lambono on 2008-04-13
Here is the output log 

```

MPlayer 2:1.0~rc1-0ubuntu13.2+medibuntu1 (C) 2000-2006 MPlayer Team
CPU: Intel(R) Pentium(R) 4 CPU 3.00GHz (Family: 15, Model: 3, Stepping: 4)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
Resolving www.bbc.co.uk for AF_INET6...
Resolving www.bbc.co.uk for AF_INET...
Connecting to server www.bbc.co.uk[212.58.251.207]: 80...
Cache size set to 320 KBytes
Terminal type `unknown' is not defined.

Playing rtsp://rmlive.bbc.co.uk/bbc-rbs/rmlive/ev7/live24/radio1/live/r1_dsat_g2.ra?BBC-UID=7418b052e6ea804269e5e3ae9080109817bb56c520c00124744f09bff61e79f2_n&SSO2-UID=.
Resolving rmlive.bbc.co.uk for AF_INET6...
Resolving rmlive.bbc.co.uk for AF_INET...
Connecting to server rmlive.bbc.co.uk[212.58.227.96]: 554...
Cache size set to 320 KBytes
Finished Recording. Start Conversion...
MPlayer 2:1.0~rc1-0ubuntu13.2+medibuntu1 (C) 2000-2006 MPlayer Team
CPU: Intel(R) Pentium(R) 4 CPU 3.00GHz (Family: 15, Model: 3, Stepping: 4)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
Terminal type `unknown' is not defined.

Playing /var/www/shell_scripts/s/cron.dump.
REAL file format detected.
Stream description: Audio Stream
Stream mimetype: audio/x-pn-multirate-realaudio-live
```

---

### Post by ron999 on 2008-04-13
Hi
To convert the dumped file to mp3 no need to bother making a fifo pipe file. You can use ffmpeg instead with a pipe symbol "|".
Just try using commands like this:-
 
```
echo "Finished Recording. Start Conversion..."

ffmpeg -i "$RECORDINGPATH$SHOWNAME".dump -f wav - | lame - "$RECORDINGPATH$SHOWNAME".mp3

rm "$RECORDINGPATH$SHOWNAME".dump

```

You don't even need to use LAME at all, you can use ffmpeg on its own (though LAME might be a better/faster encoder than ffmpeg, I don't know).
```
echo "Finished Recording. Start Conversion..."

ffmpeg -i "$RECORDINGPATH$SHOWNAME".dump "$RECORDINGPATH$SHOWNAME".mp3

rm "$RECORDINGPATH$SHOWNAME".dump

```

---

### Post by lambono on 2008-04-14
Thanks for the tip!
Ill try that out...

---

### Post by lambono on 2008-04-14
Doesnt Seem to work for an asx stream

```
 ffmpeg -i stream.dump stream2.mp3
FFmpeg version SVN-rUNKNOWN, Copyright (c) 2000-2007 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-swscaler --enable-pthreads --enable-libvorbis --enable-libtheora --enable-libogg --enable-libgsm --enable-dc1394 --disable-debug --enable-libmp3lame --enable-libfaadbin --enable-libfaad --enable-libfaac --enable-xvid --enable-x264 --enable-liba52 --enable-amr_nb --enable-amr_wb --enable-shared --prefix=/usr
  libavutil version: 1d.49.3.0
  libavcodec version: 1d.51.38.0
  libavformat version: 1d.51.10.0
  built on Dec 20 2007 21:25:50, gcc: 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)
Input #0, asf, from 'stream.dump':
  Duration: 00:00:04.9, start: 0.000000, bitrate: 164 kb/s
  Stream #0.0: Audio: wmav2, 44100 Hz, mono, 32 kb/s
  Stream #0.1: Audio: wmav2, 44100 Hz, mono, 48 kb/s
  Stream #0.2: Audio: wmav2, 44100 Hz, stereo, 64 kb/s
  Stream #0.3: Audio: wmav2, 32000 Hz, mono, 20 kb/s
Output #0, mp3, to 'stream2.mp3':
  Stream #0.0: Audio: mp3, 32000 Hz, mono, 64 kb/s
Stream mapping:
  Stream #0.0 -> #0.0
Press [q] to stop encoding
size=       1kB time=0.1 bitrate=  64.0kbits/s    
video:0kB audio:1kB global headers:0kB muxing overhead 0.000000%

```

---

### Post by ron999 on 2008-04-14
Yes, ffmpeg doesn't seem to work with an asx stream.:(
Back to the drawing board....

I see that you're using stream.dump instead of assigning a name to the dumped stream, that's good.
Try it again using a fifo pipe like this:-

```
echo "Finished Recording. Start Conversion..."
mkfifo stream.wav
mplayer stream.dump -vc null -vo null -ao pcm:file=stream.wav & lame stream.wav "$RECORDINGPATH$SHOWNAME".mp3
rm stream.wav
rm stream.dump
```

---

### Post by lambono on 2008-04-14
Think im starting to narrow this down. 

I have created a new thread at 
[http://ubuntuforums.org/showthread.php?p=4715042#post4715042](http://ubuntuforums.org/showthread.php?p=4715042#post4715042)

Please post there instead of here.

Thanks again for your help!

---

