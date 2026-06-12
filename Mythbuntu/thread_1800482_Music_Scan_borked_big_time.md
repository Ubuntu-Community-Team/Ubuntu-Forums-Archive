---
title: "Music Scan borked big time"
date: 2011-07-09
forum: Mythbuntu
---

### Post by GuiGuy on 2011-07-09
Music scanning never finishes; the music scan is reading in literally 10s of thousands of directory names, but none are circular references. It reads these into music_directories. 

I have now isolated the frontend/ backend and so at least it is not scouring all over the network.

It started at / and now we're into lib64/modules/2.6.35-28-generic/build/include/config/fs/posix some one hour and 60000 directory names later. And still going.

I can't do anything from Utilities > Setup > Media Settings > Music because it starts scanning immediately.

WTF??

Thanks

---

### Post by matthias.rieber on 2011-07-13
had a similar problem before...
Mythmusic has problems, if there are files starting with <space> or have too much empty characters in. 
I named all music like "album_artist_track_title.mp3" filled in with mp3-tag-editor
Now, if some albums are unknown - or album name is " beginners" instead of "beginners" - mythmusic-search hangs and will never finish (I killed mythfrontend after 72hours).
After changing all names (bulk renaming) musicsearch uses 20min to search for 25.000 titles over network (I stored my music on nas).
 
hope this helps....

---

