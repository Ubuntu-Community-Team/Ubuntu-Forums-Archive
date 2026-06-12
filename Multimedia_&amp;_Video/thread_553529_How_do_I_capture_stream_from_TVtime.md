---
title: "How do I capture stream from TVtime?"
date: 2007-09-17
forum: Multimedia &amp; Video
---

### Post by jnutter on 2007-09-17
I want to capture and encode the stream from TVtime. TVtime is easy to use and the picture quality is great. I'm using a Hi-8 video camera and the S-video in. 

So far the only way I've been able to capture anything is in VLC, but the resolution is low and the picture has a blurry area at the bottom - not nearly as good as TVtime. 

The end goal is to use my TV card to digitize videos from my Hi-8 video camera, encode them into something common, edit them and burn a DVD of my home movies. 

If anyone has accomplished this, please let me know how. 

I've been trying to install DVR from source (found at [http://www.pierrox.net/dvr/](http://www.pierrox.net/dvr/)) becuase I can't find it in Synaptic. Seems like it should be there since it's listed here: [http://packages.ubuntu.com/feisty/graphics/dvr](http://packages.ubuntu.com/feisty/graphics/dvr) and I have all the repositories enabled - but I can't find it. 

Here's the output I'm getting when I try to make DVR

:root@john-desktop:/home/john/dvr-3.99.3.tar.bz2/dvr-3.99.3/src# make
cpp -MM -DPREFIX="\"/usr/local\"" -DDVR_VERSION="\"3.99.3\"" -W -Wall -I. -I../build -I/usr/include/qt -pthread -I/usr/include/gstreamer-0.10 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/libxml2   -g -MT ../build/*.o device_selection.cpp dvr_control.cpp dvr.cpp main.cpp property_editor.cpp qlistbox_codec.cpp qlistview_codec_property.cpp tab_audio_config.cpp tab_codec_config.cpp tab_general.cpp tab_monitoring.cpp tab_video_config.cpp > ../build/*.d || (rm -f ../build/*.d; exit 1)
cpp: too many input files
mkdir -p ../build
uic -impl ../build/ui_dvr_control.h dvr_control.ui > ../build/ui_dvr_control.cpp
/bin/sh: uic: not found
make: *** [../build/ui_dvr_control.cpp] Error 127


I'm a newb - and  I really don't know how to make files from source. After roughly 16hours of reading, searching, copying and pasting I'm ready to ask for help. Please take pity on me and and either help me get DVR going or point me at some other package that can do what I want. 

I'm running X86-64 Ubuntu

Thanks

John Nutter

---

