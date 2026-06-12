---
title: "How to Convert Video to iPhone"
date: 2007-12-03
forum: Multimedia &amp; Video
---

### Post by TadH on 2007-12-03
thanks for this

---

### Post by Mateo on 2007-12-04
This is the easy part.

The part I haven't figured out:  how do I get my video onto the iPhone?

---

### Post by Terc on 2007-12-05
Try handbrake instead, it's kinda nice that it actually RUNS ON LINUX...  Thanks for the spam though "reallyone"

For a fantastic GTK wrapper for the CLI Linux handbrake, go here:

[http://sourceforge.net/projects/rippedwire/](http://sourceforge.net/projects/rippedwire/)

---

### Post by jazz452 on 2008-01-30
I use xilisoft iphone video converter drag in a file it automatically converts and resizes video.Then simply add media device from amarok even an idiot like me can manage that.Must add it runs under wine but it works very well.

---

### Post by Mateo on 2008-01-30
I use this script:

```
#!/bin/bash
ffmpeg -i "$1" -r 29.97 -vcodec h264 -s 480x320 -aspect 16:9 -flags +loop -cmp +chroma -deblockalpha 0 -deblockbeta 0 -b 1000k -maxrate 1250k -bufsize 4M -bt 256k -refs 1 -coder 0 -me umh -me_range 16 -subq 7 -partitions +parti4x4+parti8x8+partp8x8 -g 250 -keyint_min 25 -level 30 -qmin 10 -qmax 51 -qcomp 0.6 -trellis 2 -sc_threshold 40 -i_qfactor 0.71 -acodec aac -ab 80k -ar 48000 -ac 2 "$2"
```

---

### Post by exile on 2008-02-01
Thanks for that script. I have learnt some things that I didn't know before.

I'd just like to throw out there that I have found that using r=20 for 20 fps makes the file size smaller and the battery life longer.. now you don't necessarily want to do this for the fast action movies but for TV shows (especially the comedies or dramas) I find that it is acceptable - great for long trips!

---

### Post by FakeOutdoorsman on 2008-02-01
I recommend taking a look at the Ubuntu Wiki page: [Encoding Video for the iPod Video]("https://help.ubuntu.com/community/iPodVideoEncoding").  Take a look at the pypodconv script if you like ffmpeg or Mark Pilgrim's mencoder based solution if you prefer mencoder.  Mateo's script looks good, but could be much improved with two-pass encoding, which pypodconv uses.

---

### Post by Mateo on 2008-02-01
I think 2 pass encoding is unneccesary on the iphone.  My videos are about as crisp looking on the iphone as on the TV.   You can tell the (very slight) difference watching the video on your computer, but not on the iphone.  It's already a long encoding process (for me it's an hour and a half for a 42 minute TV show).

---

### Post by FakeOutdoorsman on 2008-02-02
> **Mateo said:**
> I think 2 pass encoding is unneccesary on the iphone.  My videos are about as crisp looking on the iphone as on the TV.   You can tell the (very slight) difference watching the video on your computer, but not on the iphone.  It's already a long encoding process (for me it's an hour and a half for a 42 minute TV show).

You can get a very fast first pass by changing a few options. For your script, try changing "-subq 7" to "-subq 5" if you want to have a quicker encode.  Subq 6 and above would help more if you were using b-frames, but that can really increase the encode time.  Changing "-me umh" to "-me hex" will also increase the speed with a small trade-off to quality.

---

### Post by mackid on 2008-07-12
Is there a way to get that script to use both of my processors? (Besides running two instances of the script for two different episodes of a TV show, for example)

Thanks.

---

