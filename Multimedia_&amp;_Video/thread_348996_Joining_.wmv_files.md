---
title: "Joining .wmv files"
date: 2007-01-29
forum: Multimedia &amp; Video
---

### Post by 22.glenroy on 2007-01-29
I am trying to join .wmv files together to create a single video file. I have tried cat 01.wmv 02.wmv 03.wmv 04.wmv > joined.wmv. This appears to work in that the resultant file is the same size as the combined size of the individual files, when I play the file back it only plays the 01.wmv part.

Any ideas would be greatly appreciated by an Ubuntu learner

---

### Post by CameronCalver on 2007-01-29
you should try avidemux
```
sudo apt-get install avidemux
```

---

### Post by 22.glenroy on 2007-01-30
Thanks for the response I have installed avidemux but I cannot get it to open .wmv files.

---

### Post by HenrikAn on 2007-01-30
If you look at *Help -> Show builtin support* in Avidemux you will see that Win32 i NOT checked. 
I don't know if an Avidemux binary with win32 support exists.

---

### Post by 22.glenroy on 2007-01-30
I have solved the problem using mencoder but thanks for the responses

---

### Post by HenrikAn on 2007-01-31
Good for you!:D 
Could you please post how you did it for future reference?

---

### Post by sh4d3z on 2007-02-24
you fixed it using mencoder?
i tried putting one of my porns together using this
```
cat *1.avi *2.avi *3.avi ...  > 1-5.avi
```
but i ran into the same prob you were having...
then i discovered the append option in avidemux
that's fine for avi but what about other format?
like some i have in wmv (god i hate that container!)
i ran this which i used for real media worked fine...
```
mencoder *1.wmv -ovc lavc -oac mp3lame -o 1.avi
```
but this was no good i got a message telling me mencoder crashed...
and when i looked at the resulting avi it is in such a bad quality that it is not viewable at all
maybe that line though might work for other peeps though

---

### Post by disturbedite on 2007-02-24
thats how i do it.  *I* on the other hand am not at liberty to mention the content of my video. :mrgreen:

---

