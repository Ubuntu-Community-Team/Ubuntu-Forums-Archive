---
title: "Install VLC player offline to UBUNTU"
date: 2009-01-09
forum: Multimedia Software
---

### Post by csirimanne on 2009-01-09
I try to install VLC player to UBUNTU 8.04 which I downloaded last month. But in my home PC I was unable to set up the Internet connection and it only work on windows(dial up connection). Then I download VLC player for UBUNTU and tried to install it. But it will displayed several error messages that not install dependencies in my machine. Then I try to download them and try to install. then it says that dependency has another dependencies. So where can I find all the dependencies as one package to install VLC player offline.
Thanks.

---

### Post by mc4man on 2009-01-09
Here's probably the complete list of deps.

 > liba52-0.7.4 libavcodec1d libavformat1d libavutil1d
 libdc1394-13 libdvbpsi4 libdvdnav4 libdvdread3
 libebml0 libfreebob0 libgsm1
 libid3tag0 libiso9660-5 libjack0 libmad0 libmatroska0
 libmodplug0c2 libmpcdec3 libmpeg2-4
 libpostproc1d libsdl-image1.2
 libtar libvcdinfo0 libvlc0
 libwxbase2.6-0 libwxgtk2.6-0
 libxosd2 ttf-dejavu ttf-dejavu-extra
 vlc-nox vlc-plugin-pulse
 
(note there are some suggested that I didn't look at, most commonly used -  libdvdcss2

[http://packages.medibuntu.org/hardy/libdvdcss2.html](http://packages.medibuntu.org/hardy/libdvdcss2.html) 

You would have to search  each one out here, get the hardy version and put them all in one folder on your install.

[http://packages.ubuntu.com/hardy-updates/vlc](http://packages.ubuntu.com/hardy-updates/vlc)

Then cd to the folder and run
```
sudo dpkg -i *.deb
```


What may be easier would be to boot to a 8.04.1 live cd on a machine with internet.

Go to system -> administration -> software sources, disable the cd and have the first 4 choices under 'ubuntu software ' enabled.

Reload and then in a terminal go 
```
sudo apt-get install vlc
```

When it's done go to /var/cache/apt/archives and copy all the .debs to a folder on a flash drive (or just copy the archives folder it self- skip any error messages

You could also try adding medibuntu to sources list before installing vlc, you'd get some updated libav's instead of repo versions.

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

---

### Post by Tomatz on 2009-01-09
Mc4man's post is excellent and should work fine but maybe you should check out apt on cd:

[http://aptoncd.sourceforge.net/](http://aptoncd.sourceforge.net/)

---

