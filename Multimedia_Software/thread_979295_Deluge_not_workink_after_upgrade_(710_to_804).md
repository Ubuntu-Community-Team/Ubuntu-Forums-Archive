---
title: "Deluge not workink after upgrade (710 to 804)"
date: 2008-11-11
forum: Multimedia Software
---

### Post by Ordep_ on 2008-11-11
Upgraded Unubtu 7.10 to 8.04 and now Deluge won't start. Went to ADD/REMOVE and it was "not installed". I added and then ended up with 2 Deluges! None of them working. Everytime I start to run it it shows as loading in the taskbar but then nothing. Here's the output from the terminal:

ordep@ordep-laptop:~$ deluge
Traceback (most recent call last):
  File "/usr/bin/deluge", line 45, in <module>
    import deluge.core
  File "/usr/lib/python2.5/site-packages/deluge/s core.py", line 58, in <module>
    import deluge_core
ImportError: libboost_filesystem-gcc-mt-1_33_1.so.1.33.1: cannot open shared object file: No such file or directory



I haven't try to uninstall it from the terminal cause i dont know how to do it. I would really like to uninstall everything and then get it from the add/remove but I'm really dumb so if you can help me with codes I'll appreciate it, just dont tell me "remove this and change this for that" cause I dont know anything but to copy and paste codes from the forum. Thanks.

---

### Post by SuperSonic4 on 2008-11-11
I just get the deb from their site since it's ahead of the repos

[http://deluge-torrent.org/downloads.php](http://deluge-torrent.org/downloads.php)

---

### Post by Ordep_ on 2008-11-11
That solved the problem, Thanks.

---

