---
title: "Amarok support for flv, rm, mkv, wma, wmv"
date: 2009-01-31
forum: Multimedia Software
---

### Post by belaviyo on 2009-01-31
Hi

I recently move from windows to kubunutu, in windows I had used Jetaudio which was one of best ever player I have seen, I hear from lots of blogs that Amarok is the best player for linux OS, but I have problem with it, 

1. how to improve Amarok to support flv, rm, mkv, wma, wmv

2. Is it support video or not ?

If not is there any player like jetaudio for linux, something which support most of popular video/Audio formats

Tnx

---

### Post by wolfen69 on 2009-01-31
copy and paste the following into a terminal:

```
sudo wget http://www.medibuntu.org/sources.list.d/intrepid.list --output-document=/etc/apt/sources.list.d/medibuntu.list
```then
```
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update
```
then go to synaptic package manager and search for gstreamer. install gstreamer good, bad, and ugly plugins. also install w32codecs for wma playback. for flash, go here [http://get.adobe.com/flashplayer/](http://get.adobe.com/flashplayer/) and download the .deb (8.04+) for ubuntu and click to install.

i use vlc player for media. it's awesome.

---

