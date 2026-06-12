---
title: "U splitter And gnome split"
date: 2014-05-25
forum: Multimedia Software
---

### Post by cowboy7305 on 2014-05-25
I down loaded both of the above last night .
i have to split large AVI files to run on my mini tv media player
I think i have missed some thing when i use U splitter it says its working but does nothing 
When i use gnome split ,it does work<BUT the files are not AVI files more like text files 
I have Ubuntu restricted extras, any help with this would be great

---

### Post by vanadium on 2014-05-26
These utilities work at the binary level: they just distribute the bytes in the files in smaller parts. These parts are not useable as such, and must be recombined to reconstruct the original file.

To split one movie file into functional smaller parts, use a dedicated video editing tool. Avidemux can be used to split an AVI file into several smaller, playable AVI files. Using a command line tool (ffmpeg or avconv on Ubuntu) takes some learning but is far more efficient if you need to do this regularly, eg. [http://stackoverflow.com/questions/5651654/ffmpeg-how-to-split-video-efficiently](http://stackoverflow.com/questions/5651654/ffmpeg-how-to-split-video-efficiently)

---

### Post by MartyBuntu on 2014-05-26
I second the recommendation for Avidemux...you can split quickly without re-encoding.

---

### Post by cowboy7305 on 2014-05-29
thanks for info i thought i had found a easy way to do it,not that avidemxx is hard but have had on some occasions had trouble with the encoding 
thanks

---

