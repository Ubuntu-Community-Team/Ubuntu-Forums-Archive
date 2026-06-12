---
title: "ubuntustudio 7.10 + dvdstyler"
date: 2008-02-16
forum: Multimedia &amp; Video
---

### Post by klein de usa on 2008-02-16
hi 
i had ubuntu 7.10 installed and then upgraded to ubuntustudio 7.10 everything went well, except the jack server isn't working but that is another question.
i'm trying to install dvdstyler, i downloaded the two files from here [http://www.dvdstyler.de/downloads.html](http://www.dvdstyler.de/downloads.html) for .deb (wxsvg-1.0b8-i386.deb) and (DVDStyler-1.6.0-i386.deb) when i try installing them i get error messages:


for wxsvg-1.0b8-i386.deb  i get
error: dependency is not satisfiable: libpango 1.0-0 

 
for DVDStyler-1.6.0-i386.deb i get 
error: dependency is not satisfiable: dvd+rw-tools

what am i doing wrong?

any ideas ?

---

### Post by gsmanners on 2008-02-17
DVDStyler has a number of big dependencies (like DvdAuthor, MJPEG Tools, and mpgtx).

Your best bet might be to check out this thread:

[http://ubuntuforums.org/showthread.php?t=644160](http://ubuntuforums.org/showthread.php?t=644160)

---

### Post by klein de usa on 2008-02-17
THANK YOU Gsmanners worked like a charm !

---

