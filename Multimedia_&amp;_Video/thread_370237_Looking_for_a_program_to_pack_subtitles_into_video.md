---
title: "Looking for a program to pack subtitles into video files"
date: 2007-02-25
forum: Multimedia &amp; Video
---

### Post by F-3582 on 2007-02-25
Hi,

At the moment I'm busy encoding some of my DVDs into smaller formats. I mainly use the x264+aac codec inside an MP4 container for this. I read that these support subtitle streams and I'd really like to know how to put a subtitle file (srt, for example) into such a container. And no, I won't hardsub my precious movies :D I'm interested in softsub solutions, only.

---

### Post by shirilover on 2007-02-25
It should be possible to import an srt subtitle file using the -add option of mp4box.
However, I do not know if this will give you your desired result.
Another option would be to use mkvtoolnix to create mkv files which will have softsubs.

---

### Post by F-3582 on 2007-02-26
Works like a charm. Thanks a lot.

By the way: In order to actually see these subtitles you need either VLC or the very latest subversion snapshot of MPlayer. The 1.0rc1 doesn't do that, yet.

---

