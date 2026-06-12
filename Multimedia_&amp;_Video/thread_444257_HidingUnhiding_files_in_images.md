---
title: "Hiding/Unhiding files in images"
date: 2007-05-15
forum: Multimedia &amp; Video
---

### Post by Shampyon on 2007-05-15
I used the command ***cat "picture.gif" "sound.mp3" > "combined.gif"*** to hide a sound file inside an image. I have no idea how to do the reverse and seperate the image and sound file.

Any help?

---

### Post by SeanHodges on 2007-05-15
There are a number of ways, the 2 files are basically combined so that the mp3 data is directly after the image data

One easy way is to "tail" to read the last N bytes of your combined file, and output it to a file:

First, find out the size of your mp3 file in bytes, then...

tail -c XXX combined.gif > out.mp3

(where XXX is the size of your mp3 file in bytes)

---

### Post by hunt.topher on 2008-06-30
Steghide is a Linux/Windows tool that makes the process a bit simpler - you won't need to remember the bytesize, etc.
[http://steghide.sourceforge.net/](http://steghide.sourceforge.net/)

However the website hasn't been updated recently...

---

