---
title: "Great audio converter: flac2mp3"
date: 2007-12-17
forum: Multimedia &amp; Video
---

### Post by mozetti on 2007-12-17
Yesterday I was staring at the gigs & gigs of flac music files I had sitting on my hard drive and despairing at the amount of time it was going to take me to convert them to mp3 (my format of choice for my iRiver H340).

Then I came across [flac2mp3](http://bytemonkey.org/projects/flac2mp3/). It's a great little BASH script that uses the flac & LAME packages to automagically convert your flac files to mp3, mimicing the directory structure.

The command-line inputs are very simple:```
$ ./flac2mp3 <input directory> <output directory>
```

In my setup, I basically have a "to-do" folder and a "new-mp3" folder so that I can manually enter the tags to fit to my method of organizing music. Enough of my descrptions though, I'll let the project speak for itself: > flac2mp3 has the following features: 

-- Mimics the directory structure of your FLAC files and maintains the same filenames. 
-- If a target MP3 already exists, flac2mp3 will skip to the next file. You may run flac2mp3 again whenever you add more FLACs to your collection. 
-- The FLAC decode process is checked for failures, and will be re-executed if necessary. (FLAC is flaky on Asus Athlon A7V133 mainboards, this side-steps the problem) 
-- It will (optionally) copy .jpg artwork files into the MP3 target directory.

I hope this helps some of you out there.

---

