---
title: "Movie Player with .srt does too much I/O"
date: 2008-11-14
forum: Multimedia Software
---

### Post by Krieg on 2008-11-14
This is with Hardy.   

When I try to play a movie with a .srt subtitle file, when the file is opened, Movie Player does tons of I/O before starting the movie.  The files are in a SMB share and this makes the smbd process in the other machine to take the whole processor.   Movie Player takes about 1 minute to open the file.

stracing the smbd in the other side I can see that the .srt is being accessed thousands and thousands of times before the playing actually starts.

If I remove the .srt file then everything is OK and the file is played immediately.

---

### Post by lovinglinux on 2008-11-14
The default Movie Player takes a lot of time to load here too, but gnome-mplayer and smplayer load fine. Have you tried one of these?

---

