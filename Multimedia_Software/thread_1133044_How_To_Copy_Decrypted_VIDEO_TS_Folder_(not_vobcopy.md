---
title: "How To Copy Decrypted VIDEO_TS Folder (not vobcopy)"
date: 2009-04-22
forum: Multimedia Software
---

### Post by mankyd on 2009-04-22
I'm curious if there exists a Linux variant of the Windows DVD Decrypter program. I would like to copy the raw video files from a DVD to a my hard drive so that I can work with them. All I want is to decrypt the files (i.e. copy the contents of video_ts to my hard drive.) I do not want to transcode or alter the data in any way.

I tried vobcopy, but something about the way it combined the data together caused my programs to hang up near the end of the video. When I went to a windows machine, ran dvd decrypter, and copied the results back over to my linux machine, everything worked flawlessly. Anyone know of a simple command line program to do this? I've done quite a bit of searching and everyone keeps recommending programs that do transcoding, not raw copies.


EDIT: Solved

the -m parameter to vobcopy solved my problems.

---

