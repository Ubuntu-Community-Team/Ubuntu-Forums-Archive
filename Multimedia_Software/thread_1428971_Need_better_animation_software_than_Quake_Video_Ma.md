---
title: "Need better animation software than Quake Video Maker"
date: 2010-03-13
forum: Multimedia Software
---

### Post by Rhemat on 2010-03-13
I have been recording some demos from games like Quake 3, 4, and Doom 3.  Now, I've been able to use Quake Video Maker in the past to take the Targa frames that the games export, and then combine those into a movie.  However, it seems this time that QVM is spitting out some bad files.  I try to watch the AVI file, but I just get this error message:

** Message: Error: Could not demultiplex stream.
gstavidemux.c(3526): gst_avi_demux_stream_header_pull (): /GstPlayBin2:play/GstURIDecodeBin:uridecodebin0/GstDecodeBin2:decodebin20/GstAviDemux:avidemux0:
pull_range flow reading header: unexpected

I figured that if I import it into Kino, then I should be able to edit just fine.  Except, when I import it into Kino, the video just hangs on the first frame for the first half, and then plays the whole video at double the speed.
Is there a better package that will take a lot of image files and export them into a movie file?  Preferably one where I don't have to add each frame manually, as the demo I'm working with now has 5000+ frames.
Thanks in advance.

---

### Post by Rhemat on 2010-05-08
Okay, I have a mencoder command that works, but I need to work on the image quality (which might be a problem with MPEG4, but I don't know):

mencoder mf://*.tga -mf w=856:h=480:fps=30:type=tga -ovc lavc -lavcopts vcodec=mpeg4:mbd=2:trell -oac copy -o test.mpeg

I'm going to keep looking for a way to get FFMPEG to work with TGA, or to get mencoder to use the MOV format.

Thanks

---

### Post by Rhemat on 2010-05-10
Found a better quality solution:

mencoder mf://*.tga -mf w=856:h=480:fps=30:type=tga -ovc lavc -lavcopts vcodec=mpeg4:vbitrate=1800 -oac copy -o test.mpeg

---

