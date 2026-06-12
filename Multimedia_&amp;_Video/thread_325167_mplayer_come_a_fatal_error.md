---
title: "mplayer come a fatal error"
date: 2006-12-25
forum: Multimedia &amp; Video
---

### Post by LaoLiulaoliu on 2006-12-25
My kernel is 2.6.19.1(the official kernel don't support my chipset),i use ubuntu 6.10-amd64.my motherboard chipset is nvidia Gforce 6100 nforce 405
I have install mplayer and a lot of decoder.
sudo apt-get install gstreamer0.8-plugins
sudo apt-get install gstreamer0.8-lame
sudo apt-get install gstreamer0.8-ffmpeg
sudo apt-get install w32codecs
sudo apt-get install libdivx4linux
sudo apt-get install lame
sudo apt-get install sox
sudo apt-get install ffmpeg
sudo apt-get install mjpegtools
sudo apt-get install vorbis-tools
but still can not use mplayer to play the file rmvb...
when I play with mplayer ,it pop a message box show the fatal error
ERROR opening/initialing the selected video_out(-vo) device.
I have download /home/lotus/essential-amd64-20061203.tar.bz2,put the folder "essential-amd65-20061202" in /usr/share/mplayer ,but it is useless.

---

### Post by pay on 2006-12-25
I don't think that there is a 64bit version of the real codec (apart from older ones). I maybe wrong though. You probably need the official realplayer for that file.

---

### Post by LaoLiulaoliu on 2006-12-25
but you are right ,i force it to install use the command  dpkg -i --force-architecture packagename_i386.deb
but maybe it does not work.

---

### Post by pay on 2006-12-25
A 32 bit codec needs a 32bit media player to work.

---

