---
title: "ffmpeg converted my movie into wide screen"
date: 2008-02-17
forum: Multimedia &amp; Video
---

### Post by Motorhead Kaze on 2008-02-17
Hello, just used ffmpeg to convert an .avi to mpg (planning to make a DVD with K3b eventually) but the thing came out wide screen, so all the people in the movie are fat and short.

How can I fix this?

---

### Post by yabbadabbadont on 2008-02-17
It would help if you posted the actual command that you used to convert the file...  ;)

Edit: You may also be interested in the "tovid" package.  There is a rather large "howto" thread around here somewhere.  I'm using it now to convert a video in preparation for making a DVD.

---

### Post by Motorhead Kaze on 2008-02-17
Yes, I used
```
ffmpeg -i input_file.avi -target ntsc-dvd output.mpg
```

Tovid, isn't that the program people complain about taking forever to complete conversions?  I just tried DeVeDe for the first time since Feisty.  See they still haven't fixed the Mencoder issue.  So, a friend recommended ffmeg.  It was very fast, but I can't deal with the size issue.

Any words on what command would be better for me, would be cool.  For example, where to put the code for the correct resolution and what that should be for a standard t.v. screen.

---

### Post by yabbadabbadont on 2008-02-17
You can configure tovid to use ffmpeg exclusively in its ~/.tovid/tovid.config file.  You could also pass the "-ffmpeg" option on the command line if you prefer.

Here is the current output for the movie I am converting right now.  It should be noted that I am converting it to US standard DVD format and that I have the tovid quality setting set rather high (8 out of 10).  You'll need to adjust the options for your region and desired quality.

```
Analysis of file /video2/Movies/MyMovie.avi:
  640 x 336 pixels, 25.000 fps
  Duration (best guess): 01:49:28 (HH:MM:SS)
  DX50 video with mp3 audio
Target format:
  720 x 480 pixels, 29.970 fps
  m2v video with ac3 audio
  7200 kbits/sec video, 224 kbits/sec audio

=========================================================

Using auto-detected aspect ratio 190:100 (override with -aspect)
Letterboxing vertically
Input is not 29.970 fps. Framerate will be adjusted.
Scaling picture to 720 x 448
Centering picture against a 720 x 480 black background

=========================================================

Using ffmpeg to encode audio and video.
Encoding video and audio with the following command:
nice -n 0 ffmpeg -i "/video2/Movies/MyMovie.avi" -target ntsc-dvd -qmin 3 -qmax 31 -b 7200k -ab 224k -ac 2 -r 29.970 -s 720x448 -padtop 16 -padbottom 16  -aspect 16:9 -map 0:0  -map 0:1 "/home/daffy/temp/MyMovie.mpg" 
```

---

### Post by Motorhead Kaze on 2008-02-17
Thank you.  But what I was really looking for was the way to continue using ffmpeg in the command line to convert my .avi files, as I have done, but without changing the resolution to look like wide screen.  I may try Tovid soon, but if I can get ffmpeg to work the way I like, I will keep using it, and then go from there.

---

### Post by pbcartwright on 2008-02-17
I use tovid on the command line, which uses ffmpeg as a back end. Tovid is very configurable also.. as for ffmpeg, if you do a:
man ffmpeg
you will see, down the list a "-s size" option with lots of configuration options:
 -s size
           Set frame size. The format is wxh (ffserver default = 160x128, ffmâ€
           peg default = same as source).  The following abbreviations are
           recognized:

           sqcif
               128x96

           qcif
               176x144

           cif 352x288

           4cif
               704x576

           qqvga
               160x120

           qvga
 320x240

           vga 640x480

           svga
               800x600

           xga 1024x768

           uxga
               1600x1200

           qxga
               2048x1536

           sxga
               1280x1024

           qsxga
               2560x2048

           hsxga
               5120x4096

---

### Post by Motorhead Kaze on 2008-02-17
Oh hey!  Very cool, thanks for the manual command!  Next question is, my .avi file, when looking under properties/audio video, says it is 672x368.  Another that I plan to convert is 720x404.  So, do I type in  -s 672x368 for example, or do I need to type in -s and the letter code for the size?  OR should I just skip that, and type in -aspect 4:3 instead?  

 ffmpeg -i BSG=mini.avi -target ntsc-dvd -aspect4:3 output.mpg didn't do anything but bring up an error...
....oh, silly me I forgot to cd Desktop where the movie is.  I am hoping just changing the aspect ratio will be enough.

---

### Post by yabbadabbadont on 2008-02-17
> **Motorhead Kaze said:**
> Thank you.  But what I was really looking for was the way to continue using ffmpeg in the command line to convert my .avi files, as I have done, but without changing the resolution to look like wide screen.  I may try Tovid soon, but if I can get ffmpeg to work the way I like, I will keep using it, and then go from there.

The last line of what I posted was the ffmpeg command...  I just included the other stuff so that you would see how the different ffmpeg options used, related to the source video format, as well as the target video format.  It was just intended to be a starting place for you in your research on the correct ffmpeg options.  :)

---

### Post by philc on 2008-02-20
If your input file is 720x404, but your NTSC DVD output is 720x480, then you could pad the top and bottom to create a letterboxed effect.

```
ffmpeg -i input.file -padtop 38 -padbottom 38 -s 720x480 output.file
```

---

### Post by Motorhead Kaze on 2008-02-29
Sorry for my late reply (work.  You know.)  

I did get my .avi converted with ffmpeg -- even got the sizing ratio right -- but all the sound was out of sync with the vid.  A real bummer.  Did I do something wrong or ?  I received no error messages.

Now, if I could figure out how to get my synchronization set correctly...  I hope this is not related to a very similar problem I had when trying out Kdenlive.  Kden put my video and sound out of sync too. 

Further advice on this newer problem would be super!  Thanks!

Yabba DD -  As it turns out I may end up using Tovid anyway, so I appreciate the extra steps you posted! I actually revisited this post today in part to reread what you guys had said about that program.

EDIT: 6/08  Tovid's GUI rocks. I am now a full-fledged Tovid fan. There are options on one of the tabs to select the proportions (ratio) of the movie and the whole program is just super easy to use.  Time consuming, but I really like having ONE program to turn an .avi, etc. into a DVD. (No cool menu effects or that, but this is what you use when you want simple).

---

