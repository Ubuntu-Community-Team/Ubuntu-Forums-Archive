---
title: "Firefox from .tar.gz &amp; embedded videos"
date: 2008-08-25
forum: Multimedia Software
---

### Post by piricoco on 2008-08-25
Hy guys!
I'm using Firefox 2.0.0.16 under Kubuntu Hardy.1 but I can't view WMP & other closed codecs videos embedded in web pages (e.g. [_**these **_](http://h20181.www2.hp.com/plmcontent/NACSC/SML/results.htm?SID=1839150&MEID=3528A65A-05AC-45B9-A726-E430BC6C33F7) videos). My Firefox is installed from binaries, i.e. I downloaded the .tar.gz from Mozilla official site and unpacked it in my home directory. I prefer this way so I just have to copy this dir to have complete portability of my firefox profile, settings and...plugins!
Firstly, I installed mozilla-plugin by synaptic and linked every file (.so & .xpt) from /usr/lib/firefox/plugins/ to my Firefox plugin directory; e.g.:
```
piricoco@compaq:~/Programmi/Firefox/plugins ln -s /usr/lib/firefox/plugins/mplayerplug-in-wmv.so
```
The result was that mplayer was embedded but it didn't succeed to play the video (buffering doesn't start).
Later, I removed mplayer & mozilla plugin and installed vlc & its mozilla-plugin-vlc, linked the file /usr/lib/mozilla/plugins/libvlcplugin.so: the result was that now vlc was not even embedded in the browser!
Of course, in both cases about: plugins confirmed the codecs installed.

Any idea? Maybe I'm forced to install Firefox via apt-get in order to view this kind of videos? Or maybe I mistake the links? :confused:

HELP!
Thanks in advance,
piricoco

---

### Post by piricoco on 2008-09-01
any idea? ](*,)

---

