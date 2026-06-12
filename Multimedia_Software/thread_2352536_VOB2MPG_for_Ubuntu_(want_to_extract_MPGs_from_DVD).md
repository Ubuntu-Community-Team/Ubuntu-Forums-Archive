---
title: "VOB2MPG for Ubuntu (want to extract MPGs from DVD)"
date: 2017-02-13
forum: Multimedia Software
---

### Post by johnsmoke on 2017-02-13
I'm looking for a way to extract mpg files from a DVD. Essentially I have a DVD of something where I want to extract the mpg files so that I can make a new fully authored DVD of the video. I want to extract mpg's from the VOB files so that I lose no quality in the process. VOB2MPG did this in Windows, can someone please help me do this in Ubuntu?

---

### Post by johnsmoke on 2017-02-14
Never mind, I found an easy command-line that does this with ffmpeg, perfect! - 
ffmpeg -i input.vob -c:v copy -c:a copy output.mpg

---

