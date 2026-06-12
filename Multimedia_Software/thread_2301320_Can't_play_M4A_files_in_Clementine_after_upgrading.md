---
title: "Can't play M4A files in Clementine after upgrading Xubuntu to 15.04"
date: 2015-11-01
forum: Multimedia Software
---

### Post by MinceyPie on 2015-11-01
The title says it all, I use Clementine frequently but ever since I upgraded Xubuntu to 15.04 I can't play any M4A files but other files such as MP3's or FLAC's work perfectly.

Running Clementine in terminal and playing an M4A file results in this error:
"*** stack smashing detected ***: clementine terminated"
This is followed by it crashing and Ubuntu reporting a "System Error"

I've reinstalled and purged Clementine but nothing works, I've tried playing them in VLC and it works perfectly fine.

---

### Post by mc4man on 2015-11-01
Clementine  in Ubuntu uses gstreamer 0.10, it's likely that. m4a needs the ffmpeg plugin which isn't available so,
1. Find a ppa that has a gst-1.0 port of Clementine 
2. Use this ppa to provide ffmpeg  support for current ubuntu clem packages thru 15.04 
(no 15.10 packages yet, may do so when I'm no longer homeless..
[https://launchpad.net/~mc3man/+archive/ubuntu/gstffmpeg-keep](https://launchpad.net/~mc3man/+archive/ubuntu/gstffmpeg-keep)

---

### Post by MinceyPie on 2015-11-02
Okay so far I think I have found a port of Clementine running gst-1.2. However, running "cmake .." results in this:

> CMake Error at /usr/share/cmake-3.2/Modules/FindPackageHandleStandardArgs.cmake:138 (message):
  Could NOT find Qt4 (missing: QT_QTOPENGL_INCLUDE_DIR QT_QTOPENGL_LIBRARY)
  (found suitable version "4.8.6", minimum required is "4.5.0")
Call Stack (most recent call first):
  /usr/share/cmake-3.2/Modules/FindPackageHandleStandardArgs.cmake:374 (_FPHSA_FAILURE_MESSAGE)
  /usr/share/cmake-3.2/Modules/FindQt4.cmake:1333 (FIND_PACKAGE_HANDLE_STANDARD_ARGS)
  CMakeLists.txt:36 (find_package)


-- Configuring incomplete, errors occurred!
See also "/home/alex/Clementine/bin/CMakeFiles/CMakeOutput.log".
See also "/home/alex/Clementine/bin/CMakeFiles/CMakeError.log".
alex@alex:~/Clementine/bin$ cmake ..
CMake Error at /usr/share/cmake-3.2/Modules/FindPackageHandleStandardArgs.cmake:138 (message):
  Could NOT find Qt4 (missing: QT_QTOPENGL_INCLUDE_DIR QT_QTOPENGL_LIBRARY)
  (found suitable version "4.8.6", minimum required is "4.5.0")
Call Stack (most recent call first):
  /usr/share/cmake-3.2/Modules/FindPackageHandleStandardArgs.cmake:374 (_FPHSA_FAILURE_MESSAGE)
  /usr/share/cmake-3.2/Modules/FindQt4.cmake:1333 (FIND_PACKAGE_HANDLE_STANDARD_ARGS)
  CMakeLists.txt:36 (find_package)


-- Configuring incomplete, errors occurred!
See also "/home/alex/Clementine/bin/CMakeFiles/CMakeOutput.log".
See also "/home/alex/Clementine/bin/CMakeFiles/CMakeError.log".


Clementine GST-1.2= [https://github.com/clementine-player/Clementine/tree/gstreamer-1.2](https://github.com/clementine-player/Clementine/tree/gstreamer-1.2)

---

### Post by Yellow Pasque on 2015-11-02
If you're attempting to build it yourself, this will help:
```
sudo apt-get build-dep clementine
```

---

### Post by MinceyPie on 2015-11-02
> **Temüjin said:**
> If you're attempting to build it yourself, this will help:
```
sudo apt-get build-dep clementine
```

Thanks for your help but that unfortunately leads to yet another dead end with a rabbit hole of dependencies :/.
After checking up how to fix broken packages/dependencies I've done "--fix-broken" but that doesn't seem to help.

> Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have unmet dependencies.
 libglew-dev : Depends: libgl1-mesa-dev but it is not going to be installed or
                        libgl-dev
               Depends: libglu1-mesa-dev but it is not going to be installed or
                        libglu-dev
 libqt4-opengl-dev : Depends: libgl1-mesa-dev but it is not going to be installed
                     Depends: libglu1-mesa-dev but it is not going to be installed
E: Build-dependencies for clementine could not be satisfied.



---

### Post by Yellow Pasque on 2015-11-04
Then perhaps it would be easier to use a pre-built version from Clementine: [https://launchpad.net/~me-davidsansome/+archive/ubuntu/clementine-dev](https://launchpad.net/~me-davidsansome/+archive/ubuntu/clementine-dev)
(I verified that this version is using gstreamer 1.0.)

---

### Post by MinceyPie on 2015-11-05
> **Temüjin said:**
> Then perhaps it would be easier to use a pre-built version from Clementine: [https://launchpad.net/~me-davidsansome/+archive/ubuntu/clementine-dev](https://launchpad.net/~me-davidsansome/+archive/ubuntu/clementine-dev)
(I verified that this version is using gstreamer 1.0.)

Excellent! It's working now. Now I can actually listen to music :).
Thanks!

---

### Post by ntdoherty on 2016-01-30
> **MinceyPie said:**
> Excellent! It's working now. Now I can actually listen to music :).
Thanks!

Works for me too! Yes! Thank you! 
I have a bunch of older files from when I still used iTunes (mouthvomit). Haven't gone back to convert all of them because life but I hated when I was all set to listen to some oldies and Clementine was just freezing or crashing. Can't find a player I like better period...tried gmusicbrowser but was unintuitive for me. Anyway, you guys rock again.

---

