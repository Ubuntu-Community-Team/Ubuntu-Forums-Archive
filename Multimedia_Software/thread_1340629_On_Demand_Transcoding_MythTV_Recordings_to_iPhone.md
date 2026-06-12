---
title: "On Demand Transcoding MythTV Recordings to iPhone"
date: 2009-11-28
forum: Multimedia Software
---

### Post by mrdek11 on 2009-11-28
I've been trying different ways to get my MythTV recordings streamed to my iPhone. Until today, I simply had a bash script that used ffmpeg to transcode specific recordings and used apache2 to serve them to the iPhone.

However, Today I decided to try transcoding the videos on demand. I set up a php page to run the ffmpeg transcode, and I assumed that I could simply point my iPhone to the url of the file and it would let me watch while it transcoded. (I guess I'm too used to VLC.)
When I tried this, I was informed that the iPhone could not play this video format.

I examined the HTTP headers and saw that the ETAG of the in-progress video had "w/" before it, whereas complete videos did not. Could the solution be as simple as fixing this?

I was hoping that I could just transcode the videos on demand, and delete the transcoded versions after a few hours. (Because storing two versions of every episode eats up storage)

Is there any way to do this?

Thanks in advance,
Derek

[edit]I found this: [http://www.ioncannon.net/programming/452/iphone-http-streaming-with-ffmpeg-and-an-open-source-segmenter/](http://www.ioncannon.net/programming/452/iphone-http-streaming-with-ffmpeg-and-an-open-source-segmenter/)
But it seems to only be of use when you have the completed video, but do not want people to be able to download it; rather than for streaming the video as the transcoding progresses.

Note: Below is the script I am using to transcode the files:
```

#!/bin/bash
#MythIPod v.1 http://www.chiefhacker.com/                                                 
#Copyright 2007 Chris Lorenzo et al                  
#This software is licensed under the CC-GNU LGPL <http://creativecommons.org/licenses/LGPL/2.1/> 
#Additionally modified 2007 Doug Johnson

if [ ! $# == 2 ]; then
  echo "Usage: $0 directory file"
  exit
fi

directory="$1";
file="$2";

#Get the video information
video_info=`mplayer -vo null -ao null -frames 10 -identify "${directory}/${file}" 2>/dev/null`

#Command line grep sucks, but we make due...
aspect=`echo $video_info | egrep -oe "Movie-Aspect is [0-9:.]+" | egrep -o "[0-9:.]+"`
framerate=`echo $video_info | egrep -oe "[0-9.]+ fps" | egrep -o "[0-9.]+"`

# set resolution by aspect ratio

if [ "$aspect" == "1.78:1" ]
then
  width=432
  height=240
  vbitrate=480k
else
  width=480
  height=360
  vbitrate=378k
fi

abitrate=128k

# Figure out which AAC we have
AAC=$(ffmpeg -v 2>&1|sed "s/--enable-/\n/g"|grep aac|awk '{print $1}')
if [ "x${AAC}" = "xlibfaac" ]
then
	ACODEC="-acodec libfaac"
else
	ACODEC="-acodec libfaac"
fi

# Create the MP4

ffmpeg -i "${directory}/${file}" $ACODEC -ab ${abitrate} -ac 2 -s ${width}x${height} -vcodec mpeg4 -b ${vbitrate} -flags +aic+mv4 -mbd 2 -cmp 2 -subcmp 2 -g 250 -maxrate 512k -bufsize 2M "${directory}/${file}.mp4"

```
[/edit]

---

### Post by mrdek11 on 2009-11-29
It seems that the problem is not the fault of the iPhone, but rather that I didn't understand how ffmpeg works. I assumed that it would transcode the file sequentially, leaving behind it a file that vlc could view.

Is there a way to transcode a video in this way?

Thanks,
Derek

[edit]It sounds like ffserver does what I want to do, but I can't find any "working" configuration for it from mpeg to h264.[/edit]

[edit2]I think I may have just made a semi-major breakthrough on this. I was able to get it working using vlc: ```
cvlc -vv 2013_20090917180000.mpg --sout '#transcode{width=320,canvas-height=240,vcodec=mp4v,vb=768,acodec=mp4a,ab=96,channels=2}:standard{access=file,mux=mp4,dst=out.mp4}'
```
The iPhone can stream/play this file perfectly, as long as VLC isn't currently running. (ie, it works even if I kill VLC prematurely).

vlc won't even play the file while it's still being transcoded, it gives:
```
mp4 demux error: MP4 plugin discarded (no moov box)
[mov,mp4,m4a,3gp,3g2,mj2 @ 0xa1652b0]moov atom not found
```

I'm hoping there's a way to keep it from getting this "moov box" error while still transcoding, and if so, everything should work right!

On an alternate note, I was able to get it running using: ```
cvlc -vv 2013_20090917180000.mpg --sout '#transcode{width=320,canvas-height=240,vcodec=mp4v,vb=768,acodec=mp4a,ab=96,channels=2}:std{access=http,mux=ts,url=:8080}'
``` and I could connect via ```
vlc http://localhost:8080
```
However, the iPhone says it cannot download that file. Is there a way to view a video stream via the iPhone?

Does anybody have any ideas for either option?

Thanks again,
Derek
[/edit]

---

