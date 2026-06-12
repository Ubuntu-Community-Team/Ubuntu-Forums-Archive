---
title: "Rhythmbox won't play the first track of several .mp3 albums"
date: 2010-08-26
forum: Multimedia Software
---

### Post by immerohnegott on 2010-08-26
I've been experiencing an odd issue since I upgraded my main desktop to Lucid - namely, that the first track on several albums doesn't appear in the Rhythmbox library. The rest of the album will show up and play just fine. I installed Exaile to see if it was just a Rhythmbox bug, and the tracks appear in the library, but will not play (it just skips through the whole track, as it would if the MP3 codec isn't installed or configured correctly). Did a clean install of Lucid yesterday, which was also of no help.

The files are all .mp3, non-VBR encoding (320kbps, IIRC...not that it should really matter). They are stored in an NTFS partition I use to share data between Windows XP and my Linux installs. 

Funny thing is, the tracks show up and play just fine in XP and on OpenSuse 11.3 (KDE version). It also works fine on my laptop, which is also dual-booting XP and Lucid, with the tunes stored on the Windows partition.

I tried switching out the MP3 codecs and whatnot, but nothing seems to help.

Any ideas?

---------UPDATE----------

Just got around to installing Amarok on the machine, which plays the songs just fine. This is evidently a Gstreamer bug.

---

### Post by immerohnegott on 2010-08-27
Another update (and a bump).

Went into the folders containing the non-playing tracks, and for some reason Nautilus is telling me they are video files (Video tab in Properties instead of Audio), with N/A listed under all the codec information, with a size of 0x0 and length of 0 seconds.

Perhaps it's just some kind of data corruption?

---

