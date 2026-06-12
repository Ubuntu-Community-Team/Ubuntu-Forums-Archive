---
title: "UNable to install VLC"
date: 2007-10-27
forum: Multimedia &amp; Video
---

### Post by mity on 2007-10-27
I am running 7.10.

i am trying to install VLC. 

Typed  "sudo aptitude install vlc"

Response

"Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Building tag database... Done      
The following packages are BROKEN:
  vlc vlc-nox 
The following NEW packages will be automatically installed:
  liba52-0.7.4 libdvbpsi4 libdvdnav4 libdvdread3 libebml0 libiso9660-4 
  libmatroska0 libmpeg2-4 libtar libvcdinfo0 libvlc0 libwxbase2.6-0 
  libwxgtk2.6-0 libxosd2 videolan-doc 
The following NEW packages will be installed:
  liba52-0.7.4 libdvbpsi4 libdvdnav4 libdvdread3 libebml0 libiso9660-4 
  libmatroska0 libmpeg2-4 libtar libvcdinfo0 libvlc0 libwxbase2.6-0 
  libwxgtk2.6-0 libxosd2 videolan-doc 
0 packages upgraded, 17 newly installed, 0 to remove and 0 not upgraded.
Need to get 21.2MB of archives. After unpacking 45.2MB will be used.
The following packages have unmet dependencies:
  vlc-nox: Depends: libavcodec1d (>= 0.cvs20070307) which is a virtual package.
           Depends: libavformat1d (>= 0.cvs20070307) which is a virtual package.
           Depends: libavutil1d (>= 0.cvs20070307) which is a virtual package.
           Depends: libdc1394-13 which is a virtual package.
           Depends: libgsm1 (>= 1.0.10) which is a virtual package.
           Depends: libid3tag0 (>= 0.15.1b) which is a virtual package.
           Depends: libmad0 (>= 0.15.1b) which is a virtual package.
           Depends: libmodplug0c2 (>= 1:0.7-4.1) which is a virtual package.
           Depends: libmpcdec3 which is a virtual package.
           Depends: libpostproc1d (>= 0.cvs20070307) which is a virtual package.
  vlc: Depends: libsdl-image1.2 (>= 1.2.5) which is a virtual package.
       Depends: ttf-dejavu which is a virtual package.
Resolving dependencies...
The following actions will resolve these dependencies:

Keep the following packages at their current version:
vlc [Not Installed]
vlc-nox [Not Installed]

Score is -9872"

what am i doing wrong?

i tried intalling the package, but i got this response

"vlc:
 Depends: vlc-nox but it is not going to be installed
 Depends: libsdl-image1.2 (>=1.2.5) but it is not installable
 Depends: ttf-dejavu  but it is not installable"

what can i do?

thanks

---

### Post by stanigator on 2007-10-27
Two suggestions:

1. Try using aptitude or synaptic or adept in the gui form and check vlc to have all the dependencies installed automatically, or
2. try installing the dependencies manually

If these two suggestions didn't work, then I'm not too sure what's going on.

---

### Post by taurus on 2007-10-27
Maybe you need to uncomment all the repos by removing the # in /etc/apt/sources.list.

```
gksudo gedit /etc/apt/sources.list
```
Then, run

```
sudo aptitude update
sudo aptitude install vlc
```

---

