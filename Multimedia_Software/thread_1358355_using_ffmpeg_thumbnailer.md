---
title: "using ffmpeg thumbnailer"
date: 2009-12-18
forum: Multimedia Software
---

### Post by manit on 2009-12-18
i am using ubuntu 9.04.
I wanted thumbnail for flv.
I installed ffmpegthumbnailer.
In order to verify its working I ran
$ffmpegthumbnailer -i ed.flv -o ed.png
It worked & gave 128x72 png image.
I read from [http://code.google.com/p/ffmpegthumbnailer/wiki/Faq](http://code.google.com/p/ffmpegthumbnailer/wiki/Faq) about using ffmpegthumbnailer.
so i ran gconf-editor
and edited desktop/gnome/thumbnailers/video@x-flv
and edited value of string 'command' to "/usr/bin/ffmpegthumbnailer -s %s -i %i -o %o -c png -f -t 10"(without double quotes).
Still thumbnail not visible.
Where am I going wrong ?

---

### Post by hellomoto on 2009-12-20
I am also having the exact same problem, does anyone have a solution?

---

