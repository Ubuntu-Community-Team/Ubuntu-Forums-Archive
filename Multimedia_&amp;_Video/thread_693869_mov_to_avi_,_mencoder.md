---
title: "mov to avi , mencoder ??"
date: 2008-02-11
forum: Multimedia &amp; Video
---

### Post by zebralinux on 2008-02-11
hi, I have an .mov file of 1.4 G.
Now I want to convert that file into an .avi
preferable with xvid as video encoder.
And I want the size of the new file to be the same
as input file: 1.4 G.

Any working mencoder line that fix this ???

---

### Post by disturbedite on 2008-02-11
x264 would be better, since xvid development is dead...
try using avidemux.  its a gui/frontend/editor to various multimedia programs/libs.

---

### Post by ubuntu-freak on 2008-02-11
WinFF is awesome. It's a GUI frontend for FFmpeg. Check out part 4 of my [how-to](http://ubuntuforums.org/showthread.php?t=661833). Might be good to look at part 1 also and make sure you have all the packages you need. It will skip anything you already have.
 
Nathan

---

### Post by disturbedite on 2008-02-12
or you could just install the winff package from getdeb.net....

---

### Post by gsmanners on 2008-02-12
Using mencoder in a console is also a good choice if you like tweaking.

[http://gentoo-wiki.com/HOWTO_Mencoder_Introduction_Guide](http://gentoo-wiki.com/HOWTO_Mencoder_Introduction_Guide)

---

