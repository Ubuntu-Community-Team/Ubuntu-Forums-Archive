---
title: "Error using ffmpeg to convert to ipod format"
date: 2007-07-31
forum: Multimedia &amp; Video
---

### Post by mr.derp on 2007-07-31
Well I have followed a tutorial for getting videos onto my ipod. It uses a script called ipodvidenc, which uses ffmpeg. However when I try to convert something ffmpeg gives this error message:

ffmpeg: error while loading shared libraries: libavformat.so.50: cannot open shared object file: No such file or directory

Not sure how to fix this. Has anyone else had this problem?

---

### Post by novalis_dt on 2007-07-31
Try this:

sudo apt-get install libavformat0d

---

### Post by mr.derp on 2007-07-31
I have libavformat0d already installed. I tried re-installing it, but I still got the same error message.

---

### Post by gsbad1 on 2007-10-19
Well I have the same error... I was told it had to do with something in the configuration. I have a work around that will help. Try this  in the terminal before you launch ffmpeg. 

export LD_LIBRARY_PATH=/usr/local/lib


Good Luck,
gsbad1

---

