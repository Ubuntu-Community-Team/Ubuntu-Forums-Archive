---
title: "[SOLVED] (JPEG library not found)"
date: 2008-02-07
forum: Multimedia &amp; Video
---

### Post by thornate on 2008-02-07
I'm trying to install Eye of Gnome 2.20.4 but when configuring, I get the error message
> configure: WARNING: *** JPEG loader will not be built (JPEG library not found) ***
configure: error:
*** Checks for JPEG loader failed. You can build without it by passing
*** --without-libjpeg to configure but some programs using GTK+ may
*** not work properly
Why would this be? The current version of EOG (2.20.1) works fine.

---

### Post by jrib on 2008-02-07
Why install something not in the repos?  What exactly is wrong with the version in the repositories?

In any case, you probably need to do ```
sudo apt-get build-dep eog
``` to get the dependencies you need.  But as I said, I don't recommend installing things by compiling them when they are already available from the repositories.

---

### Post by thornate on 2008-02-08
The version that comes with Ubuntu has one or two niggles that irritate me. I figured I'd try to get the most recent version to see if they're solved.

The code you posted won't work as that will resolve dependancies for the current version of EOG, not the one that I want to install.

---

### Post by jrib on 2008-02-08
> **thornate said:**
> The code you posted won't work as that will resolve dependancies for the current version of EOG, not the one that I want to install.

You are correct that it satisfies the dependencies for the package in the repositories, however, the dependencies usually do not change between small version changes.  Try it, because I just did and ./configure completed without error.

---

### Post by thornate on 2008-02-12
Ah, I see what you mean. Makes sense.

> E: Unable to find a source package for eog
Am I correct in assuming that this would be because there are no dev packages for EOG in Synaptic?

---

### Post by jrib on 2008-02-12
It means you need to enable the source repositories (system -> administration -> software sources).  In /etc/apt/sources.list, it means you need deb-src lines for every deb line

---

### Post by thornate on 2008-02-15
That made it work. Thanks.

---

