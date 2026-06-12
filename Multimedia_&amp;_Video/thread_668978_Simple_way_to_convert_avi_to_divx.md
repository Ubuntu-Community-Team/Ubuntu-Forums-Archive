---
title: "Simple way to convert avi to divx?"
date: 2008-01-16
forum: Multimedia &amp; Video
---

### Post by winkerbean on 2008-01-16
What's the simplest way to convert avi files to divx?  I've tried using transcode, but it does not seem to want to work (e.g., this files missing, that libraries not installed, etc.).

Thanks.

---

### Post by shad0w_walker on 2008-01-16
Just install transcode from the repos. It will handle dependencies automatically.

---

### Post by winkerbean on 2008-01-16
Yeah, tried that route.  Didn't work.

---

### Post by shad0w_walker on 2008-01-16
If it isn't installing from the repos I would suggest you focus on that, because that is a much more important problem and is gonna affect you more than not being able to transcode.

---

### Post by winkerbean on 2008-01-16
Perhaps I mis-typed: transcode installs.  But when I try to convert, I get:
[INDENT][export_divx5.so] *** Warning: DivX is broken and support for it is ***
[export_divx5.so] *** obsolete in transcode. Sooner or later it  ***
[export_divx5.so] *** will be removed from transcode. Don't use ***
[export_divx5.so] *** DivX. Use xvid or ffmpeg -F mpeg4 instead ***
[export_divx5.so] *** for all your mpeg4 encodings. ***
[export_divx5.so] libdivxencore.so.0: cannot open shared object file: No such file or directory
[/INDENT]

---

### Post by shad0w_walker on 2008-01-16
So it appears divx support is being removed. Just used xvid. I have grown tired of messing about with divx myself.

---

### Post by ron999 on 2008-01-16
> **winkerbean said:**
> What's the simplest way to convert avi files to divx? 
Don't you just need avi files that contain divx/xvid encoded video and mp3 encoded audio?

---

### Post by eye208 on 2008-01-16
> **winkerbean said:**
> What's the simplest way to convert avi files to divx?
As ron999 already pointed out, most of today's AVI files are indeed DivX/Xvid files. Remember that AVI is just a container. The *.avi extension doesn't say anything about the actual stream format inside the file.

To find out what's inside, look at the properties panel of Totem, the "About Stream/Media" window of VLC or the console output of MPlayer.

By the way, DivX and Xvid are not the best codecs out there. Unless you need to stick with them for compatibility (hardware DVD players etc.), the x264 codec will give you a much better quality/size ratio.

---

