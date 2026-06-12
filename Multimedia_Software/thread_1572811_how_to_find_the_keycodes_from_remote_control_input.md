---
title: "how to find the keycodes from remote control input."
date: 2010-09-11
forum: Multimedia Software
---

### Post by ost2life on 2010-09-11
Hi, I've got an Emprex 3009URF remote control which I'm using to run XBMC and whilst it works fine for the most part there are a couple of things that I can do with a keyboard/mouse that I'm unable to do with the remote, for instance "right clicking" with the mouse that brings up a context menu, that is totally inaccessible from the remote.

Some things I was able to fix by editing .xsessionrc as instructed by another post elsewhere on the tubes, in the format of:

xmodmap -display :0 -e “keycode 127 = space”

however I don't know how to find the keycode and I don't know how to map that to a right click event.

any help would be greatly appreciated.

---

### Post by ost2life on 2010-09-12
bump

---

### Post by geoff07 on 2010-10-03
to find the keycodes, run xev (in X11-utils) in a terminal. To map, well I'm looking for that answer too!

---

