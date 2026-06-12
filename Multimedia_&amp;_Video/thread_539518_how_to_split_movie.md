---
title: "how to split movie?"
date: 2007-08-31
forum: Multimedia &amp; Video
---

### Post by snake444 on 2007-08-31
i have movie that hes size is 1.4gb and i need to split it to two files of 700mb
someone told me to do it with avidemux and i enabled the option to auto split files that more than 700mb but when i save the movie it saves him to 1.4gb file and doesnt splits
so is there another program that can split? or i did something wrong with avidemux??

---

### Post by Amazona aestiva on 2007-08-31
See the first link in my signature.
There you can find _Kdenlive_.

---

### Post by yabbies on 2007-08-31
have you tried doing it manually with avidemux?

set marker A at the beginning of your cut
set marker B at the end of your cut
and then save the selection

---

### Post by snake444 on 2007-08-31
i tried manually but it saves the first 50% of the movie as 780~mb
so it doesnt good
and now ill try what Amazona aestiva said

---

### Post by snake444 on 2007-08-31
Amazona i have problems with installing the program in gusty
maybe there is another program from ubuntu add\remove that can split a movie?
or a way that avidemux can split it ?

---

### Post by yabbies on 2007-08-31
Autosplit

Using File->AVI Muxer Options, you can specify a file size in megabytes. Each time that file size is reached and an intra frame is present, Avidemux will create a new file. You will end up with foo.avi.1, foo.avi.2 etc.

**As the new file must begin at an I-frame, the file size you specify is only accurate to within about 5 megabytes. **

---

