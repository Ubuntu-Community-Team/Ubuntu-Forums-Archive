---
title: "mencoder script help"
date: 2007-08-15
forum: Multimedia Production
---

### Post by sleepercivic88 on 2007-08-15
```
#!/bin/bash
               mencoder -vf rotate=1,crop=480:360:0:80 -oac pcm -ovc lavc *.AVI -o Rotated

```

I made a little script that runs well.  I motorcycle vlog and my cam is mounted sideways in my helmet.  This rotates it and crops it to 4:3 aspect ratio(chops off the section of chin bar=>wanted to on purpose).  

My question is how would I modify the script to split up the file every 10min of playback time.  

also what would I add to compress it to 1000 bit/sec mpeg 4 video with 128 mp3 audio.

thanks.

---

