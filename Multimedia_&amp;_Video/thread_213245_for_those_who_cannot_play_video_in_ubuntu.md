---
title: "for those who cannot play video in ubuntu"
date: 2006-07-11
forum: Multimedia &amp; Video
---

### Post by koasd on 2006-07-11
first you must tweak Your Repository List.Then Install General-Purpose Libraries and Tools by "sudo apt-get install totem-xine vorbis-tools sox faad lame \\imagemagick ffmpeg mjpegtools".After that,you Install Gstreamer Libraries by
"sudo apt-get install gstreamer0.8-plugins-multiverse \\gstreamer0.8-ffmpeg gstreamer0.8-mad gstreamer0.8-plugins \\
 gstreamer0.8-lame".Once you have installed all the Gstreamer libraries, open a terminal and type: $ gst-register-0.8
to register all of the Gstreamer plug-ins on your system.

There are a number of multimedia formats that are encumbered by special licenses that require the user to leverage Windows codec libraries on their Linux system to play back the file. Some of these include QuickTime and Windows Media formats. In certain countries, it may be illegal to play files via these codecs, so open up your checkbook, call up your lawyer, and have a chat before proceeding. Then, open a terminal window and grab a copy of the w32codecs .deb file from [ftp://ftp.nerim.net/debian-marillat/pool/main/w/w32codecs/](ftp://ftp.nerim.net/debian-marillat/pool/main/w/w32codecs/) and install the .deb:

$ wget [ftp://ftp.nerim.net/debian-marillat/pool/main/w/w32codecs/w32codecs_](ftp://ftp.nerim.net/debian-marillat/pool/main/w/w32codecs/w32codecs_) 
               
               20050412-0.0_i386.deb
$ sudo dpkg -i w32codecs_20050412-0.0_i386.deb

---

### Post by crispy_420 on 2006-07-12
Wouldn't it be easier to add the proper repositories than manually add files? Just an opinion though. Then you can get more media players, updates, etc.

---

