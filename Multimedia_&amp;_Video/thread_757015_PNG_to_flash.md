---
title: "PNG to flash"
date: 2008-04-16
forum: Multimedia &amp; Video
---

### Post by dravidan on 2008-04-16
II would like to convert bunch of PNG image to a flash movie.  I was able to convert them to a avi movie by using the following command:

mencoder mf://*.png -mf w=401:h=411:fps=10:type=png -ovc copy -oac copy -o myavi.avi

Now I am trying to convert the avi to a flash by this command:

ffmpeg -i myavi.avi -f flv -s 320x240 myflv.flv

but I get a error message:

[avi @ 0xb7f8c5d0]Could not find codec parameters (Video: MPNG / 0x474E504D, 401x411)
junk.avi: could not find codec parameters

The resolution of my avi is 401x411.

---

