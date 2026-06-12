---
title: "WMV Support?"
date: 2009-02-05
forum: Mythbuntu
---

### Post by serapis5 on 2009-02-05
Hi all...

Hoping someone can help me with what I think is my final hurdle for my myth box.  It's the only one I can't seem to find anything related on.  I have my mythbox in the living room with both back and front-end installation.  Everything is humming along quite nicely except...I have a lot of family videos in WMV format.  When I click on them to play, I can hear the audio, but no video.  If I leave the front-end and play the videos through vlc or any other, they play just fine.  Mpeg videos play just fine as do dvds, etc.  I realize that we're dealing with a proprietary codec here, and I've installed the gstreamer plugins good, bad and ugly, but is there a package I have overlooked related specifically to the Myth front-end?

Thanks

---

### Post by ian dobson on 2009-02-05
Hi,

You can add the w32_codecs or w64_codecs through the Mythbuntu configuration programm. Sorry I can't say exactly which menu option it is but it only takes afew seconds to find,insall,configure.

Regards
Ian Dobson

---

### Post by newlinux on 2009-02-05
If for some reason adding these codecs through mythbuntu-control-centre don't work, you could always configure mythvideo to launch vlc or mplayer or your player of choice to play these files. You can specify on a file by file basis or a file type (e.g. wmv). I've found a few files that no matter what codecs I have installed, myth's internal player has a problem with them, and I end up using mplayer for those.

---

### Post by serapis5 on 2009-02-06
Thanks Ian and Newlinux.  I thought I had installed the w32 codecs through control center when I  first installed, but I will double check.  Just glad I wasn't being completely insane.  If they are there, I'll take the bait and convert them to mpeg as well, but configure vlc to launch for any future wmv's.  Just didn't want to if I didn't have to.  I really appreciate the quick responses.

---

