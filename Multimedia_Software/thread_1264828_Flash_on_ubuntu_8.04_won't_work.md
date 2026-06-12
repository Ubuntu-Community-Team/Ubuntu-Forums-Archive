---
title: "Flash on ubuntu 8.04 won't work"
date: 2009-09-12
forum: Multimedia Software
---

### Post by ravalox on 2009-09-12
I've tried copying the libflash.so file into the plugins directory as well as the non-free repository item.  I can't get flash working on my fresh installation of 64-bit 8.04.  What am I missing?

---

### Post by purgatori on 2009-09-12
In the url bar of Firefox (which I assume you're running), type about:plugins and check if you have an entry for shockwave flash. If you don't, then try the following steps:

```
sudo apt-get remove -y --purge flashplugin-nonfree gnash gnash-common mozilla-plugin-   gnash swfdec-mozilla libflashsupport nspluginwrapper
sudo rm -f /usr/lib/mozilla/plugins/*flash*
sudo rm -f ~/.mozilla/plugins/*flash*
sudo rm -f /usr/lib/firefox/plugins/*flash*
sudo rm -f /usr/lib/firefox-addons/plugins/*flash*
sudo rm -rfd /usr/lib/nspluginwrapper

```

```
wget http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.32.18.linux-x86_64.so.tar.gz
```

```
tar -xvf libflashplayer-10.0.32.18.linux-x86_64.so.tar.gz
```

Then copy the extracted libflashplayer.so to /usr/lib/mozilla/plugins.

---

