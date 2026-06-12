---
title: "Create DIVX containers from AVI files with srt subtitles included (for ps3)"
date: 2008-03-25
forum: Multimedia &amp; Video
---

### Post by SuppoTaalasmaa on 2008-03-25
With DLNA server in the network, I use PS3 to stream all my videos to the living room, and now that with the newest firmware PS3 supports subtitles in divx containers, I would like to remux them in.

I was wondering how to convert the existing AVI containers to DIVX with srt file inside the container ? 
I'm guessing this could somehow be done with mencoder, but I can't seem to get the subtitles not be hard coded. 
I also don't want to re-encode the video nor audio if possible, since PS3 is really picky about the video/audio..

I've tried this, but it doesn't add the subtitle file:
```
mencoder filename.avi -oac copy -ovc copy -o outputfilename.divx -sub dmd-themist-cd1.srt 
```

Thanks!

---

### Post by NHaGa on 2008-03-27
I would also like to get a solution for this...

---

### Post by gsmanners on 2008-03-27
I think I would try using avidemux, and you might have more success with an mp4 file than trying to do an avi file.

---

