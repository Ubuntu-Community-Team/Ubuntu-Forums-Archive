---
title: "Video Editors"
date: 2008-01-15
forum: Multimedia &amp; Video
---

### Post by RedRat on 2008-01-15
I have Ubuntu Studio installed. However when I try to load an AVI or Divx (and even wmv files) film clip into video editors such as Kino or pitivi movie editors, I get a strange error message: "Video framerates other than 25 are not supported
This is not an image file" (this from Open Movie Editor. Pitivi just plain refuse to import the clip. Kino imports the clip but does not show it in widescreen format and squeezes the frame to fit the standard video frame. Oddly, Totem movie player plays all of these clips with no problem.

I download various film clips from around the internet and would like to string them together into one longer clip. Is there a video editing program that will do this? I would like to stay with the AVI and Divx format because they play on my DVD machine which is piped into my HD set. Also, converting to other formats can lose what resolution these clips may have. 

I have looked at past posts on this subject (all from around 2005 and 2006) and they too seem to have run into the same problem I see. In the intervening time since these older posts has anything come along?

---

### Post by nexu56 on 2008-01-16
I have had much success with Kdenlive, handles anything I throw at it. A lot of people also recommend Cinelerra, but in my experience it has similar problems with compressed formats :-k

---

### Post by philc on 2008-01-16
If it's just stringing a bunch of video clips together into one longer file, then you should be able to do this without the use of a video editor, but you might need to be comfortable with the command line to do it.

Steps:

1. Use FFMPEG or Mencoder to transcode all your videos to exactly the same format.

2. Use "cat" to concatenate the files together.

Here's something that's a bit old from the FFMPEG mailing list, but might point you in the right direction:

[http://lists.mplayerhq.hu/pipermail/ffmpeg-user/2006-October/004611.html](http://lists.mplayerhq.hu/pipermail/ffmpeg-user/2006-October/004611.html)

Another suggestion might be [Transcode](http://www.transcoding.org/). This blog post has some pointers:

[http://barillari.org/blog/2007/06/](http://barillari.org/blog/2007/06/)

---

### Post by Keith Hedger on 2008-01-16
cat wont work on some video files avi for instance the files have to be headerless for it to work i personally use avidemux to hop about and append videos and then ffmepg to convert files for my ipod

---

### Post by RedRat on 2008-01-16
Thanks for the suggestion. I downloaded Kdenlive and have installed it. It does seem to recognize and load the clips that I am intrested in. I will work with it for awhile. So far it seems to do what I want!

Thanks.

---

