---
title: "HOWTO: Download / convert youtube video to music"
date: 2010-03-30
forum: Multimedia Software
---

### Post by opt1k on 2010-03-30
These are the instructions for streaming a youtube video with ffmpeg and converting it to mp3 without physically downloading it to your hard disk.




> 
#1 Download and install latest youtube-dl

[http://packages.debian.org/search?keywords=youtube-dl&searchon=names&suite=unstable&section=all](http://packages.debian.org/search?keywords=youtube-dl&searchon=names&suite=unstable&section=all)

#2 Download and install ffmpeg

sudo apt-get install -y ffmpeg

#3 Enter one command

 ffmpeg -i `youtube-dl -b -g $YOUTUBE_URL` -f mp3 -ab 160k -ar 44100 -ac 2 $FILENAME.mp3

EXAMPLE:
 ffmpeg -i `youtube-dl -b -g http://www.youtube.com/watch?v=H0DTm_bWEjs` -f mp3 -ab 160k -ar 44100 -ac 2 Scooter_vs_Status_QUO-Jump_that_rock.mp3

#4 To only download the movie with no conversion:

youtube-dl -b [http://www.youtube.com/watch?v=H0DTm_bWEjs](http://www.youtube.com/watch?v=H0DTm_bWEjs)




Simple Script
> 
#!/bin/bash
#
# requires ffmpeg / youtube-dl
# simple gui for: 
# ffmpeg -i `youtube-dl -b -g http://www.youtube.com/watch?v=H0DTm_bWEjs` # -f mp3 -ab 160k -ar 44100 -ac 2 asdf.mp3


FN=Scooter_vs_Status_QUO-Jump_that_rock
URL=http://www.youtube.com/watch?v=H0DTm_bWEjs

echo "
Enter full youtube video URL here
EX:  [http://www.youtube.com/watch?v=H0DTm_bWEjs](http://www.youtube.com/watch?v=H0DTm_bWEjs)
"
echo -n "> "
read URL
echo "
Enter name of file
EX: Scooter vs Status QUO -Jump that rock
"
echo -n "> "
read FN

echo "
Ok so we are downloading 
from: $URL and converting 
to: $FN.mp3
"
echo "
This may take a while, be patient....
"
ffmpeg -i `youtube-dl -b -g "$URL"` -f mp3 -ab 160k -ar 44100 -ac 2 "$FN".mp3

echo "
All Done
"

sleep 5



---

### Post by lovinglinux on 2010-03-30
There are several threads being locked because downloading YouTube videos is against their EULA. I would advice reporting your own thread to a moderator and asking for review.

---

