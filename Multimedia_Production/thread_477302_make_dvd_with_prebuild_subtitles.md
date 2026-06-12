---
title: "make dvd with prebuild subtitles"
date: 2007-06-18
forum: Multimedia Production
---

### Post by Doojek9 on 2007-06-18
Hi all.

I'm trying to create a DVD file and to add subtitle to it (in srt format). The problem is that the srt file contains Hebrew characters and the closest I got is a DVD with subtitles but not in the correct encoding I think.

Here's how I did it:

Using tovid I ran this command:

tovid -subtitles sub.srt -pal -dvd -in movie.avi -out movie.mpg

after extracting the audio, tovid ran this command:

nice -n 0 mplayer -noconsolecontrols -benchmark -nosound -noframedrop -sub "/home/"sub.srt"" -vo yuv4mpeg:file="/home/movie.mpg.0/video.yuv" -vf scale=720:576 "/home/movie.avi"

Again, the result was m2v file with prebuild subtitles but with characters not encoded correctly.

Thanks.

---

