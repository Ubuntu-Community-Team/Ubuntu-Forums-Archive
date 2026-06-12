---
title: "Manual Codec Download"
date: 2007-11-28
forum: Multimedia &amp; Video
---

### Post by SuperTeece on 2007-11-28
While deployed I have no way of conecting Ubuntu to the web to install new packages. While I have found a way to manually download and install from the repositories, i.e. [http://ubuntuforums.org/showthread.php?t=19175](http://ubuntuforums.org/showthread.php?t=19175) and I also have a a kind soul burning the repos to DVD for me, I still don't know which packages I need.

At the moment I would like to be able to play .avi files. Which packages are needed to get me going?

Thanks,

SuperTeece

---

### Post by jasmuz on 2007-11-28
Hey!

I recommend you use VLC for the most of your multimedia needs, its dependencies are the following:

vlc
  Depends: libaa1 (>= 1.2)
  Depends: libatk1.0-0 (>= 1.13.2)
  Depends: libc6 (>= 2.6-1)
  Depends: libcaca0 (>= 0.99.beta11-1)
  Depends: libcairo2 (>= 1.4.0)
  Depends: libcdio6
  Depends: libcucul0 (>= 0.99.beta11-1)
  Depends: libdbus-1-3 (>= 1.1.1)
  Depends: libdbus-glib-1-2 (>= 0.74)
  Depends: libfontconfig1 (>= 2.4.0)
  Depends: libfreetype6 (>= 2.3.5)
  Depends: libfribidi0 (>= 0.10.7)
  Depends: libgcc1 (>= 1:4.2.1)
  Depends: libgl1
  Depends: libgl1-mesa-glx
  Depends: libglib2.0-0 (>= 2.14.0)
  Depends: libglu1
  Depends: libglu1-mesa
  Depends: libgtk2.0-0 (>= 2.12.0)
  Depends: libice6 (>= 1:1.0.0)
  Depends: libiso9660-4
  Depends: libjpeg62
  Depends: libnotify1 (>= 0.4.4)
  Depends: libnotify1-gtk2.10
  Depends: libpango1.0-0 (>= 1.18.2)
  Depends: libpng12-0 (>= 1.2.13-4)
  Depends: libsdl-image1.2 (>= 1.2.5)
  Depends: libsdl1.2debian (>= 1.2.10-1)
  Depends: libsm6
  Depends: libstdc++6 (>= 4.2.1)
  Depends: libtar
  Depends: libtiff4
  Depends: libvcdinfo0 (>> 0.7.23)
  Depends: libvlc0 (>= 0.8.6.release.c)
  Depends: libwxbase2.6-0 (>= 2.6.3.2.1.5ubuntu12)
  Depends: libwxgtk2.6-0 (>= 2.6.3.2.1.5ubuntu12)
  Depends: libx11-6
  Depends: libxcomposite1 (>= 1:0.3-1)
  Depends: libxcursor1 (>> 1.1.2)
  Depends: libxdamage1 (>= 1:1.1)
  Depends: libxext6
  Depends: libxfixes3 (>= 1:4.0.1)
  Depends: libxi6
  Depends: libxinerama1
  Depends: libxosd2 (>= 2.2.13)
  Depends: libxrandr2 (>= 2:1.2.0)
  Depends: libxrender1
  Depends: libxv1
  Depends: ttf-dejavu
  Depends: vlc-nox (= 0.8.6.release.c-0ubuntu5)
  Depends: zlib1g (>= 1:1.2.3.3.dfsg-1)

---

