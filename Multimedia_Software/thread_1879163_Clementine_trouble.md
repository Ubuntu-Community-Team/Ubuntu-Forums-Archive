---
title: "Clementine trouble"
date: 2011-11-11
forum: Multimedia Software
---

### Post by jsfaulkner87 on 2011-11-11
Hey!  I've been having a problem with Clementine for a while now, for some reason it's just stopped opening.  I have Oneiric using gnome classic and I have tried uninstall/reinstall many times so I'm not sure what to do because I LOVE Clementine and for some reason no other media player quenches my thirst.  So what do you guys think?


Here is what I get when I run clementine in terminal.


```
GLOG Unable to locate theme engine in module_path: "pixmap", 
GLOG Unable to locate theme engine in module_path: "pixmap", 
GLOG Unable to locate theme engine in module_path: "pixmap", 
GLOG Unable to locate theme engine in module_path: "pixmap", 
Connected to accessibility bus at:  "unix:abstract=/tmp/dbus-tIUrtyZyGq,guid=54ce6be3022620d913e569dc00000029" 
Registered DEC:  true 
virtual bool GnomeGlobalShortcutBackend::DoRegister() - starting 
virtual bool GnomeGlobalShortcutBackend::DoRegister() - complete 
"sni-qt/10885" WARN  02:32:26.805 void StatusNotifierItemFactory::connectToSnw() Invalid interface to SNW_SERVICE 
Invalid parent:  0xaba1e00 QtSingleApplication(0xbffdb5a0, name = "clementine") 
Requesting child objects for an interface that is a virtual child itself. 
Requesting child objects for an interface that is a virtual child itself. 
Requesting child objects for an interface that is a virtual child itself. 
Requesting child objects for an interface that is a virtual child itself. 
Requesting child objects for an interface that is a virtual child itself. 
Requesting child objects for an interface that is a virtual child itself. 
Requesting child objects for an interface that is a virtual child itself. 
Requesting child objects for an interface that is a virtual child itself. 
Requesting child objects for an interface that is a virtual child itself. 
Requesting child objects for an interface that is a virtual child itself. 
Requesting child objects for an interface that is a virtual child itself. 
Requesting child objects for an interface that is a virtual child itself. 
Requesting child objects for an interface that is a virtual child itself. 
Creating accessible with different object than the original interface! 
Creating accessible with different object than the original interface! 
Creating accessible with different object than the original interface! 
Creating accessible with different object than the original interface! 
Creating accessible with different object than the original interface! 
Creating accessible with different object than the original interface! 
Creating accessible with different object than the original interface! 
Creating accessible with different object than the original interface! 
Creating accessible with different object than the original interface! 
Creating accessible with different object than the original interface! 
Creating accessible with different object than the original interface! 
Creating accessible with different object than the original interface! 
Creating accessible with different object than the original interface! 
Creating accessible with different object than the original interface! 
Creating accessible with different object than the original interface! 
Creating accessible with different object than the original interface! 
Creating accessible with different object than the original interface! 
Creating accessible with different object than the original interface! 
Creating accessible with different object than the original interface! 
ASSERT: "interface->valueInterface()" in file accessible.cpp, line 280
Aborted
```
Any ideas?

---

### Post by TREESofRIGHTEOUSNESS on 2011-11-11
well... that reply post is obviously spam....

I am not totally sure... but I think if you uninstall it, you need to purge the config files, also

sudo apt-get purge PROGRAM_NAME

---

### Post by coffeecat on 2011-11-11
> **TREESofRIGHTEOUSNESS said:**
> well... that reply post is obviously spam....

I've removed it. Just report spam with the [img]http://ubuntuforums.org/images/buttons/report.gif[/img] button and we'll take care of it. Thanks!

---

### Post by TREESofRIGHTEOUSNESS on 2011-11-11
ah thanks....  @coffeecat

---

### Post by Coert on 2011-11-28
Your problem seems to be with the QT package qt-at-spi . Try uninstalling that package:

sudo apt-get remove qt-at-spi

Details:
[http://code.google.com/p/clementine-player/issues/detail?id=2327](http://code.google.com/p/clementine-player/issues/detail?id=2327)

---

### Post by robmi on 2012-02-18
@Coert
Many thanks. That helped. Now also K9copy and Backlite work.

---

