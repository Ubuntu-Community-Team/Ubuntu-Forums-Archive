---
title: "gstreamer can no longer find plugins"
date: 2010-03-28
forum: Multimedia Software
---

### Post by Truthiswithin on 2010-03-28
Up until recently I have had no problem playing all kinds of video in Ubuntu.  I recently upgraded to Lucid and I can't remember if I was able to play videos after that, but yesterday I found that I am unable to play flv or MP4 videos in either totem or vlc.  Converting them to ogv using ffmpeg allows them to play just fine, and I can edit the flv and mp4 in Avidemux, so there is nothing wrong with the files themselves.  Not sure what I've done, can't seem to find a bug in launchpad for this, so I am assuming it is a problem with my setup somehow.  Anyone willing to help?

---

### Post by no2498 on 2010-03-28
you may try getting, smplayer
and or gstreamer ugly

---

### Post by Truthiswithin on 2010-03-29
I'm sorry, I didn't make it clear, I have all gstreamer plugins, including good, bad, ugly and their multiverse counterparts.

I don't know if it is a part of the problem, but mplayer gives the following error when trying to play an flv video:

> mplayer: error while loading shared libraries: libopencore-amrnb.so.0: wrong ELF class: ELFCLASS32

I have tried reinstalling libopencore-amrnb0, to no end.

---

### Post by Truthiswithin on 2010-03-29
Okay, I built libopencore-amrnb0 from source and now mplayer and vlc are playing the videos fine.  totem is still asking permission to search for every video codec from XVID to H.264, and it is finding none.

---

### Post by Truthiswithin on 2010-04-19
Okay, I somehow fixed it... first I deleted (moved) all gstreamer files I could find on the system, then purged all of the gstreamer packages using dpkg --force-all --purge and then reinstalled them.  That didn't work right away, but then I found out that it was only that one user who had a problem, so I removed the ~/.gstreamer-0.10 folder (which I had done previously to no avail) and when it rebuilt the database, all was well.

Thanks for the help, sorry to be a bother.

---

