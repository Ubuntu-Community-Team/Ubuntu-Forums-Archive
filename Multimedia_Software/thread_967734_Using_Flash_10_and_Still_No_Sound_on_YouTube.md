---
title: "Using Flash 10 and Still No Sound on YouTube??"
date: 2008-11-02
forum: Multimedia Software
---

### Post by Teclas5 on 2008-11-02
I've been trying to find a solution to this and still cant get sound to play when trying to watch videos online. Previously had Flash 9 and experienced the same thing till i added libflashsupport which gave me sound but Firefox kept crashing. Does anyone have a solution that i may try? :confused:

---

### Post by gandaran on 2008-11-02
> **Teclas5 said:**
> I've been trying to find a solution to this and still cant get sound to play when trying to watch videos online. Previously had Flash 9 and experienced the same thing till i added libflashsupport which gave me sound but Firefox kept crashing. Does anyone have a solution that i may try? :confused:
if you got flash 9 to work with libflashsupport then flash 10 should work just fine!
question: did you remove flash 9 and libflashsupport? libflashsupport is not needed for flash 10 ,in fact it conflicts! 
and which ubuntu version, hardy or intrepid?
open terminal and type **locate libflash** post the **full** output here

about solutions there are many just search the forum

---

### Post by Teclas5 on 2008-11-02
Greetings gandaran! Yes, as far as removing both flash 9 and libsupport, i went thru synaptic and removed both. I am using Hardy. My output is:

ernesto@laptop:~$ locate libflash
/home/ernesto/.local/share/Trash/files/libflashsupport_1.0~2219-2_i386.deb
/home/ernesto/.local/share/Trash/info/libflashsupport_1.0~2219-2_i386.deb.trashinfo
/usr/lib/adobe-flashplugin/libflashplayer.so
/usr/lib/openoffice/program/libflash680li.so
/var/cache/apt/archives/libflashsupport_1.9-0ubuntu1_i386.deb


Thanks in advance!

---

### Post by gandaran on 2008-11-03
hi
look, I'm sure theres a easy fix for you, there are a lot of things you can try before you apply one of many fixes for pulseaudio that you can find here on the forum.
yesterday I read a post here by someone that just right clicked the flash video window and sound started working, maybe something simple like that can work for you.
try setting the sound capture to alsa first then oss  or back to the original setting in system » preferences » sound, this is easy and may well work!

---

### Post by Teclas5 on 2008-11-03
Well, it seems to work if i close any other application that i have running at the time like Banshee. Strange that it does that. I guess i will utilize this method till a more permanent solution is found. Either way, i appreciate the help gandaran!

---

### Post by gandaran on 2008-11-04
[http://ubuntuforums.org/showthread.php?t=885437](http://ubuntuforums.org/showthread.php?t=885437)

---

### Post by TORRO89 on 2008-11-04
try system>administration>services and check audio setttings management. worked for me lol

---

### Post by Teclas5 on 2008-11-07
Many thanks gandaran! The link you provided was the solution to my problem. I am still trying to figure out Ubuntu and linux in general so i hope i wasn't too much of a "noobie" pain for you. Funny to think that even though i have to put up with the lag time in getting responses and suggestions to my problems in linux, it is much more palatable than dealing with the issues (viruses and the like; along with running programs that rarely eliminate them) in redmond derived products. Thanks again!:guitar:

---

### Post by Teclas5 on 2008-11-07
Appreciate your suggestion TORRO89! Any and all suggestion are/were not unappreciated!  :)

---

