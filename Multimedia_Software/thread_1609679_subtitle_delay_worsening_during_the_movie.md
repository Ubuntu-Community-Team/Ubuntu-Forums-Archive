---
title: "subtitle delay worsening during the movie"
date: 2010-10-30
forum: Multimedia Software
---

### Post by simormate on 2010-10-30
I start watching a movie with vlc or smplayer, I adjust the subtitles to fit the movie. But while the movie is going on, the subtitles are getting late more and more, so I should adjust it all the time, making it impossible to watch it.
It happened with more movies, so it's not a particular movie's problem.

---

### Post by P4man on 2010-10-30
You probably dont have the correct .srt subtitles (I assume thats what we are talking about). find a better one or synchronize them yourself with gnome subtitle editor.

---

### Post by simormate on 2010-10-31
> **P4man said:**
> You probably dont have the correct .srt subtitles (I assume thats what we are talking about). find a better one or synchronize them yourself with gnome subtitle editor.

Thanks for your answer. Yes, they are .srt files. I don't think this is the problem: it happens with several subtitles for the same movie, and also with several movies. It looks as if time counting would be slower for the subtitles than the movie - thats why it is not possible to adjust it.

---

### Post by P4man on 2010-10-31
its easy to check. Just open the srt file in a text editor and see if the time stamps in them correspond with actual times. Since VLC and SMplayer share nothing, it would really surprise me if the problem was with the players rather than your srt's. Some srt's are made for 25fps others for 23.96 or whatever fps, so they will play incorrectly with a 25fps rip.

---

### Post by yugo4k on 2011-01-22
This thread's a bit old, but I'm having the same problem and can't find anyone who's fixed it.

It happens to just a few .mkv files, in both Totem and VLC. In VLC I'm able to adjust the subtitle delay so that the audio and subtitle fit... but the delay keeps increasing over time.

The thing is, the .srt times are right... but both programs seem to "slow it down", so that I have to keep increasing the subtitle delay throught the file. Curious that it happened in just 2 of the 50 files I've seen. Which makes me think the problem is with the files somehow.

Has anyone else seen this?... or knows how to fix it?

---

