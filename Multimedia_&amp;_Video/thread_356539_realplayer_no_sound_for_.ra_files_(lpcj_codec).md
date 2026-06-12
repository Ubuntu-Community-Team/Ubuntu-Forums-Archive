---
title: "realplayer: no sound for .ra files (lpcj codec)"
date: 2007-02-08
forum: Multimedia &amp; Video
---

### Post by roel46 on 2007-02-08
Hoi,

I installed realplayer because I want to play an .ra (real audio) file. The installed realplayer can play music, but it rejects .ra files, saying: "Component Missing: The player does not have the capabilities to play back this content. Details: The following components are required: lpcj.".

I did the realplaying installation more or less like described in the community contributed documentation in "https://help.ubuntu.com/", i.e. the following 5 commands:

$ sudo apt-get install gstreamer0.10-pitfdll gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse gxine libxine-main1 libxine-extracodecs ogle ogle-gui
$ wget -c [http://www.debian-multimedia.org/pool/main/w/w32codecs/w32codecs_20061022-0.0_i386.deb](http://www.debian-multimedia.org/pool/main/w/w32codecs/w32codecs_20061022-0.0_i386.deb)
$ sudo dpkg -i w32codecs_20061022-0.0_i386.deb
$ wget -c [http://www.youmortals.com/ubuntu/packages/realplayer_10.0.7-0.0_i386.deb](http://www.youmortals.com/ubuntu/packages/realplayer_10.0.7-0.0_i386.deb)
$ sudo dpkg -i realplayer_10.0.7-0.0_i386.deb

Note: .ra files found at "http://www.maths.tcd.ie/gaeilge/general.html#A1.1"

Any ideas? TIA, Roel.

---

