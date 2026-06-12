---
title: "AVI 2 MPEG DVD software?"
date: 2011-06-11
forum: Multimedia Software
---

### Post by sandman3838 on 2011-06-11
I have a TV series that is about 6 seasons and all the files are AVI.  I would like convert all to a standard MPEG files so that they can easily be played on any/most Tv DVD players.  What's the easiest program to burn these files to DVD's.  I have the following programs already installed.  Unfortunately the process for what I have now doesn't seem a little too rough, it should be smoother?  Am I missing something in setting up the burns in these programs or is there another program you could recommend?



- Brasero

- DeVeDe

- DVD:Rip

- GnomeBaker CD/DVD Write

Thank you!  :)

---

### Post by wolfen69 on 2011-06-11
Winff is probably what you want. It has a "convert to dvd" option. Then you take the converted file and use DeVeDe to burn it.

---

### Post by AlexDudko on 2011-06-11
ffmpeg is a good and easy to use console tool for encoding videos.
Just type in terminal
> ffmpeg -i inputfilename.avi outputfilename.mpeg

---

### Post by handy on 2011-06-11
> **AlexDudko said:**
> ffmpeg is a good and easy to use console tool for encoding videos.
Just type in terminal

Can it handle a string such as the following, which would be a collection of .avi files of various sizes that would in combination all fit on DVD media:

```
ffmpeg -i inputfilename_1.avi inputfilename_2.avi inputfilename_3.avi inputfilename_4.avi outputfilename.mpeg
```

---

### Post by ron999 on 2011-06-11
> **AlexDudko said:**
> 
Just type in terminal
Quote:
[COLOR="Red"]ffmpeg -i inputfilename.avi outputfilename.mpeg[/COLOR] 

This command will create a file with MPEG-1 video and mp2 audio.:(

---

### Post by handy on 2011-06-11
> **ron999 said:**
> This command will create a file with MPEG-1 video and mp2 audio.:(

That's true.

I've rarely needed to convert movie files to DVD format. When I have I used DeVeDe, it did a good job on those instances.

---

