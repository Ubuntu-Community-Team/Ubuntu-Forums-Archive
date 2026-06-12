---
title: "need help setting up webcam....."
date: 2006-06-29
forum: Multimedia &amp; Video
---

### Post by someguyouknow on 2006-06-29
i have a logitech quickcam webcam and i dunno how to set it up.....
i am a n00b so i can use all the help i can get.....
thanks in advance.....

---

### Post by olsonar on 2006-06-29
should be automatic. just install software that can use it and plug it in. if you want something to test it with, try camorama. I have the quickcam for notebooks and that's alll I had to do. Just be sure to plug in the camera before starting the program.

---

### Post by someguyouknow on 2006-06-29
you mean the software provided by logitech?.....
i have tried camorama and it didnt work.....

---

### Post by olsonar on 2006-06-29
logitech doesn't provide linux software. maybe you don't have the nessecary v4l sftuff installed? when i search for v4l in synaptic, it turns up the followiing packages as installed: gstreamer0.8-misc libpt-plugins-v4l libpt-plugins-v4l2 xserver-xorg-driver-v4l. perhaps if you installed these it would help?
it's also possible your webcam is not supported by v4l, and simply will not work.

---

### Post by richbarna on 2006-06-29
[QUOTE=someguyouknow]you mean the software provided by logitech?.....
i have tried camorama and it didnt work.....[/QUOTE]

I think it might have but you didn't notice. I've got a Logitech cam as well. It works but for some reason it's really dark. Try starting up camorama and then pointing the webcam directly at a light, you should see a blur, (if you're lucky).

---

### Post by someguyouknow on 2006-07-03
The camorama says there is nothing connected or something.....
i will try the v4l thing.....

---

### Post by someguyouknow on 2006-07-07
ok....
i installed all the v4l and it didnt work....
camorama says that it couldnt connect to the video device (/dev/video0)
i looked around and it seems like some people got this one working but what am i doing wrong?.....

---

