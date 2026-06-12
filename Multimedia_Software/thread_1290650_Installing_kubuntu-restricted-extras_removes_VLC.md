---
title: "Installing kubuntu-restricted-extras removes VLC?"
date: 2009-10-13
forum: Multimedia Software
---

### Post by WindPower on 2009-10-13
Hi, I'm trying to get a DVD to play (works out-of-the-box on Windows so it's not a hardware or region code issue). With VLC, the drive starts spinning but the Play Pause button shifts back to the "Play" button after a few seconds and the drive stops spinning. With mplayer, I get the few introduction videos (before the menu) and then mplayer exists, saying it's the "end of the file". I ran sudo apt-get install libdvdread4 (it said I already had the package) and then sudo /usr/share/doc/libdvdread4/install-css.sh which seems to install libdvdcss2, but that did no visible change, VLC still can't play the DVD. Then I stumbled across [this wiki page](https://help.ubuntu.com/community/RestrictedFormats) on Restricted formats; I guess that if VLC can't play it, it's probably a restricted format or something. So I install kubuntu-restricted-extras because I'm on Kubuntu, and...
```
$ sudo apt-get install kubuntu-restricted-extras
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following extra packages will be installed:
  flashplugin-installer flashplugin-nonfree icedtea6-plugin libavcodec-extra-52 libavcodec-unstripped-52 libavutil-extra-49 libdirac0c2a
  libopenjpeg2 libx264-67 nspluginwrapper ttf-mscorefonts-installer
Suggested packages:
  msttcorefonts ttf-xfree86-nonfree xfs
Recommended packages:
  libxine1-ffmpeg
The following packages will be REMOVED:
  libavcodec52 libavutil49 vlc vlc-nox
The following NEW packages will be installed:
  flashplugin-installer flashplugin-nonfree icedtea6-plugin kubuntu-restricted-extras libavcodec-extra-52 libavcodec-unstripped-52
  libavutil-extra-49 libdirac0c2a libopenjpeg2 libx264-67 nspluginwrapper ttf-mscorefonts-installer
0 upgraded, 12 newly installed, 4 to remove and 0 not upgraded.
Need to get 3406kB of archives.
After this operation, 8389kB disk space will be freed.
Do you want to continue [Y/n]?
```
It asks me if I want to remove VLC? :confused: Then how am I going to play videos after that?

Running Kubuntu 9.04 64-bit on MacBook Pro 5,3.

---

