---
title: "The audio device is unavailable"
date: 2007-09-01
forum: Multimedia &amp; Video
---

### Post by bricksen on 2007-09-01
After todays kernel device upgrade I get this message when trying to play .avi files with xine.

"The audio device is unavailable. Please verify if another program already use it"

Well it doesn't and both xmms and vlc plays without trouble but xine worked beautyfully until this upgrade.

What happened??

---

### Post by bricksen on 2007-09-01
It seems its only one movie that doesn't work with xine....
messages:
xine:found input plugin: file input plugin
xine:found demuxer plugin: AVI/RIFF demux plugin
xine:found input plugin: file input plugin
xine:found demuxer plugin: Elementary MPEG stream  plugin
xine:found input plugin: file input plugin
xine:found demuxer plugin: sputex demuxer plugin
xine_play:no demux available
cideo_out:throwing away image with pts 41772 because it's too old (diff:6485)
cideo_out:throwing away image with pts 44772 because it's too old (diff:3485)
cideo_out:throwing away image with pts 53772 because it's too old (diff:3541)
xine:found input plugin: file input plugin
xine:found demuxer plugin: Elementary MPEG stream  plugin
xine_play: no demux available

Why? it works in Vlc??? Is it a codec in xine that it can't find??

---

