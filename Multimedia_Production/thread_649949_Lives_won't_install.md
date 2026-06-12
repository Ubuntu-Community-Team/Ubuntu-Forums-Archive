---
title: "Lives won't install"
date: 2007-12-25
forum: Multimedia Production
---

### Post by etech1 on 2007-12-25
Hello all,
I've been trying to install the movie editor LiVES from the source, I'm new to Linux but have gotten closer to getting it going but seem to have run into a problem. I've pasted the last part of the configure log below, it says package gtk=-2.0 is missing. Searching all in the package manager fails to find it although there are many other gtk entries. It looks like the environmental variables can be modified to ignore the error but I'm not sure how to do this.

Any help would be appreciated!

checking for GTK... configure: error: Package requirements (gtk+-2.0 >= 2.4.0) were not met:

No package 'gtk+-2.0' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables GTK_CFLAGS
and GTK_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

mark@mark-desktop:~/Documents/lives-0.9.8.6$

---

### Post by taurus on 2007-12-25
Looks like you need the developing package for GTK, libgtk+-dev.  Search for libgtk in synaptic and install the developing package before you try to compile that app again.

---

### Post by FakeOutdoorsman on 2007-12-26
The LiVES [readme]("http://www.xs4all.nl/%7Esalsaman/lives/README") lists the requirements.  You may also need to install: mplayer, imagemagick, perl, and libjpeg62.

---

