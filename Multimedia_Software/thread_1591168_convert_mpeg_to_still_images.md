---
title: "convert mpeg to still images"
date: 2010-10-08
forum: Multimedia Software
---

### Post by kr651129 on 2010-10-08
Well heres my problem I need to convert an mpeg into a series of still images but I cant find any software on linux to do this unless you know of any software that can convert video into vector style graphics, thanks for the help

---

### Post by kr651129 on 2010-10-08
ha!  nevermind, found the option in cinelerra

---

### Post by andrew.46 on 2010-10-09
Hi kr651129,

Looks like you have sorted out your problem but you may be interested to know that MPlayer can output as gif, jpg and png with the png output being the most flexible.

Andrew

---

### Post by SeijiSensei on 2010-10-09
+1 to Andrew for the advice and another +1 for his David Byrne signature reference!

cinelerra is overkill for this task.  

mplayer -ao null -vo png input.file

will extract all the frames in input.file and save them as numbered PNGs.  If you want to extract just a segment of the video, you can use the "-ss" and "-endpos" options like this:

mplayer -ao null -vo png -ss hh:mm:ss -endpos #secs input.file

replacing hh:mm:ss with the starting time of the extract and #secs with the length in seconds you wish to capture.

---

### Post by kr651129 on 2010-10-10
Thanks for all the advice!

I'm converting each jpeg into a vector and I found a pretty neat program for windows called vector magic but it runs slow in wine and crashes a lot plus I'm converting some 2000 frames of footage so I need to do this in linux.  I'm fully aware that you can do this manually in gimp and similar image editors but I need to automate this process if I want to do this any quick that 10 years.

Ideas?

---

### Post by SeijiSensei on 2010-10-11
What do you mean by "into a vector?"  What file format do you want the output to be?  Have you tried [ImageMagick]("http://www.imagemagick.org/script/index.php") from the repositories?  It can do most any image conversion you can imagine, and as it's a command-line program, you can script it easily to handle batch conversions.

---

### Post by kr651129 on 2010-10-11
basicly I want to convert a video into vector style graphics similar to that of the movie "A Scanner Darkly"

---

### Post by SeijiSensei on 2010-10-12
That really doesn't help.  What *file format* do you want?

---

### Post by kr651129 on 2010-10-14
The end result will be an mpeg video, but each frame (image) needs to be jpeg unless there is a way to do this to a mpeg without having to work each frame

---

