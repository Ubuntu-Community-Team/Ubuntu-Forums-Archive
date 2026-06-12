---
title: "Video encoding questions"
date: 2008-05-01
forum: Multimedia Software
---

### Post by zaius55 on 2008-05-01
Hello,

I'm trying to encode some files I have (200MB XVID TV Episodes) to MPEG2 format for burning onto a DVD.  Using Tovid with the ffmpg option I have a question.  I setting a -quality of 9, however after encoding the resulting dialog indicates the following 

```

Final size:      753952 kilobytes
Target bitrate:  8100 kbits/sec
Average bitrate: 2497 kbits/sec
Peak bitrate:    2802 kbits/sec

```

The original XVID file is not of stellar quality is it possible that any encoding above 2500 will not make a noticeable difference in quality given the source?

Thanks!

---

### Post by TenPlus1 on 2008-05-01
Why not just download DeVede from getdeb.net and install that instead... It'll take any video and let you create a DVD Video with menu's, plus it's easy to use...

---

### Post by xzero1 on 2008-05-01
If you use ffmpeg directly or can add parameters to the ffmpeg option, you could use the -sameq option which encodes at the same quality as the source.

See [http://ffmpeg.mplayerhq.hu/ffmpeg-doc.html]("http://ffmpeg.mplayerhq.hu/ffmpeg-doc.html")

---

### Post by zaius55 on 2008-05-01
I'll look at the output tovid passes.  I'm willing to bet it passes that by default.

Bob Out

---

### Post by zaius55 on 2008-05-01
Devede was ok, found it be fairly buggy.  I really like the menus I can created with 'todisc' very easily.  Plus with tovid I can batch process all my avi's overnight.  

However the quality of the todisc menu's looks questionable (grainy etc).

---

### Post by xzero1 on 2008-05-01
> I'll look at the output tovid passes. I'm willing to bet it passes that by default.


Try "ffmpeg -i [name] -sameq -f dvd [name].mpg" and compare encodings to see if tovid uses sameq.

---

### Post by zaius55 on 2008-05-02
Well it doesn't pass sameq.  Here is the actual line that it passes to ffmpeg

```
nice -n 0 ffmpeg -i "sample.avi"             -target ntsc-dvd -qmin 1 -qmax 31 -b 9000k -ab 224k -ac 2  -r 29.970          -s 720x480   -aspect 4:3  "sameple.tovid_encoded.mpg" 
```

I guess the question is If my target bitrate is 8100 or 9000 (quality 9 or 10) why is it only encoding to 2400kbps?

---

### Post by xzero1 on 2008-05-02
> I guess the question is If my target bitrate is 8100 or 9000 (quality 9 or 10) why is it only encoding to 2400kbps? 

Your comand line is using *vbr* and a wide range for your quantizer with no bit rate tolerance set. I think you can get it closer to your target bitrate using a different command line.

---

### Post by grepster on 2008-05-22
The encoder will only use as many bits as it needs to encode your source.  If it is of poor quality to begin with, encoding at an artifically high bitrate will just stuff useless bits.

With respect to grainy looking menus, I have not heard that one before.  You might try svn todisc which uses lossless ppm for the final montages - you may find you get better quality.

Note: tovid also has a -fit option that is worth looking into - though that is more for encodes that might take up more space than available on a single DVD.

grepper

---

