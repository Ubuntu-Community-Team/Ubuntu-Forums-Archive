---
title: "SMB and AFP shares not working after power outages. I/O error?"
date: 2011-07-31
forum: Networking &amp; Wireless
---

### Post by rubicks on 2011-07-31
I posted the other day about my AFP shares not working:
[http://ubuntuforums.org/showthread.php?t=1815071](http://ubuntuforums.org/showthread.php?t=1815071)

i was able to mount my SMB shares, but I didn't actually try to transfer data.  I tried to move some data off my linux box to my mac, but i got a finder error 36. which i believe is a input/output error.


I got further proof of that when i was going through some directories and got this:
ls: reading directory .: Input/output error

so i'm gonna guess that whatever input/output errors are happening is what is causing AFP and SMB to not work properly.

---

### Post by rubicks on 2011-07-31
also, tried connecting from a windows 7 computer.  can't copy files over from there either.  some directories that i know have files aren't showing the files inside.

---

