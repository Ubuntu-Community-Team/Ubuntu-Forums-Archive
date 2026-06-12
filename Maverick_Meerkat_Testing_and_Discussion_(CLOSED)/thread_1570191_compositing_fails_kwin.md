---
title: "compositing fails kwin"
date: 2010-09-07
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by buzzmandt on 2010-09-07
can anyone make heads or tales of this?

```
buzzmandt@buzz-dev:~$ kwin --replace
kwin(1825) KWin::CompositingPrefs::detectDriverAndVersion: GL vendor is "Tungsten Graphics, Inc" 
kwin(1825) KWin::CompositingPrefs::detectDriverAndVersion: GL renderer is "Mesa DRI Mobile IntelÂ® GM45 Express Chipset GEM 20100328 2010Q1 " 
kwin(1825) KWin::CompositingPrefs::detectDriverAndVersion: GL version is "2.1 Mesa 7.8.2" 
kwin(1825) KWin::CompositingPrefs::detectDriverAndVersion: Detected driver "intel" , version "20100328" 
QInotifyFileSystemWatcherEngine::addPaths: inotify_add_watch failed: No such file or directory
QFileSystemWatcher: failed to add paths: /home/buzzmandt/.config/ibus/bus
Bus::open: Can not get ibus-daemon's address. 
IBusInputContext::createInputContext: no connection to ibus-daemon 
kwin(1825): OpenGL compositing self-check failed, disabling compositing. 

```

intel graphics daily build from 09-07-10. all updates applied. also added xorg-edgers ppa for spits and gigles but didn't help any.  

that was the error generated from a manual kwin --replace.  when system starts kwin effects wont enable.  i can then turn off effects and apply, then enable effects and apply and effects work like a charm.  I'm hoping this error message will assist someone in assisting me in the right direction.

---

### Post by Reiger on 2010-09-07
I think it is a known issue, upstream: [https://bugs.kde.org/show_bug.cgi?id=242413](https://bugs.kde.org/show_bug.cgi?id=242413) Perhaps you should update and check if the problem persists in 4.5.1 If it does you may want to point this out in the bug report...

---

