---
title: "debian vlc without intf wx, why?"
date: 2008-08-29
forum: Multimedia Software
---

### Post by quasitr0n on 2008-08-29
I take the vlc from debian binary repository.
But I don't understand why it be installed within only command line interface ncurses. I want use it with X interfave such as wx.
Please, say me good repository and how to installing that.
I tried the next ways..
```
#cat /etc/apt/sources.list
 #deb http://download.videolan.org/pub/videolan/debian sid main
 #deb-src http://download.videolan.org/pub/videolan/debian sid main
deb http://http.us.debian.org/debian stable main contrib non-free
deb http://ftp.us.debian.org/debian/ stable main non-free contrib
```
```
# vlc --list | grep interface
VLC media player 0.8.6a Janus
starting VLC root wrapper... using UID 0 (root)
***************************************
* Running VLC as root is discouraged. *
***************************************

 It is potentially dangerous, and might not even work properly.
  http                  HTTP remote control interface
  gestures              Mouse gestures control interface
  showintf              Show interface with mouse
  telnet                VLM remote control interface
  hotkeys               Hotkeys management interface
  lirc                  Infrared remote control interface
  rc                    Remote control interface
  ncurses               Ncurses interface
  dummy                 Dummy interface function
  xosd                  XOSD interface
```

---

### Post by quasitr0n on 2008-08-29
^
|
up

---

### Post by shirilover on 2008-08-29
Have you looked in your applications menu to see if VLC was there?
Have you tried running wxvlc anyway?
You should probably update to 0.8.6h-4.
wxvlc is now a dummy package that installs the vlc package.

---

