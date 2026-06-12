---
title: "totem and rhythmbox"
date: 2006-01-09
forum: Multimedia &amp; Video
---

### Post by borisattva on 2006-01-09
this is not realy a request for support, more like a rant / request to help better understand a neuance in the world of linux.

it is somewhat stemming from the ["how to replace totem with mplayer"]("http://ubuntuforums.org/showthread.php?t=76946&highlight=mplayer+embedded") thread, but it is also a trail  off and i didnt wnat to rain on all the glory taht thread has.

i was able to remove and install mplayer smoothly using synaptics.
thats not a probelm.

my problem is why did removing TOTEM cost me Rhythmbox as well?
admitedly neither application is perfect, but they are just about the best linux has right now.
in the sense of a manageable and searchable music library Rhythmnbox actually appears to be the ONLY choice.
TOTeM on the other hand seems to fit gnome aesthetics well and plays all files i throw at it (with proper codecs installed) and even embeds player windows in firefox, my only grudge against it is it cant play anything embedded in such windows, instead producing error or worse yet killing the browser all together.

now i'm sitting here, able to browse fine, and can even play embedded videws (albeit annoyingly in a seperate popup window), and i dont have the versatility of music library control that is gone with rhythm box,

and some how it doenst feel like it should be that way. so why is it?

---

### Post by mackinax on 2006-03-12
Are we talking about dependency hell? 
(Would repairing the package dependencies (needed by Rhythmbox ... *there seems to be a ton of them*), that were apparently broken by removing Totem, then cause MPlayer to break?)

---

### Post by doclivingston on 2006-03-12
Rhythmbox doesn't depend on Totem per se, it depends on totem-plparser. In Dapper that is in a separate binary package, so you can uninstall Totem and leave Rhythmbox installed - however I'm not sure if it's separate in Breezy.

---

