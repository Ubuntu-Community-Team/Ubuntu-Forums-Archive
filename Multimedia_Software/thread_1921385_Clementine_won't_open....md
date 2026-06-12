---
title: "Clementine won't open..."
date: 2012-02-06
forum: Multimedia Software
---

### Post by loganbell45 on 2012-02-06
I'm trying to find a player that I like enough to replace iTunes, and I like the look of clementine, however when I try and open it, it just disappears. The terminal has this to say:

~$ clementine
GLOG Unable to locate theme engine in module_path: "pixmap", 
GLOG Unable to locate theme engine in module_path: "pixmap", 
GLOG Unable to locate theme engine in module_path: "pixmap", 
GLOG Unable to locate theme engine in module_path: "pixmap", 
Connected to accessibility bus at:  "unix:abstract=/tmp/dbus-OzOqDHiHnR,guid=8bfb6f95e955c1a767a9c2b500000d91" 
Registered DEC:  true 
virtual bool GnomeGlobalShortcutBackend::DoRegister() - starting 
virtual bool GnomeGlobalShortcutBackend::DoRegister() - complete 
Couldn't load icon "find" 
Invalid parent:  0xb6c37838 QtSingleApplication(0xbf8b2ec0, name = "clementine") 
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

But I can't make much sense of this, I don't understand what it wants me to do :l haha, could anybody help?

---

### Post by wolfen69 on 2012-02-06
Try this:
```
sudo apt-get install gtk2-engines-pixbuf
```

---

