---
title: "Ffmpeg help convert video"
date: 2009-04-13
forum: Multimedia Software
---

### Post by elliotn on 2009-04-13
1. I am trying to convert a .vob to mpg

I did the following  [QUODE]cd Desktop
(Desktop is were my vob file is)

ffmpg -i gafield.vob gafield.mpg

Then I get this error. File or directory not found[QUOTE]
 2. I downloaded a youtube video, using ./tmp copying trick. But file has no extention like the others but it shows as a video file. Is it suppose to be like that

---

### Post by cotcot on 2009-04-13
1. Have you put the directory path before gafield.vob ?

2. check youtube-dl to get a [[COLOR="Red"]youtube[/COLOR]]("http://manpages.ubuntu.com/manpages/intrepid/man1/youtube-dl.1.html") clip; the extension is normally .flv

---

### Post by bumanie on 2009-04-13
You probably haven't got the correct path. You could try winff which is a GUI to ffmpeg, that may be easier.

---

### Post by FakeOutdoorsman on 2009-04-13
VOB is based on MPEG-2 and most players will play them just fine if you rename the file extension to mpg.

---

