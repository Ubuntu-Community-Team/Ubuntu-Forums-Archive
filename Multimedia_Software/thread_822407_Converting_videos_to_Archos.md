---
title: "Converting videos to Archos"
date: 2008-06-08
forum: Multimedia Software
---

### Post by Dooley on 2008-06-08
I've just bought an archos 504, I was wondering if anyone had any experience converting videos to this or even converting videos in general.

I want to convert mostly avis to.

	
Resolution: 480x272

Audio Rate: 91 kbit/s (Mp3 Lame)

Video Rate 31 kbit/s (AVI)

I tried avidemux but was a little confused. Anyone have a simple script that I can just plug these values into or a decent GUI tool?

Help is much appreciated!

---

### Post by Matthew Wiebelhaus on 2008-06-08
You won't have very much choices besides avidemux because it is probally the best on out. There are some online video converters but it defeats the purpose of your post I guess.

---

### Post by ubuntu-freak on 2008-06-08
[www.winff.org](www.winff.org)
 
Simple and works. There is an advanced option where you can enter the res, audio bitrate you want etc.

---

### Post by Dooley on 2008-06-08
Cool thanks for your replies. I'll give winff a bash and see if its playable on my archos.

---

### Post by Dooley on 2008-06-08
Hmm no luck with winff. For some reason it doesnt see the xvid codec.
Have u had any luck with this?

---

### Post by Dooley on 2008-06-08
In fact I can't output to anything. All the output codecs are unsupported. I've installed gstreamers extra plugins for these types of videos etc.

---

### Post by cariboo on 2008-06-08
You may also have to install the ubuntu-restricted-extras. to get the codecs you need.

Jim

---

### Post by ubuntu-freak on 2008-06-09
> **Dooley said:**
> Hmm no luck with winff. For some reason it doesnt see the xvid codec.
Have u had any luck with this?


Works for me, there isn't much of a need to compile FFmpeg anymore. When was the last time you did a fresh install of Ubuntu? If you have only been upgrading to newer versions, that may  be what's causing the issue.

Try purging and reinstalling everything related to FFmpeg.

Nathan

---

### Post by little_penguin on 2009-02-20
To convert a video to a format playable on Archos, open the video file
in Avidemux, then in the left dropdown boxes select:
 
Video - MPEG-4 ASP (Xvid4)
Audio - Lame (MP3)
Container - AVI
 
Click Save file with the .avi extension, and the file will be converted.

---

### Post by binbash on 2009-02-20
you can also check handbrake for converting

---

