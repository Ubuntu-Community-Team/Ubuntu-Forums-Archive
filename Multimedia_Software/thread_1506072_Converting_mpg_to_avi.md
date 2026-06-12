---
title: "Converting mpg to avi"
date: 2010-06-09
forum: Multimedia Software
---

### Post by nemodot on 2010-06-09
I'm having some problem converting an mpg file to avi.
I did it with mencoder.

The result was an avi file as I wanted but the image was like stretched vertically. Like this:

[IMG]http://i.imgur.com/8kip0.jpg[/IMG]

(The avi is on the left)

What can I do to convert it without the stretching?

---

### Post by cosine352 on 2010-06-10
try 'ffmpeg'

> sudo apt-get install ffmpeg
then this code 
> ffmpeg -i file.mpg -vcodec wmv2 -sameq -acodec wmav2 -f asf -fs 100 file.avi

you can look at the man page for the ffmpeg for more details.

---

