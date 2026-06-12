---
title: "Make a video from pictures and a .mp3 playing over it ???"
date: 2007-08-07
forum: Multimedia Production
---

### Post by herbster on 2007-08-07
I have a bunch of pictures and a .mp3, I want to make a simple video that transitions from picture to picture with the .mp3 playing over it. Something like you see on Youtube all the time. Perhaps add text but that's not important.

How do I do this ? TIA!! :)

---

### Post by dougfractal on 2007-08-07
dvd-slideshow This is the main script. It generates a DVD-compatible MPEG2 video file with audio from a text file input listing of pictures and effects.

> apt-get install dvd-slideshow
dvd-slideshow

---

### Post by herbster on 2007-08-07
dougfractal,

Thanks! I am a bit bewildered, though. I am testing it with about 5 .jpg's in a ~/Desktop/video folder, using this cmd:

```
dvd-slideshow -n video.avi -a /media/extra/MP3/Singles/Icecore\ Scientist\ -\ A\ Pale\ Blue\ Dot.mp3  -f 30-10-06_1712.jpg crossfade::3 -f Jenny\ and\ Vijay\ LSI\ 2007.JPG:fadein:3
```

And it's not working as I'm sure it's quite wrong ;) Could you give me a sample command? I don't know what to put in the text file either. TIA.

---

### Post by dougfractal on 2007-08-07
> **herbster said:**
> dougfractal,```
dvd-slideshow -n video.avi -a /media/extra/MP3/Singles/Icecore\ Scientist\ -\ A\ Pale\ Blue\ Dot.mp3  -f 30-10-06_1712.jpg crossfade::3 -f Jenny\ and\ Vijay\ LSI\ 2007.JPG:fadein:3
```


I'm a bit old school, spaces in filenames :???:  spaces used to seperate commands or arguments. I know the "\" makes it alright and so does ""'s.  I guess i'm just getting old, or a KeepItOneLongName.kindaguy



[http://dvd-slideshow.sourceforge.net/examples/very_simple/](http://dvd-slideshow.sourceforge.net/examples/very_simple/)
> 
Very simple example
The text file is on the left with comments, and the sample output is on the right.

dvd-slideshow was run with the following arguments:

dvd-slideshow -n 'test verysimple' -f verysimple.txt

verysimple.txt
[QUOTE]
# blank lines and lines starting with '#' are ignored
# use "title" in the image field to create a title slide.
# title:duration:description
# The "description" string gets put on the title slide.

title:5:This is my title 	sample

# each picture gets put on a separate line. The format is:
# image.jpg:duration:subtitle
# duration is how long the picture will be visible in seconds.
# The Subtitle field is optional and can be left blank.

picture 1.jpg:4:Picture 1 	sample
pano.jpg:4:What a cool picture 	sample
picture2.jpg:3 	sample

# At any time in the slideshow, you can use special keywords:
# "background:2:subtitle:black" will insert a black background frame for 2 seconds

background:2:This is a black frame:black

# so this would work fine as well:
#background:2:This is a background image:background.jpg 	sample
# You can also use the "background" keyword to display the current
# background image (black or some passed image) for a given time:

background:2:This is the background[/QUOTE]

---

### Post by herbster on 2007-08-08
> **dougfractal said:**
> I'm a bit old school, spaces in filenames :???:  spaces used to seperate commands or arguments. I know the "\" makes it alright and so does ""'s.  I guess i'm just getting old, or a KeepItOneLongName.kindaguy



[http://dvd-slideshow.sourceforge.net/examples/very_simple/](http://dvd-slideshow.sourceforge.net/examples/very_simple/)

Thanks so much man! Doggone spaces in filenames :D I got it to work just fine. This is a great tool :) Much appreciated my friend! Thx! :)

---

### Post by ridgeland on 2007-08-09
In this thread:
[http://ubuntuforums.org/showthread.php?t=480314](http://ubuntuforums.org/showthread.php?t=480314)
we tried several ways to make slideshows with mp3
I also burned DVDs that could play on the TV's DVD player.
mandvd  was the easiest one.

---

### Post by ulixes84 on 2007-09-06
Hi there!

During the procedure I get the message:

sox: Can't open input file '/.../dvd-slideshow_temp_7662/audio1_0000.wav': No such file or directory

and there is no sound in the final file. Can anyone help me please?
Many thanks for your effort!
Matej :)

---

### Post by dougfractal on 2007-09-07
> Can't open input file '/.../dvd-slideshow_temp_7662/audio1_0000.wav': No such file or directory

funny name for a directory  **/...**   
check your paths

---

### Post by Coburn on 2007-09-07
I looked around to find a tool to do this.  I tried dvd-slideshow, polidori, varsha, etc. and settled on slideshow creator.  It is simple but it works for me.  The others did not seem to be able to do what I wanted.

You will probably have to research dependencies, etc. and install from tar.gz.  I think this is a non-Ubuntu/non-Debian program.  It's been a while since I installed it, so hopefully I am wrong.

If I remember right and dvd-slideshow is command-line, then my situation is that I am using slideshow creator as a GUI for it.  That would make DS a dependency.

My daughter and I made a great video (we like it anyway) using Eoghan Heaslip's "Lord Have Mercy" by making an Impress presentation, exporting the slides to JPEG in a folder with numerical extensions, like mercy001.jpg, mercy002.jpg, and compiling it into a video with slideshow-creator.  So far we haven't actually burnt it to DVD.

I think the project is on SourceForge.

---

