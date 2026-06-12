---
title: "Vlc Segmentation fault and vlc closes when I click next song"
date: 2007-11-30
forum: Multimedia &amp; Video
---

### Post by marisdembovskis on 2007-11-30
1-----

linux@DTDDDSG:~$ vlc
VLC media player 0.8.6c Janus
libdvdnav: Using dvdnav version 0.1.10 from [http://dvd.sf.net](http://dvd.sf.net)
libdvdread: Encrypted DVD support unavailable.
libdvdread: Couldn't find device name.
libdvdnav: Can't read name block. Probably not a DVD-ROM device.
libdvdnav: Unable to find map file '/home/linux/.dvdnav/.map'
libdvdnav:DVDOpenFilePath:findDVDFile /VIDEO_TS/VIDEO_TS.IFO failed
libdvdnav:DVDOpenFilePath:findDVDFile /VIDEO_TS/VIDEO_TS.BUP failed
libdvdread: Can't open file VIDEO_TS.IFO.
libdvdnav: vm: faild to read VIDEO_TS.IFO
*** PULSEAUDIO: Unable to connect: Connection refused
[00000359] oss audio output error: cannot open audio device (/dev/dsp)
Segmentation fault (core dumped)
linux@DTDDDSG:~$ 



What should I do?


2 -----
anybody knows, how to make thin client work with the same keyobard as on server. I installed LTSP, but on server keyboard is fine, but on thin clients is used some other layout, but I need that thin client could use the same as specified in xorg.conf

how can I do that?



/etc/apt/sources.list

deb [http://lv.archive.ubuntu.com/ubuntu/](http://lv.archive.ubuntu.com/ubuntu/) gutsy main restricted
deb-src [http://lv.archive.ubuntu.com/ubuntu/](http://lv.archive.ubuntu.com/ubuntu/) gutsy main restricted

deb [http://lv.archive.ubuntu.com/ubuntu/](http://lv.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted
deb-src [http://lv.archive.ubuntu.com/ubuntu/](http://lv.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse

---

### Post by marisdembovskis on 2007-12-10
Anyone knows the answer?
Im using Amd64  Gutsy version.

linux@DTDDDSG:~$ vlc
VLC media player 0.8.6c Janus
[00000289] main interface: creating VLM
libdvdnav: Using dvdnav version 0.1.10 from [http://dvd.sf.net](http://dvd.sf.net)
libdvdread: Encrypted DVD support unavailable.
libdvdread: Couldn't find device name.
libdvdnav: Can't read name block. Probably not a DVD-ROM device.
libdvdnav: Unable to find map file '/home/linux/.dvdnav/.map'
libdvdnav:DVDOpenFilePath:findDVDFile /VIDEO_TS/VIDEO_TS.IFO failed
libdvdnav:DVDOpenFilePath:findDVDFile /VIDEO_TS/VIDEO_TS.BUP failed
libdvdread: Can't open file VIDEO_TS.IFO.
libdvdnav: vm: faild to read VIDEO_TS.IFO
*** PULSEAUDIO: Unable to connect: Connection refused
Segmentation fault (core dumped)

---

### Post by marisdembovskis on 2007-12-10
solved, by install xine player.

---

