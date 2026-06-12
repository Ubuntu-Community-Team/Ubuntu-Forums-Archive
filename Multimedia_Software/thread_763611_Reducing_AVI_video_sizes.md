---
title: "Reducing AVI video sizes"
date: 2008-04-23
forum: Multimedia Software
---

### Post by avantgardaclue on 2008-04-23
I have just finished recording our family's cine collection from the 1960s. I used a fuji digital camera and i can confirm that it did a wonderful job.

The camera recorded as AVI. However, it strikes me that these AVI files are huge... about 60 MB per minute of recording. A 10 minute film ended up at 642 MB (640 x 480 @ 30 fps). By using FFMPEG i can convert these to MPEG at about 20% original size using the 'sameq' tag, ie 642 MB AVI converts to 128 MB mpeg.

I am sure i have seen AVI files much much smaller than this for this sort of duration and dimension, and consequently the 20% MPEG files would be proportionally smaller. 

I was hoping to get all these films on one CD for distributing around the family, but the way it stands at the moment there's no chance of this happening!!

Any advice gratefully received... thanks

---

### Post by TenPlus1 on 2008-04-23
Pop onto [www.getdeb.net](www.getdeb.net) and search & download a program called Avidemux...

This will allow you to open any movie (so long as you have the codec installed) and re-compress the video (mpeg4xvid) and audio (mp3) and resize it so that it will save a smaller sized .avi file of that movie...  btw, when it asks to unpack movie, say no...

---

### Post by nicedude on 2008-04-23
Those are huge since most movie rips in Xvid or Divx format are 700 MB for a full movie. I would just try the program the first person suggested and see what you can squeeze them down to. How are you wanting to distribute them to your family when you say CD do you mean as data files? If stored as data on a disc then you should be able to shrink 10min videos to at least somewhere around 70mb apiece meaning you could fit 10 or so on a CD.

---

### Post by loell on 2008-04-23
also try mencoder,

```
mencoder -idx huge_size.avi -ovc lavc -oac mp3lame -o output.avi 
```

---

### Post by avantgardaclue on 2008-04-23
> **TenPlus1 said:**
> Pop onto [www.getdeb.net](www.getdeb.net) and search & download a program called Avidemux...

This will allow you to open any movie (so long as you have the codec installed) and re-compress the video (mpeg4xvid) and audio (mp3) and resize it so that it will save a smaller sized .avi file of that movie...  btw, when it asks to unpack movie, say no...

Hi tenplus1, i happen to have 'avidemux 2' on my machine, though please guide me through this a bit more please as i cannot see what you are referring to!!

[[IMG]http://www.imageshadow.com/images/23042008min/avidemux1297073_1e.jpg[/IMG]](http://www.imageshadow.com/view.php?image=avidemux1297073_1.jpg)

---

### Post by avantgardaclue on 2008-04-23
> **loell said:**
> also try mencoder,

```
mencoder -idx huge_size.avi -ovc lavc -oac mp3lame -o output.avi 
```

Hey Loell, did exactly what you suggested and the output came down to about 10% 25.3 MB from 274 MB!

However the new avi file when played was very 'patchy', sort of squares highlighted (not describing this very well sorry). Is it possible that the 'compression' was too aggressive, is there another instruction set that will allow more gentle reduction?

I found this...
[http://gentoo-wiki.com/HOWTO_Mencoder_Introduction_Guide#GUI_frontends_to_MEncoder]("http://gentoo-wiki.com/HOWTO_Mencoder_Introduction_Guide#GUI_frontends_to_MEncoder")
but it still seams way to advanced for me (but i am learning all the time by asking these questions!)

I ran the output 25 MB AVI file through FFMPEG expecting/hoping that the file would reduce down again significantly, but no... the MPG file came out at 68.7 MB!!

thanks

---

### Post by aeiah on 2008-04-23
just as an aside...

your video is so large because it is uncompressed. avi video can be encoded in several formats, or not at all (in your case). the common one for videos downloaded from the net is xvid, but the best one for quality vs filesize right now is x264. you could also consider converting them straight to dvd format if you'd like. this would result in the highest quality, practically speaking, although might be overkill for old home videos.

if you're serious about conserving the quality then you'll want to look into either xvid multipass encoding or processing the video for x264, and although these are time consuming, you'll get the best possible quality for size settings. it'll involve a bit of reading though unfortunatley :(

---

### Post by FakeOutdoorsman on 2008-04-23
I compress videos at work from DV sources to web and iPod using ffpmeg and x264.  I've never used Avidemux, but it uses ffmpeg's libavcodec to encode some formats such as mpeg4.  The ffmpeg package in Ubuntu universe has been compiled without support for x264, aac, and mp3 (among other codecs due to legal issues).  You can either compile ffmpeg (and/or x264), or use the ffmpeg package from [_Medibuntu_]("https://help.ubuntu.com/community/Medibuntu#head-7486ed038a9becc1dff10a24cc07a38a00d70e9f").

Once you get it installed, you can mess around with the command line.  I use a large script to help keep things nice, but here is a smaller example.  Since this is for the SVN of ffmpeg, some options have been renamed and you will get error messages, but type 'ffmpeg --help' to find the renamed commands:

```
#!/bin/bash
# ***************
# Encoding Script
# encoder.sh
# ***************
# Config Variables
film="nipplefire.avi"
outputDir="/media/sda5/movies/ipod640/"
newNameBase="nipplefireconcert"

ffmpeg -y -i ${film} -pass 1 -threads auto -s 640x480 -vcodec libx264 -b 384k -bt 192k -f mp4 -flags +loop -cmp +chroma -partitions 0 -me_method epzs -subq 1 -trellis 0 -refs 1 -coder 0 -me_range 16 -g 300 -keyint_min 30 -sc_threshold 40 -i_qfactor 0.71 -maxrate 10M -bufsize 10M -rc_eq 'blurCplx^(1-qComp)' -qcomp 0.6 -qmin 10 -qmax 51 -qdiff 4 -level 30 -aspect 4:3 -an /dev/null

ffmpeg -y -i ${film} -pass 2 -threads auto -s 640x480 -vcodec libx264 -b 384k -bt 192k -f mp4 -flags +loop -cmp +chroma -partitions +parti4x4+partp4x4+partp8x8+partb8x8 -me_method umh -subq 6 -trellis 2 -refs 1 -coder 0 -me_range 16 -g 300 -keyint_min 30 -sc_threshold 40 -i_qfactor 0.71 -maxrate 10M -bufsize 10M -rc_eq 'blurCplx^(1-qComp)' -qcomp 0.6 -qmin 10 -qmax 51 -qdiff 4 -level 30 -aspect 4:3 -acodec libfaac -ab 96k -ac 1 ${outputDir}${newNameBase}.mp4
```

To make it work, first make the script executable and then run it:
```
chmod +x encode.sh
./encode.sh
```

Options to monkey with:
**-b**	bitrate, this will determine the size and quality of your final file, lower number = smaller file and lower quality
**-ab**	audio bitrate
**-ac**	audio channels, 1 mono/2 stereo
**-subq**	sub motion estimation quality, smaller numbers will decrease encoding time at a small cost of quality, 7 is suggested highest, can try 5 or 6
**-deinterlace**	add if your source footage is interlaced or if you see horizontal lines during high movement scenes

---

### Post by FakeOutdoorsman on 2008-04-23
Here's a version that should work for Medibuntu ffmpeg:
```
ffmpeg -y -i input.avi -pass 1 -threads auto -s 640x480 -vcodec h264 -b 384k -bt 192k -f mp4 -flags +loop -cmp +chroma -partitions 0 -me epzs -subq 1 -trellis 0 -refs 1 -coder 0 -me_range 16 -g 300 -keyint_min 30 -sc_threshold 40 -i_qfactor 0.71 -maxrate 10M -bufsize 10M -rc_eq 'blurCplx^(1-qComp)' -qcomp 0.6 -qmin 10 -qmax 51 -qdiff 4 -level 30 -aspect 4:3 -an /dev/null

ffmpeg -y -i input.avi -pass 2 -threads auto -s 640x480 -vcodec h264 -b 384k -bt 192k -f mp4 -flags +loop -cmp +chroma -partitions +parti4x4+partp4x4+partp8x8+partb8x8 -me umh -subq 6 -trellis 2 -refs 1 -coder 0 -me_range 16 -g 300 -keyint_min 30 -sc_threshold 40 -i_qfactor 0.71 -maxrate 10M -bufsize 10M -rc_eq 'blurCplx^(1-qComp)' -qcomp 0.6 -qmin 10 -qmax 51 -qdiff 4 -level 30 -aspect 4:3 -acodec aac -ab 96k -ac 1 output.mp4
```

---

### Post by avantgardaclue on 2008-04-24
Hi guys, thanks for all your help! You lot together with the guys at the avidemux forum have got me through this! My version of avidemux was, apparently, hopelessly out of date so i installed the one from getdeb and voilla, i was able to do all sorts of things!

I did the 2 pass x264 thing, raised the colours and contrast, invoked the denoise3d filter and we have a much improved much shrunk video! 

I managed to reduce the 274.4 MB video down to 44.1 MB without losing any quality 

cheeers :)

---

### Post by wersdaluv on 2008-06-15
> **avantgardaclue said:**
> Hi guys, thanks for all your help! You lot together with the guys at the avidemux forum have got me through this! My version of avidemux was, apparently, hopelessly out of date so i installed the one from getdeb and voilla, i was able to do all sorts of things!

I did the 2 pass x264 thing, raised the colours and contrast, invoked the denoise3d filter and we have a much improved much shrunk video! 

I managed to reduce the 274.4 MB video down to 44.1 MB without losing any quality 

cheeers :)

How exactly did you do that? I'm having trouble with it. thanks :)

---

