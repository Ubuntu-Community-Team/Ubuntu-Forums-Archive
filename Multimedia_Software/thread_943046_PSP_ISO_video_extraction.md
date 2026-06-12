---
title: "PSP ISO video extraction"
date: 2008-10-09
forum: Multimedia Software
---

### Post by dgray_from_dc on 2008-10-09
I have a hacked PSP slim.  With it, I can insert a UMD movie and directly extract an ISO image from the UMD.  I've gotten as far as being able to mount the ISO image with:

```
sudo mount -o loop (filename) (mount point)
```

I've wandered around in the mounted image and found the movie data in a number of /umd_video/stream/xxxx.mp files contained within the image.  I was hoping that they would be in a variant of the MP4 format that VLC could read but they aren't.  I want to convert them into something more portable.  According to VLC, the files use the mpgv video codec and the a52 audio codec.  However, it's unable to decode and play them.  Any ideas?

Edit:  I tried opening it with avidemux (GTK+) and it thought the file was mpeg, tried to index it and then crashed.

---

### Post by dgray_from_dc on 2008-10-14
Update:  I think my problem with AVIdemux was that it tried to write back into the image and didn't know what to do when it ran into write permission problems.  I'm going to try and copy the file out first and then tinker with AVIdemux.

---

### Post by dgray_from_dc on 2008-10-15
I used 7-zip to pull the .mps file out if the ISO image and then gave AVIdemux another try.  It did the same thing, it opened the file identified it as mpeg, indexed it, then it displayed a message:

```
H.264 detected

If the file is using B-frames as reference it can lead to a crash or shuttering.
Avidemux can use another mode which is safe but YOU WILL LOSE FRAME ACCURACY.
Do you want to use that mode?
```

If you select no, it crashes.

If you select yes, then all of the frames look like garbage and as you look around in the file or perform any operation it crashes.

---

### Post by dgray_from_dc on 2008-10-23
I figured out that it's DRM that's preventing me from playing this file.  ***_D_***igital ***_R_***ights ***_M_***anagement means that this movie is licenced and encrypted.  I figured this out when I bought a Blu-Ray with Digital Copy.  Digital Copy only lets you copy your movie twice, to your PC once and a portable player (i.e. iPod or Zune) once, and only with iTunes or Windows Media Player.

It's against the law to circumvent the measures in the US, so I guess I'm out of luck.  With the exception of the analog loophole.  I can't create a digital conversion, but I can make an analog recording because of the quality degradation.  Maybae I'll just go with that.

---

