---
title: "Mencoder: Too many video packets in the buffer"
date: 2010-03-18
forum: Multimedia Software
---

### Post by mister_playboy on 2010-03-18
I used the record feature in VLC to record a section of a DVD.  The file plays fine in VLC and mplayer, but seek doesn't work in mplayer because it apparently has retained the index of the DVD.  I cannot successfully rebuild the index with ```
mencoder vlc-record-2010-03-18-09h07m03s-DVDVolume-.mpg -forceidx -ovc copy -oac copy -noskip -o file.mpg
``` because I get "too many video packets in buffer" errors and the resulting file has video that plays much too slowly.

Is their a way to increase the buffer size?  Since I'm simply copying the streams rather than encoding anything, it seems ridiculous that the buffer isn't large enough.

Is there a better way of doing this?

---

