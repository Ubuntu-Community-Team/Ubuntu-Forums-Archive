---
title: "Youtube videos play, not BBC, in Firefox. Chrome OK."
date: 2011-03-06
forum: Multimedia Software
---

### Post by cocorocara on 2011-03-06
Ubuntu 10.10, 32 bit. Firefox 3.6.14

Why don't BBC videos play in Firefox if Youtube has no problem? Moreover videos play fine in Chrome.
Another strange thing: there seem to be two flashplugins in about:plugins

File:  libflashplayer.so
Version: Shockwave Flash 10.1 r102

File:  libflashplayer.so
Version: Shockwave Flash 10.2 r152

But there is only one flashplugin in the plugins directory: /usr/lib/firefox/plugins/flashplugin-alternative.so -> /etc/alternatives/firefox-flashplugin

$ update-alternatives --list firefox-flashplugin
/usr/lib/flashplugin-installer/libflashplayer.so

Any ideas?

---

