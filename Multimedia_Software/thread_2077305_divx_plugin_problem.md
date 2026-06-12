---
title: "divx plugin problem"
date: 2012-10-28
forum: Multimedia Software
---

### Post by madnbri on 2012-10-28
Hi,
I've switched to xubuntu 12.04 about 2 weeks ago. Works fine, but...
something strange with divx plugin
I've tried to install many kind of packages, like gecko-mediaplayer (multipackage of divx web plugin, realplayer - this is unusable many years of course, windows-mediaplayer and some other), and I've got shockwave flash plugin of course.
Results:
There is no working plugin to play divx. I've checked them all [COLOR=DarkRed]separately[/COLOR] in firefox and google-chrome.
Googled a lot... => I need some help :(

Thanks in advance for Your answers.

Best regards,
m

P.S.: If You need some info about my settings, programs, anything, just ask (something like) this way:
"post the output of " and here comes the command

---

### Post by ajgreeny on 2012-10-28
Do you have every codec that is available for Xubuntu installed, such as all the gstreamer-plugins, good, bad and ugly?

Also for good measure it may be worth enabling the [medibuntu]("http://www.medibuntu.org/") repositories and installing w32codecs or w64codecs (depending on your system architecture).

---

### Post by madnbri on 2012-10-28
> **ajgreeny said:**
> Do you have every codec that is available for Xubuntu installed, such as all the gstreamer-plugins, good, bad and ugly?

Also for good measure it may be worth enabling the [medibuntu]("http://www.medibuntu.org/") repositories and installing w32codecs or w64codecs (depending on your system architecture).

```
~$ sudo apt-cache show gstreamer-plugin*|grep Package
Package: libgstreamer-plugins-base0.10-0
Package: libgstreamer-plugins-base0.10-0
Package: libgstreamer-plugins-base0.10-dev
Package: libgstreamer-plugins-base0.10-dev
Package: qtgstreamer-plugins
Package: libgstreamer-plugins-bad0.10-0
Package: libgstreamer-plugins-bad0.10-0
Package: libgstreamer-plugins-bad0.10-dev
Package: libgstreamer-plugins-bad0.10-dev
``````
sudo apt-cache search gstreamer-plugins
libgstreamer-plugins-base0.10-0 - GStreamer libraries from the "base" set
libgstreamer-plugins-base0.10-dev - GStreamer development files for libraries from the "base" set
qtgstreamer-plugins - GStreamer plugins from QtGStreamer
libgstreamer-plugins-bad0.10-dev - GStreamer development files for libraries from the "bad" set
libgstreamer-plugins-bad0.10-0 - GStreamer shared libraries from the "bad" set
```I've already installed.

I am trying suggested medibuntu...

---

### Post by madnbri on 2012-10-28
> **ajgreeny said:**
> Do you have every codec that is available for Xubuntu installed, such as all the gstreamer-plugins, good, bad and ugly?

Also for good measure it may be worth enabling the [medibuntu]("http://www.medibuntu.org/") repositories and installing w32codecs or w64codecs (depending on your system architecture).

medibuntu is almost good. Plays voice only.

---

### Post by madnbri on 2012-10-28
> **madnbri said:**
> medibuntu is almost good. Plays voice only.

But not in 12.10. I do not know why, but the packages of this version are clear.

---

