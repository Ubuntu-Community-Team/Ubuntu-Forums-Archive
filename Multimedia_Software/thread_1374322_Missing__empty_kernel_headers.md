---
title: "Missing / empty kernel headers"
date: 2010-01-06
forum: Multimedia Software
---

### Post by !win on 2010-01-06
I'm trying to compile the latest pvrusb2 to get support for the 16kb firmware of a new Hauppauge hvr-1950.  Unfortunately, when I try to compile it following the directions on [www.isely.net/pvrusb2/setup.html]("http://www.isely.net/pvrusb2/setup.html") it starts smooth then starts spitting a long chain of errors that seem to stem from the first few, namely:
```
/build/pvrusb2-mci-20091124/driver/pvrusb2-devattr.c:42:22: error: tda18271.h: No such file or directory
/build/pvrusb2-mci-20091124/driver/pvrusb2-devattr.c:43:21: error: tda8290.h: No such file or directory
/build/pvrusb2-mci-20091124/driver/pvrusb2-devattr.c:44:26: error: tuner-simple.h: No such file or directory
```I can locate the first two files but when I check them, I get:
```
file /usr/src/linux-headers-2.6.31-17-generic/include/config/media/tuner/tda18271.h
/usr/src/linux-headers-2.6.31-17-generic/include/config/media/tuner/tda18271.h: empty
file /usr/src/linux-headers-2.6.31-17-generic/include/config/media/tuner/tda8290.h
/usr/src/linux-headers-2.6.31-17-generic/include/config/media/tuner/tda8290.h: empty
``` and I can't locate tuner-simple.h at all.  Clearly missing and empty headers aren't going to resolve anything.  I've installed everything I can think of to ensure the files are there but they are still missing. I have the following installed but no joy locating the files.
linux-headers-2.6.31-17
linux-headers-2.6.31-17-generic
build-essential
linux-source-2.6.31
If anyone knows in what package the files reside, I would be very appreciative.  Oh, if it matters, I'm running the 64 bit kernel

---

### Post by !win on 2010-01-08
Simple solution: I pulled the headers from a suse box and used those.  Of course that was after I installed twice, once from cd and again from dvd, both times with a live internet connection.  I don't know why ubuntu doesn't provide all the kernel headers.  It isn't like there is some need to save a few kB or even MB.

---

