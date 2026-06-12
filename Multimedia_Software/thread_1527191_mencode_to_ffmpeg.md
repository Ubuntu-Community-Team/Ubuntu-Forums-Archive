---
title: "mencode to ffmpeg"
date: 2010-07-09
forum: Multimedia Software
---

### Post by I8NY on 2010-07-09
okay i have been using video4fuze to convert my videos because sandisk doesn't convert a thing.  video4fuze is great but fails sometimes in h.264 videos from handbrake.(menconder bug)  video4fuze uses menencoder and i have the settings it uses so i'm hoping some one could convert it to ffmpeg settings to use in WinFF. ```
mencoder  -msglevel all=0:statusline=5 -ofps 20 -ovc lavc -lavcopts vcodec=mpeg4:vqscale=3:keyint=15  -vf field,expand=:::::224/176,scale=224:176,harddup -srate 44100 -af resample=44100:0:1,format=s16le -oac mp3lame -lameopts cbr:br=128
```The Fuze player is very picky to the video settings.

---

