---
title: "ffmpeg in h264/mpeg-4 avc high profile"
date: 2008-04-17
forum: Multimedia &amp; Video
---

### Post by grifter13 on 2008-04-17
Has anyone got this to work?  I have a Linksys NAS200 and I'm tyring to use the built in media server to stream to my PS3.  Now, PS3 spec says that it supports h264 and MPEG-4 avc high profile.  So I tried to convert some of my video with both codec but neither was liked by PS3 over the media server.  So my question is

1. What is the proper ffmpeg command to convert PS3 compatible H264/MPEG4 video?
2. Has anyone been successful in stream these videos from Linksys's NAS200, if so what did you do.

Thanks in advance.

Grift..

P.S. I was advised to use avidemux, but yet to have tried this.  Going to do that tonight, wish me luck.

---

### Post by disturbedite on 2008-04-17
just use avidemux.

---

### Post by grifter13 on 2008-04-18
I did and it doesn't work for me... PS3 simply says "There are no titles".

grift

---

### Post by xzero1 on 2008-04-18
It could be you may not be using the right container type for the ps3. There are two things to consider: the container type (file format) and the codec (encoder) used. Try "ffmpeg -formats" to list them. I don't know anything about the NAS200 but you can stream to the ps3 using a DLNA server such a Mediatomb. In any case their help forum should be useful.

---

### Post by cor2y on 2008-04-18
for ffmpeg hq x264 ffmpeg has to be compiled with x264 support which means x264 dev has to be installed/compiled on your system. And mp4 output/container requires that gpac be installed/compiled.
Simpler way is to use h264enc for linux , xvidenc for linux or divxenc for linux. These are scripts that come with preset profiles (from low to very high quality) for encoding in either x264. mpeg4 or xvid and can be output as mp4, mkv ogm or avi with various audio formats and video filters. 
The only downside is that it uses mencoder and not ffmpeg
take a look at the sites to get the script.
```
http://h264enc.sourceforge.net/
http://divxenc.sourceforge.net/
http://xvidenc.sourceforge.net/
```
You will also need to have installed the various audio encoders etc.

---

### Post by grifter13 on 2008-04-18
Thanks for all the tips and suggestion guys, they are all so helpful.  I have all the libraries compiled as matter of fact the h264 in mp4 formate plays in both my psp and ipod.  However oddly enough PS3 just don't like it.  Now my question is I am wondering if PS3 is just very pick with it h264 format?  i.e. it is expecting a very specific resolution, amount of B-frame, X amount of bps etc.  If so what are they?  Thanks again everyone.

Grift

---

### Post by grifter13 on 2008-04-22
A quick update on this issue.  I decided to try mythtv's DLNA functionality just to see if PS3 with pick it up.  It turns out it PLAYS!  AVI, Dixv, mp4 etc.  The difference is that I have all these codecs installed on my Ubuntu box, does that mean a DLNA server only streams videos that is the respective codec installed?  I originally though the decodeing happenes on the player side.


Grif

---

### Post by graveson on 2008-06-30
grifter13:
i would be interested in how you setup mythtv? backend or frontend and did you need to configure DLNA

---

