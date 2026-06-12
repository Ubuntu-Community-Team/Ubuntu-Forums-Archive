---
title: "How do you install Losslesscut"
date: 2018-10-29
forum: Multimedia Software
---

### Post by jacatone on 2018-10-29
I'm using Ubuntu Mate 18.04. The simple video cutter/joiner Losslesscut isn't in the repositories so I downloaded it instead. Can't seem to figure out how to install it. Anyone know?

---

### Post by Holger_Gehrke on 2018-10-29
Unzip, change to the directory, run './LosslessCut', open an avi file, get told it's not in a 'friendly format' (It doesn't tell you which those are, but I assume it's the ones chromium can show), wait about an hour for a (lossy) conversion, try to cut, erase it.

<rant> This is about the worst piece of bloat I've ever seen. A ~90MB zip that decompresses to ~260MB, containing three executables, two of them fully statically linked version of ffmpeg (~64MB) and ffprobe (ditto) to do the real work (those files are a bit unnecessary, installing ffmpeg from the repositories is a better idea), the third (~80MB) is a complete web browser with less than 100KB Javascript baked into it  to do the UI. This is everything that's wrong with trying to use Javascript on the desktop.</rant>

Holger

---

### Post by HermanAB on 2018-10-30
Hmm, I occasionally try a different video editor and always come back to my favourite most hated one: kdenlive.

---

### Post by jacatone on 2018-10-31
I'm using Ubuntu 18.04 LTS. Been trying to install losslesscut following the instructions listed below, but get an error message. Can anyone tell me how to fix this?

[https://www.linuxhelp.com/how-to-install-lossless-cut-v1-11-0-on-linuxmint-18-03/](https://www.linuxhelp.com/how-to-install-lossless-cut-v1-11-0-on-linuxmint-18-03/)

root@jacatone:/home/jacatone/Downloads/LosslessCut-linux-x64# ./LosslessCut
./LosslessCut
: error while loading shared libraries: libgconf-2.so.4: cannot open shared object file: No such file or directory

---

### Post by mc4man on 2018-10-31
```
sudo apt install libgconf-2-4
```
If you get a new error on another then run 
> ldd /path/to/LosslessCut  and look for any 'not found'  (s)
You can usually determine package from the .so that's missing

---

### Post by ajgreeny on 2018-11-01
Threads merged.

**Please do not create duplicate posts;** it is confusing for all including you and dilutes the forum's ability to help.

---

### Post by jacatone on 2018-11-07
Only seems to work if I click on the launch icon within the losslesscut folder. How do I permanently install it and get a menu icon?

---

