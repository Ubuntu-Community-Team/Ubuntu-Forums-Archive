---
title: "converting .ogg"
date: 2007-11-03
forum: Multimedia Production
---

### Post by 127.0.0.1 on 2007-11-03
Hello people of the ubuntu forums! i have been trying to post a youtube video of ubuntu 7.10, because i like my desktop settings and i like to brag and on the internet i can get away with it :) 

theres just one problem, youtube dosen't support .ogg files. so i need to convert .ogg to a .avi, or .mpg, or any other supported file type by youtube, i have tried using iriverter but i lose video quality significantly. Is there a way to convert with out losing video quality?

---

### Post by Creative2 on 2007-11-03
hi... maybe search in the forum before next time ?

xD well there is this converter for linux 

[http://ubuntuforums.org/showthread.php?t=567016](http://ubuntuforums.org/showthread.php?t=567016)

if you don t want install it , look the page the same you can find your conversion command-line for mencoder 

cheers

---

### Post by eye208 on 2007-11-05
> **127.0.0.1 said:**
> Is there a way to convert with out losing video quality?
No, because YouTube video quality sucks by default.

But at least you can save some upload time by generating a video file that YouTube will accept without transcoding. YouTube uses FLV (Flash Video) at 320x240, 22.05kHz mono MP3 sound. Just download any clip from YouTube that you think looks good, then analyze its format specs using MPlayer. Then use MEncoder or FFMPEG to convert your own .ogg video to exactly that format.

I did this a few weeks ago with one of my videos, and YouTube did not touch the stream data at all. You'll get a chance to see what your video will look like on YouTube prior to the actual upload. And the file to upload will be small.

---

### Post by lunaz on 2008-06-10
how do you use mplayer to get the specs from a downloaded youtube video?

---

### Post by Creative2 on 2008-06-11
i use  ffmpeg for that 

ffmpeg -i INPUTFILE 2>&1 | grep Stream

---

