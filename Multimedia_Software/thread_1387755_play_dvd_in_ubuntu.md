---
title: "play dvd in ubuntu"
date: 2010-01-22
forum: Multimedia Software
---

### Post by alin19 on 2010-01-22
hello guys, i have a problem playing dvd movies, :(

i have tryed:

root@alin-laptop:~# sudo apt-get install ubuntu-restricted-extras
Reading package lists... Done
Building dependency tree       
Reading state information... Done
ubuntu-restricted-extras is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
root@alin-laptop:~# 

root@alin-laptop:~# sudo /usr/share/doc/libdvdread4/install-css.sh


root@alin-laptop:~# sudo apt-get install gstreamer0.10-ffmpeg gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse
Reading package lists... Done
Building dependency tree       
Reading state information... Done
gstreamer0.10-ffmpeg is already the newest version.
gstreamer0.10-plugins-ugly is already the newest version.
gstreamer0.10-plugins-ugly-multiverse is already the newest version.
gstreamer0.10-plugins-bad is already the newest version.
gstreamer0.10-plugins-bad-multiverse is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.


root@alin-laptop:~# sudo apt-get install ubuntu-restricted-extras
Reading package lists... Done
Building dependency tree       
Reading state information... Done
ubuntu-restricted-extras is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
root@alin-laptop:~# sudo apt-get install libdvdcss
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting libdvdcss2 instead of libdvdcss
libdvdcss2 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.


then tryed with: vlc , SMPlayer , xine, gxine , MPlayer Media Player , Media Player ,Amrock 

now when i play with vlc, i get the sound but no image
what can i try next ?

---

### Post by jimmers on 2010-01-22
Try sudo apt-get install w32codecs libdvdcss2

---

### Post by doas777 on 2010-01-22
you probably still need the medibuntu repos for libdvdcss and w32/64codecs.
check out the repository how to here:
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

---

### Post by alin19 on 2010-01-22
thanks, now it is working with xine

---

