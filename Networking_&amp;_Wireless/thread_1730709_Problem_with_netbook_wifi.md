---
title: "Problem with netbook wifi"
date: 2011-04-16
forum: Networking &amp; Wireless
---

### Post by quodscath on 2011-04-16
I have installed ubuntu netbook on an hp pavilion dm1-3120 but when i try to connect to wifi, it doesn't show any acces point.

Following some posts i've managed to make it show acces points, but when I try to connect to one of them it waits endlessly and nevers connects.

The network card is a ralink rt539f.

I would be very gratefully if someone coul help me.
Thank you.

---

### Post by uncaspi on 2011-04-16
First you must search the threads for your  ralink card to see if there is a driver problem connected to it.

---

### Post by espressobeanie on 2011-04-16
Here are all the RALINK Linux Drivers you can download.
[http://web.ralinktech.com/ralink/Home/Support/Linux.html](http://web.ralinktech.com/ralink/Home/Support/Linux.html)

If that doesn't work, look at aircrack-ng. It's possible that they have tutorials on how to setup that driver. Usually all you have to do is extract the package, run './configure', then 'make && make install' for the driver to compile.

---

### Post by skyant on 2011-05-11
Hi,

Maybe you already found out: the instructions in this thread 

[http://ubuntuforums.org/showthread.php?p=10452987#post10452987](http://ubuntuforums.org/showthread.php?p=10452987#post10452987) 

worked for me. :)

---

