---
title: "Convert video from bin to avi"
date: 2007-01-09
forum: Multimedia &amp; Video
---

### Post by fernando_lopes_jr on 2007-01-09
I have a video file that's in bin format  is an svcd of a movie what I want to do is to convert it in to avi.thanks

---

### Post by adarkmethod on 2007-03-08
i too could really use some help here. I've got a ton of movies backed up on my HD to .bin,cue format, but i cant seem to find anything that works for either burning them to DVD again or converting them to mpeg or avi to burn.
anyone got any suggestions?

---

### Post by dbd on 2007-03-18
Not sure about converting them, but mplayer can play them without any problems.

---

### Post by airtonix on 2007-03-18
mmm, bin/cue is like iso. 

your goal here will be to extract the actual video file from this disc image(bin/cue).

But first you need to convert the BIN/CUE combo to an ISO
 to do this there is a program in the repos called [B]bchunk
 [/B]```
sudo apt-get install bchunk
```then you want to grab the .DAT file from one of the folders....it will be tha largest file in the image.

Failing that you can try using vcdimage or vcdtools from the repos to deal with the BIN/CUE files......
```
sudo apt-get install vcdimage vcdtools
```or you can just play them bin file with VLC, MPLAYER or TOTEM

---

### Post by Patrick-Ruff on 2007-03-20
VLC is awesome . . .

thanks for the info ;).

---

### Post by thagoat on 2007-04-15
To convert the bin/cue to dvd-compatible mpeg files, first change the extension on the.bin to .avi. Then you can use Manencode to convert the file to a dvd compliant mpeg2 file. Then burn away!! I use this process myself and it works great!

---

### Post by pagingmrherman on 2008-01-13
Since nobody answered your question (and someone misspelled mencoder), here's the answer:


******** TYPE THIS IN **********
sudo wajig install mencoder
mencoder -o MovieNameHere.avi -of avi -ffourcc DX50 -lavcopts vbitrate=900:vhq -ovc lavc -oac mp3lame -vf pp=lb MovieNameHere.bin

---

