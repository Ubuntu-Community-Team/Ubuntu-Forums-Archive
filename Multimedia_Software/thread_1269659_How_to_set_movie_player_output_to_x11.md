---
title: "How to set movie player output to x11 ?"
date: 2009-09-18
forum: Multimedia Software
---

### Post by ubfu on 2009-09-18
As title is there a way for movie player to output video using x11 code ?

---

### Post by ajgreeny on 2009-09-18
Using totem-xine instead of gstreamer there is a **xine-config** file where this looks as if it can be changed in **~/.config/totem**.  Maybe it's the same for the gstreamer version.

---

### Post by mc4man on 2009-09-18
for totem-gstreamer (overall not a very good dvd player) change with this

```
gstreamer-properties
```

Note that will bring up "Multimedia Systems Selector" which is one of several menu items hidden away in a default install

run this in a terminal to see what's available
```
alacatre
```

---

### Post by ubfu on 2009-09-21
> **ajgreeny said:**
> Using totem-xine instead of gstreamer there is a **xine-config** file where this looks as if it can be changed in **~/.config/totem**.  Maybe it's the same for the gstreamer version.
Nothing can be change .The config file is just state.ini.The folder is empty.


> **mc4man said:**
> for totem-gstreamer (overall not a very good dvd player) change with this

```
gstreamer-properties
```

Note that will bring up "Multimedia Systems Selector" which is one of several menu items hidden away in a default install

run this in a terminal to see what's available
```
alacatre
```

At "Multimedia Systems Selector" , I have nothing showing x11 .It's hidden but how to unhide it ?

---

