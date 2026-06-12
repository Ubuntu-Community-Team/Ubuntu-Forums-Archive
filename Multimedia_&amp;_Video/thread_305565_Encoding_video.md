---
title: "Encoding video"
date: 2006-11-23
forum: Multimedia &amp; Video
---

### Post by cjhardie on 2006-11-23
I recently used a script for changing video formats to mp4 so i could put it on my ipod.  Here is the scrpt:

#!/bin/bash

base=`echo $1 | gawk -F. '{print $1}' `

echo "$1 $base"

vlc -vvv "$1" :sout="#transcode{vcodec=mp4v,vb=1024,scale=1,acodec=mp4a,ab=128,channels=2}:standard{access=file,url=$base.mp4}" vlc:quit --aspect-ratio "4:3" --sout-transcode-width 360 --sout-transcode-height 240 --sout-transcode-fps 30

After it was done the movie worked, but without sound.  Think anybody could tell me why that happened???

Thanks

---

### Post by malcolm1234 on 2006-12-03
I've had the same problem ([here]("http://ubuntuforums.org/showthread.php?p=1838551")).

When I open the converted file in VLC and go to View, Stream and Media Info it lists 2 streams, both of which are video. Seems very strange to me - anyone got any ideas? Or another simple way of doing transcoding from divx/realplayer/wmv files to mp4 files?

---

