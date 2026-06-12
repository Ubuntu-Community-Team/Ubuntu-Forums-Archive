---
title: "Problem with Comprehensive Multimedia &amp; Video Howto"
date: 2009-03-05
forum: Multimedia Software
---

### Post by zookrider on 2009-03-05
When I get to the installation step I try to run this code
> sudo apt-get remove gnash gnash-common libflashsupport mozilla-plugin-gnash swfdec-mozilla && sudo apt-get install alsa-oss faac faad flashplugin-nonfree gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse gstreamer0.10-pitfdll libavcodec-unstripped-51 libmp3lame0 non-free-codecs sun-java6-fonts sun-java6-jre sun-java6-plugin unrar
and I get this response
> Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package gnash is not installed, so not removed
Package gnash-common is not installed, so not removed
Package icedtea-gcjwebplugin is not installed, so not removed
E: Couldn't find package libflash-mozplugin
I tried running this code
> sudo rm /var/lib/apt/lists/partial/*
and all I recieved was
> rm: cannot remove `/var/lib/apt/lists/partial/*': No such file or directory
I also made sure that the Medibuntu, Universe and Multiverse repositories are enabled. 

Please help.

---

### Post by zookrider on 2009-03-05
Ttt

---

### Post by mc4man on 2009-03-06
You could post into that thread if no answer comes up here, Why don't you try the command starting at 
> sudo apt-get install alsa-oss faac faad ......

and maybe leave out flashplugin-nonfree (you could leave this also

---

