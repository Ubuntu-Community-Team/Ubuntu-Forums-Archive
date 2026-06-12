---
title: "Totem + Create Screenshot Gallery"
date: 2010-01-01
forum: Multimedia Software
---

### Post by kg87 on 2010-01-01
happy new year guys, 

I've made it my new years resolution to sort out my video collection :lolflag:

I know totem can create a png montage with the frames of a video, however, I've only been able to create one at a time. If i told you i have 621 videos to deal with, you can understand why im asking this question. 

Is there anyway in which i can script this, so i can can do the entire directory, name the png the title of the film while my pc is doing nothing?, I've looked at the "man" for totem, and there doesnt seem to be anything in there. 

Or alternatively, suggest alternate software, which can do the whole thing without scripting?! I've already looked at GframeCapture, but that doesn't do it also. 

Thanks in advance,

---

### Post by chewearn on 2010-01-02
mplayer can be scripted to do what you want.

E.g. command to use:
[http://lists.mplayerhq.hu/pipermail/mplayer-users/2004-August/047831.html](http://lists.mplayerhq.hu/pipermail/mplayer-users/2004-August/047831.html)

---

### Post by Gourgi on 2010-01-02
look at this one too [http://cli-apps.org/content/show.php/Movie+Thumbnailer?content=74676](http://cli-apps.org/content/show.php/Movie+Thumbnailer?content=74676)

---

### Post by kg87 on 2010-01-02
thanks guys, but i found out about totem-video-thumbnailer

"totem-video-thumbnailer" --size 200 -l -g 30 /mnt/HARD\ DRIVE/E/Movies/<<filename>> <<imagefilename>>

but, i wondered how i can make this work with multiple files, short of "catting" the ls of the folder into a text file, then writing the same command for each file, is there anyway of automating this?! like using variables (%f) etc.?!

---

### Post by kg87 on 2010-01-06
just a quick bump, as havent been able to solve the issue :D

---

### Post by chewearn on 2010-01-06
[http://www.cyberciti.biz/faq/bash-loop-over-file/](http://www.cyberciti.biz/faq/bash-loop-over-file/)

---

