---
title: "vlc wont play avi"
date: 2006-07-28
forum: Multimedia &amp; Video
---

### Post by linuxnoob40 on 2006-07-28
installed vlc player and it works fine except for avi format where i gte blank screen the progress bar moves and i hear sound just no picture. ubuntu 6.06 amd 32

any fixes for this that i have missed?

---

### Post by ajgreeny on 2006-07-28
Have you installed the win32 codecs?  Without them you will have lots of problems playing many different multimedia files.  Go to:-
[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)
for more useful info on this, and good luck.

---

### Post by linuxnoob40 on 2006-07-28
have downloaded all codecs that i can find and still no picture:confused:

---

### Post by linuxnoob40 on 2006-07-29
dpkg: error processing w32codecs_20060611-0.0_i386.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 w32codecs_20060611-0.0_i386.deb

---

### Post by PokerFacePenguin on 2006-08-04
I think this is a simple error.

I believe you copy and pasted the instructions exactly, but you have downloaded a newer version, so the filenames don't match.  

Double check to see that you are dpkging the right filename.

---

### Post by burquedout on 2006-08-04
Avi doesn't really say what kind of file it is.  It could be divx, xvid or any number of other formats but for win32 codecs you could also use automatix and remember this is proprietary softeware you are downloading and if you are in the US it is illegal.

---

