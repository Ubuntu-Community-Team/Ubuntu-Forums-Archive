---
title: "Is GStreamer available for Ubuntu 21.04, and if it is, then how to install it?"
date: 2021-05-25
forum: Multimedia Software
---

### Post by GwibberFooey on 2021-05-25
My first attempt looks like this:

```
user@localhost:~$ sudo apt install gstreamer
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
E: Unable to locate package gstreamer
```

Because that didn't work, therefor I visited the GStreamer webpage for installing on Linux: [https://gstreamer.freedesktop.org/documentation/installing/on-linux.html?gi-language=c](https://gstreamer.freedesktop.org/documentation/installing/on-linux.html?gi-language=c)
In compliance with the instructions of the aforementioned webpage, my second attempt looks like this:

```
user@localhost:~$ sudo apt-get install libgstreamer1.0-0 gstreamer1.0-plugins-base gstreamer1.0-plugins-good gstreamer1.0-plugins-bad gstreamer1.0-plugins-ugly gstreamer1.0-libav gstreamer1.0-doc gstreamer1.0-tools gstreamer1.0-x gstreamer1.0-alsa gstreamer1.0-gl gstreamer1.0-gtk3 gstreamer1.0-qt5 gstreamer1.0-pulseaudio
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
Package gstreamer1.0-doc is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Package 'gstreamer1.0-doc' has no installation candidate
```

What procedure enables the installation of GStreamer on Ubuntu 21.04?

---

### Post by Yellow Pasque on 2021-05-26
Ubuntu comes with the basic gstreamer packages installed by default. Installing these packages should take care of most gstreamer needs.
```
sudo apt-get install gstreamer1.0-plugins-bad gstreamer1.0-plugins-ugly gstreamer1.0-libav
```

There are some other specialty gstreamer packages, and -dev packages if you need to build software using gstreamer. Synaptic is a useful tool to browse packages and read their descriptions.

---

