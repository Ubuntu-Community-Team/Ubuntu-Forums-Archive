---
title: "Mencoder and sound"
date: 2007-01-01
forum: Multimedia &amp; Video
---

### Post by tzulberti on 2007-01-01
Hi. I am having a problem when I use mencoder to capture the tv. The command I use is the following:
mencoder -tv driver=v4l2:width=640:height=480:norm=pal-nc:input=2:chanlist=us-cable:channel=12 -ffourcc DIVX -fps 25 -ovc lavc -lavcopts vcodec=mpeg4:vhq -oac mp3lame -lameopts cbr:br=128 -endpos 2 -o outfile.mpg tv://

But I have a beep sound in the background. Does anyone has any clue of what it could be happening?

---

