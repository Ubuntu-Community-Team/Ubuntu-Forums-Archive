---
title: "Video/mp3 not playing within Firefox (screenshots attached)"
date: 2006-12-05
forum: Multimedia &amp; Video
---

### Post by jsully1 on 2006-12-05
Hi all,

I have mplayer installed, as well as mozilla-mplayer obviously, but whenever I try to play any sort of embedded media - clicking on an mp3 file or trying video on CNN.com or apple trailers, I get a black window that say (no video).   Here are some screenshots:

[img]http://mr2.phpwerx.net/Photos/Sully/stuff/full/novideo1.png[/img]

[img]http://mr2.phpwerx.net/Photos/Sully/stuff/full/novideo2.png[/img] 

Ytmnd doesn't play audio either, thought that's really the least of my concerns :)

Sully

---

### Post by jsully1 on 2006-12-05
Well 5 seconds later I solved it by deleting the VLC plugin, libvlcplugin.so.  It seems Firefox was defaulting to that and wasn't giving good old mplayer a chance.  Hopefully this is helpful to the next person!

---

### Post by pay on 2006-12-05
Good work;)

---

### Post by the_dark_light on 2007-09-10
Deleting other plugins (such as totem) from the usr/lib/firefox/plugins and installing the mplayer plugin helped my feisty system, so thanks guys (and gals, if present)

Only problems I've found are that on YTMND (the reason I tried for so long to get the plugins resolved) the audio doesn't loop (which I kinda prefer, as that was an annoying "feature") and audio being truncated.  ("No more Mr nice Gaius" is truncated to "no more mr nice gaiu")

---

