---
title: "audio, video codecs, restricted format, and win32codecs"
date: 2007-03-19
forum: Multimedia &amp; Video
---

### Post by gizmoarena on 2007-03-19
i need all gstreamer packages (specially ugly and bad) for playing mp3s, wma and other restricted formats. 

is there any link where I can download those debian packages?  I dont have internet connection at home right now, so I cannot download it from repo. 

what are the packages for playing mpeg, divx, avi, vob, rm files? can anyone give me a download link?

please let me know, as soon as possible. do not forward into another thread if possible.

*NOTE: I am using ubuntu drapper drake DVD.*

---

### Post by Kobalt on 2007-03-19
You can download the w32codecs package from there : 
```
wget -c http://www.debian-multimedia.org/pool/main/w/w32codecs/w32codecs_20061022-0.0_i386.deb
```
For the other packages (there are a lot) you can download them manually from there : [http://packages.ubuntu.com](http://packages.ubuntu.com) , here is a list of the packages you'll need for dapper, in order to play mp3s for example : 
> gstreamer0.10-pitfdll gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse gxine libxine-main1 libxine-extracodecs ogle ogle-gui

---

