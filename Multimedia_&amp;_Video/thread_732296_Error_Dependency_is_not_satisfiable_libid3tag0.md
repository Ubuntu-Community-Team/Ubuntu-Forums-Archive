---
title: "Error: Dependency is not satisfiable: libid3tag0"
date: 2008-03-22
forum: Multimedia &amp; Video
---

### Post by Lourie2 on 2008-03-22
How do I overcome the following?  I am trying to install GStreamer plugins from the "ugly" set so I can play mp3's.

gstreamer0.10-plugins-ugly:
 Depends: libid3tag0 (>=0.15.1b) but it is not installable
 Depends: libmad0 (>=0.15.1b) but it is not installable

---

### Post by hhhhhx on 2008-03-22
```
sudo apt-get install libid3tag0
```
 
also you will want to make sure that all the sourses are open,  software sourses, under adminastration

---

### Post by Lourie2 on 2008-03-22
Thanks, nice to have someone like you to help beginners like myself!

---

