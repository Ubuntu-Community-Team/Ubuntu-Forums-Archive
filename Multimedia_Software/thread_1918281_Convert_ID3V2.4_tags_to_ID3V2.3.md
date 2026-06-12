---
title: "Convert ID3V2.4 tags to ID3V2.3?"
date: 2012-01-31
forum: Multimedia Software
---

### Post by callmebruce on 2012-01-31
I have an older feature phone (not a smart phone) that has an MP3 player in it. I added a MicroSDHC card to it and added some 1200 songs. Artist and Album info did not work - so I used EasyTag. That corrected some 750 or so MP3's. I then used MusicBrainz Picard and got the list of unknown albums and artists down to 360. I ran MP3 Diag to clean up tags, then researched songs and got the list to 104 unknown.

Genre was not working - so I cleaned that up automatically for some mp3s and manually for others (using the apps above and Banshee). However - some mp3's that are tagged correctly are not showing up under Genre. I ran eyeD3 on some good mp3's and some bad mp3's - and saw that my mp3 player seems to support ID3V2.3 format but not ID3V2.4 (at least the songs that list correctly are in 2.3 format, and the songs that show up as unknown are in 3.4 format)'

What's a good tool to to change ID tags from 2.4 to 2.3?

---

### Post by callmebruce on 2012-01-31
EasyTag did the trick. I just set my default tag to 2.3, went through each directory and it automagically saved the tags in 2.3 format. I used eyeD3 to manually view some files - and they changed from 2.4 to 2.3 just like that!

---

### Post by samfuzz on 2012-02-06
you can also try mp3diag:
[http://mp3diags.sourceforge.net/010_getting_the_program.html](http://mp3diags.sourceforge.net/010_getting_the_program.html)

---

