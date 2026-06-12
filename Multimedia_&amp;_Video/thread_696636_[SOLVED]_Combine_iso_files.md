---
title: "[SOLVED] Combine iso files"
date: 2008-02-14
forum: Multimedia &amp; Video
---

### Post by skippi90 on 2008-02-14
I downloaded 2 rar files. Each containing part of an iso.

How can I combine the two iso files to make the disc?

---

### Post by erginemr on 2008-02-14
Fire up the terminal, change to the directory where these two files are located and use "echo" and ">" (output redirection) to combine them in order to a big file. 

Say, if you have the rar files are on your desktop. Then
```
cd ~/Desktop
echo part-1.rar part-2.rar > complete.rar
```

To extract the iso from the rar file, you may need to install the rar package:
Main Menu -> Admin -> Synaptic

Select the main, universe, multiverse repositories from Synaptic settings, press update, find the "rar" package and install it.

When you are done, double-click on the rar file, file-foller (gnome archive manager) will fire up, extract the iso from there. 

Alternatively, the "rar" package should support combining split files. Its man file may contain some info on this:
```
man rar
```

---

