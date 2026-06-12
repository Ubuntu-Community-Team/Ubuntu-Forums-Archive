---
title: "Help Creating Video File from Images"
date: 2007-09-10
forum: Multimedia Production
---

### Post by morning_napalm on 2007-09-10
I am trying to find a simple way to convert a folder full of images into a video file. My son (10) makes animated movies using Legos and has typically used Make AVi (windows) to convert a list of images to an avi file.  I have tried the following command line that I found but get an error message:

Creating an MPEG-4 file from all the JPEG files in the current directory:

mencoder mf://*.jpg -mf w=800:h=600:fps=25:type=jpg -ovc lavc \
    -lavcopts vcodec=mpeg4:mbd=2:trell -oac copy -o output.avi

the error I get is:  

============ Sorry, this file format is not recognized/supported =============
=== If this file is an AVI, ASF or MPEG stream, please contact the author! ===
Cannot open demuxer.

I think there is a way using mencoder or ffmpeg to do this, but I have not been able to find a good source for help.

Does anyone know how to do this?

Thanks.

---

### Post by loell on 2007-09-10
not sure if this can help, but can you try this,
```
mencoder -ovc lavc -mf fps=3:type=jpg 'mf://*.jpg' -o movie.avi
```

---

### Post by morning_napalm on 2007-09-11
Thanks.  This actually worked great.  The only issue I had was that the image files ended in .JPG, not .jpg.  I haven't tried it yet, but I think that may have been the problem with the original command line I tried.

I appreciate the help.

:)

---

