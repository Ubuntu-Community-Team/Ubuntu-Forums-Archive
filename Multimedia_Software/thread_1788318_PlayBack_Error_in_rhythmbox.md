---
title: "PlayBack Error in rhythmbox"
date: 2011-06-22
forum: Multimedia Software
---

### Post by wethegreenpeople on 2011-06-22
When  I try to play a song using rhythmbox I get this error: "Configured audiosink bin1 is not working"

Any fixes? I'm using ubuntu 10.10

---

### Post by Yellow Pasque on 2011-06-22
Assuming you're using pulseaudio:
```
gconftool-2 --type string --set /system/gstreamer/0.10/default/audiosink pulsesink
gconftool-2 --type string --set /system/gstreamer/0.10/default/chataudiosink pulsesink
gconftool-2 --type string --set /system/gstreamer/0.10/default/musicaudiosink pulsesink
```
Note that Rbox uses musicaudiosink and it is not configurable from gnome-media-properties or Rbox itself. :( Bad design IMHO, but that's the way GNOME likes to roll.

---

### Post by wethegreenpeople on 2011-06-22
Fixed! Thanks :D

---

