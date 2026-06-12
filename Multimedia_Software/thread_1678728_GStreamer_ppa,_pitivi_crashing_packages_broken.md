---
title: "GStreamer ppa, pitivi crashing packages broken"
date: 2011-01-30
forum: Multimedia Software
---

### Post by mpnordland on 2011-01-30
Ok, I know it sounds like a hopeless title, but you guys have helped me out before! My tale of woe starts with this video project that I have to get done, and so I check out all the options, and end up with pitivi working the best for me. Enter problem no. 1: Pitivi crashes every time I try to add a clip. The net result is frustration and no work getting done. So, I say to myself, I'll add that gstreamer ppa that I read about on pitivi's website, and see if that helps. well, I add it, I start updating packages, the thing fails, and I am left with pitivi not opening, and when I want to do something with installing, uninstalling any software, it wants to remove a good part of my lovely gnome desktop and install KDE stuff!!! I don't want that, so I have come to the Ubuntu wizards for help. I do need to get this done by Friday February 4 2011, so if you could be speedy, I would appreciate it.

---

### Post by mpnordland on 2011-01-31
bump

---

### Post by mpnordland on 2011-01-31
I'm going to keep bumping this till I get an answer

---

### Post by mpnordland on 2011-01-31
Alright, I made an answer: Just do
```
sudo apt-get install -f
```
let it do it's thing, and then type:
```
sudo apt-get install ubuntu-desktop
```
then install any other programs you had installed that got removed.

---

