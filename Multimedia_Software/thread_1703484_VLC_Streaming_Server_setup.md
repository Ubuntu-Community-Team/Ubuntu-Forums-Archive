---
title: "VLC Streaming Server setup"
date: 2011-03-09
forum: Multimedia Software
---

### Post by usn on 2011-03-09
G'day,

I just got myself a Virtual Private Network (server) to run a VLC streaming server from.

Following this tutorial here:

[http://n00tz.net/2008/07/vlc-media-server-ubuntu-hardy/](http://n00tz.net/2008/07/vlc-media-server-ubuntu-hardy/)

However, when i try to install vlc via sodu apt-get install vlc i get this:
[PHP]root@usntv:~# sudo apt-get install vlc
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following extra packages will be installed:
  liba52-0.7.4 libass4 libaudio2 libavcodec52 libavformat52 libavutil49
  libcddb2 libdca0 libdvbpsi5 libdvdnav4 libdvdread4 libebml0 libenca0
  libfaad2 libgsm1 libiso9660-7 liblua5.1-0 libmad0 libmatroska0 libmng1
  libmodplug0c2 libmpcdec3 libmpeg2-4 libpostproc51 libqtcore4 libqtgui4
  libschroedinger-1.0-0 libsdl-image1.2 libswscale0 libtar libtwolame0
  libupnp3 libvcdinfo0 libvlc2 libvlccore2 libx264-85 libxcb-keysyms1 vlc-data
  vlc-nox vlc-plugin-pulse
Suggested packages:
  nas libdvdcss2 debhelper fakeroot build-essential qt4-qtconfig
  mozilla-plugin-vlc videolan-doc
Recommended packages:
  head
The following NEW packages will be installed:
  liba52-0.7.4 libass4 libaudio2 libavcodec52 libavformat52 libavutil49
  libcddb2 libdca0 libdvbpsi5 libdvdnav4 libdvdread4 libebml0 libenca0
  libfaad2 libgsm1 libiso9660-7 liblua5.1-0 libmad0 libmatroska0 libmng1
  libmodplug0c2 libmpcdec3 libmpeg2-4 libpostproc51 libqtcore4 libqtgui4
  libschroedinger-1.0-0 libsdl-image1.2 libswscale0 libtar libtwolame0
  libupnp3 libvcdinfo0 libvlc2 libvlccore2 libx264-85 libxcb-keysyms1 vlc
  vlc-data vlc-nox vlc-plugin-pulse
0 upgraded, 41 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B/25.8MB of archives.
After this operation, 75.4MB of additional disk space will be used.
Do you want to continue [Y/n]? y
debconf: apt-extracttemplates failed: Bad file descriptor
Extracting templates from packages: 73%debconf: apt-extracttemplates failed: Bad file descriptor
Extracting templates from packages: 100%
Selecting previously deselected package liba52-0.7.4.
(Reading database ... 30%dpkg: unrecoverable fatal error, aborting:
 malloc failed (8192 bytes): Cannot allocate memory
E: Problem executing scripts DPkg::Post-Invoke 'if [ -d /var/lib/update-notifier ]; then touch /var/lib/update-notifier/dpkg-run-stamp; fi; if [ -e /var/lib/update-notifier/updates-available ]; then echo > /var/lib/update-notifier/updates-available; fi '
E: Sub-process returned an error code
E: Sub-process /usr/bin/dpkg returned an error code (2)
[/PHP]Any idea how using putty (from Windows) i can install VLC and setup its webserver, so that I can at least set it up from there via some kind of visual interface?

Any help would be much appreciated.

---

