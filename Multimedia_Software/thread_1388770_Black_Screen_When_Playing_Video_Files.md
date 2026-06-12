---
title: "Black Screen When Playing Video Files"
date: 2010-01-23
forum: Multimedia Software
---

### Post by ephman on 2010-01-23
so the other day there was an upgrade i did the other day (see files below).  and ever since then the videos i try to play only show up with black a black screen.  youtube videos play however find through the browser.  this issue was happening sporadically before the upgrade, but now it is permanent.  it is happening for every format i tried.  avi, m4v, mpg, etc...  i've also tried plaing the files in different players and the same issue.  the sound does play however, so at least i can listen to things :)

i've tried reinstalling the xorg files, players, and codecs, all to no avail.

has anybody seen this issue before?  the only thing i can imagine from the upgrades that is causing this the xorg upgrades.  but i don't really know.  

any help would be greatly appreciated.  thanks.  ephman

ubuntu 9.10 x64
nvidia 9650m get (195 driver)


Upgraded the following packages:
bind9-host (1:9.6.1.dfsg.P1-3ubuntu0.2) to 1:9.6.1.dfsg.P1-3ubuntu0.3
dnsutils (1:9.6.1.dfsg.P1-3ubuntu0.2) to 1:9.6.1.dfsg.P1-3ubuntu0.3
emerald-tropical-theme (1.5.2.karmic.ppa1+nmu1) to 1.5.3.karmic.ppa1+nmu1
gnome-tropical-theme (1.5.2.karmic.ppa1+nmu1) to 1.5.3.karmic.ppa1+nmu1
gtk-tropical-theme (1.5.2.karmic.ppa1+nmu1) to 1.5.3.karmic.ppa1+nmu1
gzip (1.3.12-8ubuntu1) to 1.3.12-8ubuntu1.1
icon-tropical-theme (1.5.2.karmic.ppa1+nmu1) to 1.5.3.karmic.ppa1+nmu1
libbind9-50 (1:9.6.1.dfsg.P1-3ubuntu0.2) to 1:9.6.1.dfsg.P1-3ubuntu0.3
libdns50 (1:9.6.1.dfsg.P1-3ubuntu0.2) to 1:9.6.1.dfsg.P1-3ubuntu0.3
libdns53 (1:9.6.1.dfsg.P1-3ubuntu0.2) to 1:9.6.1.dfsg.P1-3ubuntu0.3
libexpat1 (2.0.1-4ubuntu1) to 2.0.1-4ubuntu1.1
libisc50 (1:9.6.1.dfsg.P1-3ubuntu0.2) to 1:9.6.1.dfsg.P1-3ubuntu0.3
libisccc50 (1:9.6.1.dfsg.P1-3ubuntu0.2) to 1:9.6.1.dfsg.P1-3ubuntu0.3
libisccfg50 (1:9.6.1.dfsg.P1-3ubuntu0.2) to 1:9.6.1.dfsg.P1-3ubuntu0.3
liblwres50 (1:9.6.1.dfsg.P1-3ubuntu0.2) to 1:9.6.1.dfsg.P1-3ubuntu0.3
metacity-tropical-theme (1.5.2.karmic.ppa1+nmu1) to 1.5.3.karmic.ppa1+nmu1
tropical-theme (1.5.2.karmic.ppa1+nmu1) to 1.5.3.karmic.ppa1+nmu1
wallpaper-tropical-theme (1.5.2.karmic.ppa1+nmu1) to 1.5.3.karmic.ppa1+nmu1
xserver-common (2:1.6.4-2ubuntu4) to 2:1.6.4-2ubuntu4.1
xserver-xorg-core (2:1.6.4-2ubuntu4) to 2:1.6.4-2ubuntu4.1

---

### Post by rjovec on 2010-08-31
Hi Ephman,

it also happened to me and many other people. I purpose you two options:

If you are using vlc, open it and go to: Tools -> preferences -> Video -> change default by X11 or OpenGL.

If you are using Totem, open a terminal and launch: "gstreamer-properties" . You will get a box in which you should change your video preferences to "X window system (without Xv)".

Try it and if it works, we should check this thread as solved. I hope it will save a lot of time for many people!

Roger

---

