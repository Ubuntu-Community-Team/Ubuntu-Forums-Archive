---
title: "[SOLVED] QDVDAuthor and qrender"
date: 2008-08-06
forum: Multimedia Software
---

### Post by KoolPenguin on 2008-08-06
I have been trying to install the latest version of QDVDAuthor 1.5 and was able to figure it all out except when I go to install qrender I get an error.  I think it has something to do with ffmpeg.  Here is part of the output after the make install command.

g++ -c -pipe -g -O0 -ggdb3 -Wall -W -D_REENTRANT -DQDVD_RENDER -DQT_XML_LIB -DQT_GUI_LIB -DQT_NETWORK_LIB -DQT_CORE_LIB -DQT_SHARED -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtNetwork -I/usr/include/qt4/QtNetwork -I/usr/include/qt4/QtGui -I/usr/include/qt4/QtGui -I/usr/include/qt4/QtXml -I/usr/include/qt4/QtXml -I/usr/include/qt4 -I/usr/local/include -I.moc -I.ui -o .obj/ffmpeg_enc.o engine/ffmpeg_enc.cpp
engine/ffmpeg_enc.cpp:19:29: error: ffmpeg/avformat.h: No such file or directory
engine/ffmpeg_enc.cpp: In constructor ‘Encoder::FFmpeg::FFmpeg()’:
engine/ffmpeg_enc.cpp:42: error: ‘avcodec_init’ was not declared in this scope
engine/ffmpeg_enc.cpp:45: error: ‘avcodec_register_all’ was not declared in this scope

...and it goes on for about a page, all ffmpeg errors.  Yes ffmpeg is installed.

In the qrender install instructions it says:

QRender is part of the QDVDAuthor suite. It is linked against ffmpeg, and Qt 4.4 and up.

Linking against ffmpeg can become tricky as the API is still somewhat in flux. 

I encourage to link statically against ffmpeg if possible to avoid broken dependencies.


This maybe the problem, but I have no clue how to "link statically" and what it means.

Any help would be greatly appreciated.

Also, I already tried the package from getdeb but it is missing qrender.

Thanks.

---

### Post by KoolPenguin on 2008-08-08
bumping for help...

---

### Post by mocha on 2008-08-08
Did the author of qdvdauthor fix the issues with dual core machines?  I was trying to help him a while back but we didn't get too far.  You might be disappointed after you get it to compile if those issues weren't resolved yet.  I think qdvdauthor is the most promising of dvd authoring tools on Linux, it's a shame that it was unstable with dual cores.  Sadly I've resorted to using TMPGenc DVD Author under wine whenever I need to author with snapshot or animated menu buttons.

---

### Post by KoolPenguin on 2008-08-08
> **mocha said:**
> Did the author of qdvdauthor fix the issues with dual core machines?  I was trying to help him a while back but we didn't get too far.  You might be disappointed after you get it to compile if those issues weren't resolved yet.  I think qdvdauthor is the most promising of dvd authoring tools on Linux, it's a shame that it was unstable with dual cores.  Sadly I've resorted to using TMPGenc DVD Author under wine whenever I need to author with snapshot or animated menu buttons.

I did not know there was a problem with the dual cores.  I used version 1.0x with no problems, but never could get ver. 1.2x to work 100%.  This version I am trying to install seems to work except the parts that require the qrender.

I do agree that QDVDAuthor is the most promising for DVD authoring and sure hope I can figure this qrender issue out or if someone else can get it going and create a deb or rpm of it.

---

### Post by mc4man on 2008-08-09
it took quite some time and was a major **pita** but finally got qrender to build and install on hardy. Ultimately the only 'easy' way was to build _ffmpeg in qrender._ The first time i tried (with the built-in local-ffmpeg.sh) i failed to notice it didn't build. (using a small terminal window) After exhausting all other possibilities (other than removing alot of libav*'s) I went back to it and noticed it wasn't building .

The problem with the script is on line 48 'cd ffmpeg' - the extracted source is named ffmpeg-export-blah, blah. So I deleted the broken link in qrender named ffmpeg and renamed the extracted source ffmpeg. I then ran the rest of the script manually 1 line at a time. (from line 48
Then just simply ran this from terminal

> doug@doug-desktop:~/Desktop/qdvdauthor-1.5.0/qrender$ export STATIC_FFMPEG=1
and then
> doug@doug-desktop:~/Desktop/qdvdauthor-1.5.0/qrender$ qmake && make

That should give you a qmake of this
> Project MESSAGE: Qt version: 4.4.0
Project MESSAGE: Qt is installed in /usr
Project MESSAGE: Using ffmpeg lib from : /home/doug/Desktop/qdvdauthor-1.5.0/qrender/ffmpeg
Project MESSAGE: Using static ffmpeg library

After that it was smooth sailing
> ........-L/usr/lib /home/doug/Desktop/qdvdauthor-1.5.0/qrender/ffmpeg/lib/libavformat.a /home/doug/Desktop/qdvdauthor-1.5.0/qrender/ffmpeg/lib/libavcodec.a /home/doug/Desktop/qdvdauthor-1.5.0/qrender/ffmpeg/lib/libavutil.a /home/doug/Desktop/qdvdauthor-1.5.0/qrender/ffmpeg/lib/libavdevice.a -L/home/doug/Desktop/qdvdauthor-1.5.0/qrender/ffmpeg/lib -lvorbisenc -lbz2 -lQtXml -lQtGui -lQtNetwork -lQtCore -lpthread
doug@doug-desktop:~/Desktop/qdvdauthor-1.5.0/qrender$ sudo make install
[sudo] password for doug: 
install -m 755 -p "../bin/qrender" "/usr/bin/qrender"



note: if libbz2-dev isn't installed do so, it comes up at the end of the make

the reason you can't use hardy's ffmpeg is the absense of this - 'libavdevice'

---

### Post by IanW on 2008-08-09
Alternatively, a pre-compiled .deb of QDVDAuthor 1.5.0 can be got from [http://www.getdeb.net/](http://www.getdeb.net/).

---

### Post by KoolPenguin on 2008-08-09
> **mc4man said:**
> it took quite some time and was a major **pita** but finally got qrender to build and install on hardy. Ultimately the only 'easy' way was to build _ffmpeg in qrender._ The first time i tried (with the built-in local-ffmpeg.sh) i failed to notice it didn't build. (using a small terminal window) After exhausting all other possibilities (other than removing alot of libav*'s) I went back to it and noticed it wasn't building .


Thank you!  I made a slideshow and it worked. :)

Thanks again.

---

### Post by KoolPenguin on 2008-08-09
> **IanW said:**
> Alternatively, a pre-compiled .deb of QDVDAuthor 1.5.0 can be got from [http://www.getdeb.net/](http://www.getdeb.net/).

I tried the one from getdeb and it was missing qrender.  It still was when I checked yesterday, so you won't be able to render and slideshows, etc.

Thanks for the suggestion anyways.

---

