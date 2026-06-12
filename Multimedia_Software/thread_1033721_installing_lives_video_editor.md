---
title: "installing lives video editor"
date: 2009-01-07
forum: Multimedia Software
---

### Post by 9ine0h5ive on 2009-01-07
Hi Ive been using Ubuntu 8.10 for the past 3 months. Ive found the applications in the software libraries to be sufficient for my needs. However i haven't been able to find a good video editor (something along the lines of Imovie, not very hard to use but acceptable for most tasks). I previously tried Pitivi but found it lacking in features. Recently a friend recommended LIVES. I have tried to download the .deb package from the LIVES website but found through experience and user comments that the .deb file does not install properly. I have been trying to install it through a binary but have been unsuccessful. It happily chugs along until it gets to "checking for GTK". Heres what happens when I try to install by hand

huma@huma-laptop:~/lives-0.9.9.5$ ./configure
.........
.........
.........
checking for GTK... configure: error: Package requirements (gtk+-2.0 >= 2.4.0) were not met:

No package 'gtk+-2.0' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables GTK_CFLAGS
and GTK_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

huma@huma-laptop:~/lives-0.9.9.5$ 

What am I doing wrong and what should I do to get the installation to work??? 

(I am currently using kernel version 2.6.27-9-generic)

---

### Post by roberto.eiberle on 2009-01-10
look for gtk+ in synaptic and install, run ./configure again - keep synaptic open, you may need more packages just install everything configure asks for. it works!

---

### Post by 9ine0h5ive on 2009-01-11
No dice. i tired it and it still wont work :(:(

the problem is that I already have GTK installed and it still wont work!!!

---

### Post by Kylie on 2009-12-17
I am having a problem as well. :(

Here's a picture of what shows whenever I open Lives: 
link :[http://i45.tinypic.com/14b3qma.png](http://i45.tinypic.com/14b3qma.png)

I've already installed xmms/audacious and dvgrab as well but they can't be detected.

Thank you!

---

