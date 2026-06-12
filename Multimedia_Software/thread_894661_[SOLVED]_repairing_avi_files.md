---
title: "[SOLVED] repairing avi files"
date: 2008-08-19
forum: Multimedia Software
---

### Post by co0lingFir3 on 2008-08-19
hello,
i recently discovered vlc saying that one of my video files was corrupt and asked if it should fix it. i clicked yes and it worked fine. however the next time i'd like to open the file, vlc was asking the same question. so vlc is able to repair a avi file but does not make that permanent.
so i looked for a program to fit my need and found [divfix++]("http://divfixpp.sourceforge.net/home.htm"). the only repo i found has a very old version of divfix in it so i wanted to compile it from source but ended up having this error:
```
 sudo make
`wx-config --cxx` `wx-config --cxxflags` -c -Os src/DivFix++App.cpp -o src/DivFix++App.o
/bin/sh: wx-config: not found
/bin/sh: wx-config: not found
/bin/sh: -c: not found

```
since there was no configure file i tried "sudo make" right away.
can anyone help me fixing this problem or suggest another program which can repair avi files.

thanks a lot!

---

### Post by shirilover on 2008-08-19
Looks like you need to install the wxwidgets development files.
Or, you could try using avidemux to repair the file.

---

### Post by co0lingFir3 on 2008-08-19
i downloaded and installed avidemux. but how do i repair avi files with it? simply copying the audio and video stream into a new avi container? or is there a better way?

---

### Post by shirilover on 2008-08-20
That's pretty much it, just save to either a new name or new location.

---

### Post by co0lingFir3 on 2008-08-20
Ok. Thanks for your help!

---

