---
title: "Very slow x264 encoding using Avidemux in 10.04"
date: 2010-05-08
forum: Multimedia Software
---

### Post by orionds on 2010-05-08
I have been using Avidemux to encode edited video using x264 and the mp4 container for most of my videos. My PCs are not new, using single-core AMD Athlon processors.

In 9.04 and 9.10 (Linux Mint), encoding speeds ranged from 7 to 10 frames per second. In 10.04 these dropped down to less than 2 frames per second.

I booted back into Linux Mint 8 (9.10) and the same video encoded at the previous 7 to 10 fps.

I tried with other videos in different formats (mpeg2 and VOB). The results were the same - 10.04 was extremely slow encoding x264 but Mint 8 was "normal" at 7 to 10 fps.

With a dual-core notebook, however, the encoding speeds ran at 8 to 14 fps in 10.04.

Anyone had the same problem? Was 10.04 optimized for dual and multi-core at the expense of single-core? If so, is there a way to restore "single-core optimization"?

Thanks in advance for any suggestions or ideas.

---

### Post by no2498 on 2010-05-08
as long as you have 264 
try  tragtor
read and install what the page tells you to do

[http://mein-neues-blog.de/tragtor-gui-for-ffmpeg/](http://mein-neues-blog.de/tragtor-gui-for-ffmpeg/)

hope you can install it

and enjoy a faster speed

---

### Post by orionds on 2010-05-09
Thanks for the reply. I tried Tragtor. The encoding is faster but to get a smaller file size the video becomes very blocky especially when there is fast motion.

Avidemux was faster in 9.04 and 9.10 but in 10.04 it became very slow. Something has changed in 10.04 and Avidemux is not behaving as it used to and the speed for encoding x264 has dropped from about 8 or 9 fps to as low as 1 fps.

---

### Post by no2498 on 2010-05-09
dont know if changing the plugin in  gstreamer-properties may help

you should have cheese loaded
in sound&video  open it look in its help file faq's

it tells you how to change it

---

### Post by @H.264 on 2010-05-10
Do u have "Yasm" ?

---

### Post by FakeOutdoorsman on 2010-05-10
> **orionds said:**
> Anyone had the same problem?

I can't duplicate the slowness.  I tried 32-bit Karmic and 64-bit Lucid (both virtual machines) on an Intel i7-860.  Avidemux took 1:15 minutes in Karmic and Lucid took 1:32 with both using the same [clip](http://mirror05.x264.nl/Dark/x264clips/IronMan.mkv) and both exporting to MPEG-4 AVC (x264)/Audio copy in MP4.

As for x264 itself.  I opened two terminals and in one:
```
wget http://mirror05.x264.nl/Dark/x264clips/IronMan.mkv
sudo apt-get install mplayer
mkfifo video.y4m
mplayer input.foo -vo yuv4mpeg:file=video.y4m -nosound -ao null -noframedrop -ni
```
In the other terminal:
```
time x264 --threads auto --crf 26 video.y4m -o output.264
```

Karmic took 1:48 minutes and Lucid took 1:54 minutes to encode.  I guess that the time difference is due to Karmic's x264 being older and the default settings between the two x264 versions probably vary.

**Update:**  More numbers, but this time comparing today's x264 that I compiled.  Karmic 2:19 minutes and Lucid 1:56 minutes.

---

### Post by orionds on 2010-05-15
I tried using Arista transcoder on the Ironman mkv clip on a dual core notebook.

The encoding speed in 10.04 has half that of 9.10.

I have posted this as a bug in Launchpad. Hope they can fix it or provide a solution.

Thanks for the suggestions but they haven't worked so far.

---

### Post by FakeOutdoorsman on 2010-05-17
Are you experiencing slowness in Avidemux, x264, or Arista?  Did you test x264 as I did in my previous post?  What is the link to your bug report?

---

### Post by emarkay on 2010-05-19
Also, another Avidemux issue with more recent updates of it, in Karmic and Lucid - may be related?
[http://ubuntu-ky.ubuntuforums.org/showthread.php?p=9327772](http://ubuntu-ky.ubuntuforums.org/showthread.php?p=9327772)

---

### Post by fig_wright on 2010-07-07
Think I'm having this problem also. x264 encoding ridiculously long - 20x slower than Xvid for example!

---

### Post by alphacrucis2 on 2010-07-07
What version of Avidemux? You could try 2.5.3 which can be obtained from getdeb.

---

### Post by Ghost_Mazal on 2010-08-08
I have exactly the same problem. And it's not only in AVIdeMux. I get it in any app I use. All codecs convert a 2 hour movie in about 40min , but when I use x264 it jumps up to 5 hours. (Core 2duo @ 3ghz with 4gig ram , 32bit 10.04 LTS)

So far I can't find an answer.

---

### Post by triva911 on 2011-02-04
Which format is good and fast for encoding/compres avi files ?

---

