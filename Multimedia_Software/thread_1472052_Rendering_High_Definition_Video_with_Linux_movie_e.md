---
title: "Rendering High Definition Video with Linux movie editors"
date: 2010-05-04
forum: Multimedia Software
---

### Post by Rhemat on 2010-05-04
Heya,
Okay, I recently got a High Definition camcorder, and I do want to record high definition videos.  Unfortunately, I've not been able to edit the video, and export a high definition video.  KDenLive takes up the majority of my CPU's time (AMD Athlon 64 3200+ 2GHz), and usually crashes.  Kino will import it, but any format I export it with just resizes it to 854 or 720x480.  The OpenMovie editor is unreliable, and quits without provocation.  I want to try OpenShot, but due to a dependency not in the repos, I haven't got far with it.
I guess I don't mind that too much, but I may be doing some video editing for a friend, and he said that he needs the video to be high definition.  Is there some tweaking I can do with the programs?  For example, telling Kino to stop using DV format?
Thanks in advance.

---

### Post by rylleman on 2010-05-04
Camcorders often use strange formats and codec variants that the NLEs may have trouble working with.
Try transcoding the clips to another format. In Kdenlive you can do this by importing the materialm then right-click on them in the bin and choose "transcode". Use the DNxHD profile that best fits the material you got.

---

### Post by SL666 on 2010-05-04
I've got a canon HD camcorder, i use cinelerra to edit, but i convert it from the avchd format with FFMPEG first (to a stupidly high bit rate MPEGTS format)

i then render the output from cinelerra to the YUAV? format? and mp3 audio, then combine with FFMPEG again, into the final format i want.

i installed ffmpeg from fakewoodsmans instructions on here.

---

### Post by Rhemat on 2010-05-05
Thanks for the replies, I have been playing with FFMPEG (I found a tutorial, which I will post here later), and I can transcode from one format to another.  The only problem is that when transcoding to DV format, it lowers the resolution to 720x480, and switches to 4:3 aspect ratio instead of 16:9.  Maybe I don't have the proper DV libraries or codecs?
I'm trying to install Cinelerra, but the deb source I got just gave me errors.

While we're talking about FFMPEG, can it be used to take many frames, and lump them into a video?  I would prefer to use MPEG for my Quake/Doom movies rather than AVI, since it does not take long to hit the 2GB size limit.  I know I posted about that in another thread, but I don't think I phrased the question properly.

Thanks in advance.

---

### Post by Rhemat on 2010-05-08
I forgot, here is the FFMPEG tutorial I mentioned a couple of days ago:
[http://linuxers.org/tutorial/ffmpeg-tutorial-beginners](http://linuxers.org/tutorial/ffmpeg-tutorial-beginners)

I got Cinelerra to work, and the interface is daunting, but I think I finally got it to do what I want it to do.

Thanks for your replies.

---

### Post by Rhemat on 2010-05-08
Okay, I have a mencoder command that works, but I need to work on the image quality (which might be a problem with MPEG4, but I don't know):

mencoder mf://*.tga -mf w=856:h=480:fps=30:type=tga -ovc lavc -lavcopts vcodec=mpeg4:mbd=2:trell -oac copy -o test.mpeg

I'm going to keep looking for a way to get FFMPEG to work with TGA, or to get mencoder to use the MOV format.

Thanks

---

### Post by Rhemat on 2010-05-10
I found a better quality solution:

mencoder mf://*.tga -mf w=856:h=480:fps=30:type=tga -ovc lavc -lavcopts vcodec=mpeg4:vbitrate=1800 -oac copy -o test.mpeg

---

### Post by ricardisimo on 2011-03-15
Is mencoder actually rendering an HD ISO for you? I have no problem editing the videos with OpenShot, but I need to know how to create the actual high-def disc image. Thanks.

---

### Post by ricardisimo on 2011-03-16
Anyone?

---

### Post by ricardisimo on 2011-03-21
What are any of you using to render an HD-DVD? Thanks.

---

### Post by ricardisimo on 2011-03-29
MANDVD crashes, every time, as do most options besides devede.

---

### Post by SeijiSensei on 2011-03-29
> **ricardisimo said:**
> Is mencoder actually rendering an HD ISO for you? I have no problem editing the videos with OpenShot, but I need to know how to create the actual high-def disc image. Thanks.

Most HD files use H.264 video and AAC audio in the Matroska (MKV) container.  Either mencoder or ffmpeg or both shoujld be able to use the x264 encoder for video and lavc to create the audio.

I recommend browsing sites like doom9 and other places where encoding is discussed.

---

