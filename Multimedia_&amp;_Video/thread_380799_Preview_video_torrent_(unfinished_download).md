---
title: "Preview video torrent (unfinished download)"
date: 2007-03-10
forum: Multimedia &amp; Video
---

### Post by dowoshek on 2007-03-10
Hello,
I'm just trying to open and watch .avi file. The problem is - it was not completly downloaded (using torrent), but i have more than 90% of it. VLC doesnt work at all, MPlayer crash after 12 sec. Is there any way to fix it? Maybe sb could suggest an appropriate application?
Will be grateful for any help.

---

### Post by RomeReactor on 2007-03-10
Hi. This is from the [Wikipedia page]("http://en.wikipedia.org/wiki/Audio_Video_Interleave") on .avi files:

> The first sub-chunk is identified by the "hdrl" tag. This sub-chunk is the file header and contains metadata about the video, such as its width, height and frame rate. The second sub-chunk is identified by the "movi" tag. This chunk contains the actual audio/visual data that make up the AVI movie. The third optional sub-chunk is identified by the "idx1" tag which indexes the physical addresses [within the file] of the data chunks.

So, in essence, if a .avi video file is missing the last chunk of the file (the "idx1" tag), it will likely not be able to read beyond the first completed part of the file; most of the time, if it's missing the first chunk (the "headers"), it will not read it at all. I realize this in no way answers your question (sorry), and i could be wrong, but just wanted to provide some sort of explanation as this has been my experience with incomplete video files. My only suggestion is to wait until it's finished downloading, if it's still available.

---

### Post by dowoshek on 2007-03-10
Unfortunetly, it's not unavailable and it seems it won't be in the future too.

I've found an application DivFix ([http://gnomefiles.org/app.php/DivFix_Plus_Plus)](http://gnomefiles.org/app.php/DivFix_Plus_Plus)), that maybe could do sth with my issue, but unfortunetly I can't make install it properly :(

---

