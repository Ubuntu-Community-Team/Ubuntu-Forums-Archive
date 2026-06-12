---
title: "Make DVD that will play on a TV"
date: 2014-10-21
forum: Multimedia Software
---

### Post by Bill_McConnell on 2014-10-21
I want to make a simple DVD for use on a TV, using pictures as content.   i don't need background music or special framing.  If I can include movie clips, thatwould be even better.  Can anyone recommend a software package for this task?

---

### Post by kc1di on 2014-10-21
I use DeVeDe it's in the repository. It will convert multiple formats to dvd. good luck.

---

### Post by SeijiSensei on 2014-10-21
You might need to convert the images to a video stream before burning it to a disc.  I haven't used DeVeDe in a while, but I believe it expects a video file as input.

You can [use ffmpeg to create a video from still frames]("https://trac.ffmpeg.org/wiki/Create%20a%20video%20slideshow%20from%20images"), then use DeVeDe to burn the file to DVD.  For "political" reasons, Ubuntu distributes the "libav" fork of ffmpeg rather than the program itself.  If libav doesn't work for this task, you can install the actual ffmpeg from [here](https://launchpad.net/~jon-severinsson/+archive/ubuntu/ffmpeg).

---

### Post by Bill_McConnell on 2014-10-21
Thanks for the help.  These two tools sound like the combination that I am looking for.

---

### Post by kc1di on 2014-10-22
Good Luck hope it all works for you :)

---

