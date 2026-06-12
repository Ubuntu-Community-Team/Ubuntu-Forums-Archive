---
title: "BMP XMMS plugin Scizzor How To"
date: 2007-06-10
forum: Multimedia &amp; Video
---

### Post by keziahhh on 2007-06-10
hello, i'm absolute ubuntu beginner, i found a plugin for beep media player named scizzor, i think for me it's perfect, but it is not available as debian package (only *.tar.gz). Can somebody tell em how i can insatll that plugin? Does somebody know about another pitch/speed plugin. with windows i got a plugin named chronotron,it was perfect, it was possible to change key and speed while playing mp3s etc. tried the instructions shown in article [http://ubuntuforums.org/archive/index.php/t-159335.html](http://ubuntuforums.org/archive/index.php/t-159335.html), downloaded the beep-config etc., but without success. the foolwing error is in terminal:

admini@desktoppc:~/scizzor$ make

                make xmms for xmms plugin.
                make bmp for bmp plugin.
                make both for both plugins.

admini@desktoppc:~/scizzor$ make bmp
gcc -Wall -O2 -DBMP `beep-config --cflags` -fPIC -c scizzor.c -o scizzor.lo
/bin/sh: beep-config: command not found
/bin/sh: gcc: command not found
make: *** [bmp] Fehler 127

---

