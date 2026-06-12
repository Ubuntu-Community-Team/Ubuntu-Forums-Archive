---
title: "Real player 10 issue"
date: 2007-01-22
forum: Multimedia &amp; Video
---

### Post by DavidTingdahl on 2007-01-22
I have problems running Real player 10.
Either I get the message "Segmentation fault (core dumped)"
or otherwise nothing happens at all (have to press ctrl-c to get back to the prompt)
Anyone else with the same issues? I am quite new to Ubuntu

---

### Post by taurus on 2007-01-22
How did you install it, by hand, by synaptic/apt-get/aptitude, or by automatix2?

---

### Post by DavidTingdahl on 2007-01-22
I Downloaded the file 'RealPlayer10GOLD.bin' and installed it manually

---

### Post by taurus on 2007-01-22
Where did you install it to?  You didn't get any error message when you installed it?

```
./RealPlayer10GOLD.bin
-or-
sudo ./RealPlayer10GOLD.bin
```

---

### Post by DavidTingdahl on 2007-01-22
No, there were no Error messages.
I installed in the usr/bin/RealPlayer. Here is the directory

david@Spruttibangbang:/usr/bin/RealPlayer$ ls -all
total 647
drwxr-sr-x 11 root root    432 2007-01-21 21:50 .
drwxr-xr-x  3 root root  38272 2007-01-22 18:17 ..
drwxr-sr-x  2 root root     48 2007-01-21 21:50 Bin
drwxr-sr-x  2 root root    416 2006-07-19 06:17 codecs
drwxr-sr-x  2 root root    112 2006-07-19 06:17 common
drwxr-sr-x  2 root root     48 2006-07-19 06:17 doc
-rw-r--r--  1 root root  24198 2007-01-21 21:50 install.log
drwxr-sr-x  2 root root     80 2006-07-19 06:17 lib
-rwxr-xr-x  1 root root  11286 2006-07-19 06:17 LICENSE
drwxr-sr-x  2 root root    112 2006-07-19 06:17 mozilla
drwxr-sr-x  2 root root   1648 2006-07-19 06:17 plugins
drwxr-sr-x  2 root root    112 2006-07-19 06:17 postinst
-rw-r--r--  1 root root   3047 2006-07-19 06:17 README
-rwxr-xr-x  1 root root   2479 2007-01-21 21:50 realplay
-rwxr-xr-x  1 root root   2486 2007-01-21 21:50 realplay.bak
-rwxr-xr-x  1 root root 570344 2006-07-19 06:17 realplay.bin
drwxr-sr-x  7 root root    432 2006-07-19 06:17 share
david@Spruttibangbang:/usr/bin/RealPlayer$ 
david@Spruttibangbang:/usr/bin/RealPlayer$ realplay

david@Spruttibangbang:/usr/bin/RealPlayer$ realplay
Segmentation fault
david@Spruttibangbang:/usr/bin/RealPlayer$

---

