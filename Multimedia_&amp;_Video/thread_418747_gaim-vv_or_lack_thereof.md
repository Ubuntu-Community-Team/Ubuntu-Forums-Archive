---
title: "gaim-vv or lack thereof"
date: 2007-04-22
forum: Multimedia &amp; Video
---

### Post by go_dragons on 2007-04-22
I want to find an instant messenger that supports video and voice. While looking on the internet I found some information about gaim-vv that looked promising, and I am trying to install it. FIrst I looked for repositories and I was able to find these that claimed to have the program:

deb [http://people.debian.org/~smimram/debian](http://people.debian.org/~smimram/debian) unstable main
deb-src [http://people.debian.org/~smimram/debian](http://people.debian.org/~smimram/debian) unstable main
deb [http://perso.ens-lyon.fr/samuel.mimram/debian](http://perso.ens-lyon.fr/samuel.mimram/debian) unstable main

It turns out that none of those actually did have the gaim-vv app. Perhaps they have had it in the past but got rid of it for some reason? After that failed, I tried to compile the source code. Before I could even ./configure it shat out some errors about missing glib development files. apparently there was a mismatch of information somewhere about which version of glib I have and I dont know how to fix it. Here is what I saw: 

checking for GLIB - version >= 2.0.0... 
*** 'pkg-config --modversion glib-2.0' returned 2.13.0, but GLIB (2.12.11)
*** was found! If pkg-config was correct, then it is best
*** to remove the old version of GLib. You may also be able to fix the error
*** by modifying your LD_LIBRARY_PATH enviroment variable, or by editing
*** /etc/ld.so.conf. Make sure you have run ldconfig if that is
*** required on your system.
*** If pkg-config was wrong, set the environment variable PKG_CONFIG_PATH
*** to point to the correct configuration files
no
configure: error:
*** GLib 2.0 is required to build Gaim; please make sure you have the GLib
*** development headers installed. The latest version of GLib is
*** always available at [http://www.gtk.org/](http://www.gtk.org/).


If anyone knows what I am doing wrong, or of a debian/ubuntu repository where I could find gaim-vv that would be a great help. Or, if there is another program that I do not know of, that would also be a great help! ubuntuforums has always been a great source of helpful information.

Thanks!

---

