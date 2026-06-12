---
title: "Converting .it to ogg vorbis"
date: 2008-02-11
forum: Multimedia Production
---

### Post by Ragzouken on 2008-02-11
Could someone direct me to, if one exists, an easy tool for converting music in the .it format to either ogg vorbis, or .wav so I convert it to ogg?

---

### Post by gsmanners on 2008-02-11
You should be able to set the output plugin of XMMS or Audacious or some media player like that to "Disk Writer" which should save the file as a wav file when you tell it to play the file.

From there, you can simply go to a console and use oggenc (in vorbis-tools):

oggenc audio.wav

---

### Post by Ragzouken on 2008-02-12
Thanks!

---

### Post by Creative2 on 2008-02-12
sudo apt-get install mp32ogg

and fuoco tools 
[http://fuocotools.byethost13.com/index.php](http://fuocotools.byethost13.com/index.php)
or here
[http://ubuntuforums.org/showthread.php?t=652843](http://ubuntuforums.org/showthread.php?t=652843)

---

