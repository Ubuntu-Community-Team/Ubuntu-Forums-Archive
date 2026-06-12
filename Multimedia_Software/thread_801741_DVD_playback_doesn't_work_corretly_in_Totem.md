---
title: "DVD playback doesn't work corretly in Totem"
date: 2008-05-20
forum: Multimedia Software
---

### Post by Aryding on 2008-05-20
So I'm using Mplayer (Totem) and when I put in a dvd there is no main menu, it just starts the film.  Some films are in different languages and some have the directors comments going.  When I manually go through the Video_TS file and find the main menu I can't click on anything.  My DVD's are fine, but what am I doing wrong, am I missing DVD codecs?

---

### Post by Yellow Pasque on 2008-05-20
mplayer doesn't do a good job with menus IMHO. Try VLC. Open Synaptic Package Manager and do a search for VLC. Be sure to get the sound plugins you need and libvlc0 if you plan on building media apps from source.

You can also try starting mplayer from the terminal and see if it complains about missing codecs if you still want to use it.

---

### Post by cor2y on 2008-05-21
Replace totem-gstreamer (gstreamer does not yet have dvd menu navigation) with totem-xine for dvd menu navigation
```
sudo apt-get remove totem-gstreamer;sudo apt-get install totem-xine
```You may need to install some extra xine plugins for other media playback if you are not automatically notified when you try to play a different file type.

---

