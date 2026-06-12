---
title: "iso movie"
date: 2011-07-25
forum: Multimedia Software
---

### Post by bobk_nyc on 2011-07-25
I have A  iso movie file, I can't seem to open or mount it view. I have tried a few things but it says it is no a iso 6996 format... I can mount it under windows, as a virtual dvd, and play it..d o I need other software?  thanks

---

### Post by Mr. Shannon on 2011-07-25
Try **gnome-mplayer**, It can play non copy protected DVDs and ISO images.  In gnome-mplayer go to **File->Disc->Open DVD from ISO**.  Or the one with menus if needed. Then choose your ISO file.

---

### Post by bobk_nyc on 2011-07-25
mplayer trys to play, but after it starts  nothing happens....maybe I need a codec or something...I think gom player plasyed it. I guess I have to ry that wine , and load gom..thanks for the idea anyway

---

### Post by Mr. Shannon on 2011-07-25
You could try VLC.  I think there are illegal codecs in VLC (depending on your country) but it might work.

---

### Post by bobk_nyc on 2011-07-25
I tried vlc, and same thing, doesn't do anything...I will mess with it...or just use windows, windows is not going anywhere soon...have too much that I need  it for....have a good night

---

### Post by undeuxtrois on 2011-07-28
Hello,

have you tried Gmount-iso ? It's a simple GUI application to mount .iso files. I've used it in the past to play some DVD images with Totem.

sudo apt-get install gmountiso

P.

---

### Post by bobk_nyc on 2011-07-28
> **undeuxtrois said:**
> Hello,

have you tried Gmount-iso ? It's a simple GUI application to mount .iso files. I've used it in the past to play some DVD images with Totem.

sudo apt-get install gmountiso

P.

when I try to open the ISO, gmount tells me the folder is not empty...well I knew that, if there weren't a file, what would I be doing with it....

thanks anyway.

---

### Post by undeuxtrois on 2011-07-29
If I am not mistaken, this error message happens when you are trying to mount an iso to a folder that is not empty. You have to use an empty folder as mount point.

---

### Post by shantiq on 2011-07-29
have you tried AcetoneIso it is in your synaptic it might be able to handle it turn it into a folder of files or whatever it is you wish.... 


```
sudo apt-get install acetoneiso
```


i have found it to be a very supple application...

---

