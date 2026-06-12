---
title: "Jack: hw:0 already in use"
date: 2007-11-22
forum: Multimedia &amp; Video
---

### Post by rishabh on 2007-11-22
When I try and start Jack Control, I get the following errors:
```
loading driver ..
apparent rate = 44100
creating alsa driver ... hw:0|hw:0|1024|2|44100|0|0|nomon|swmeter|-|32bit
control device hw:0
the playback device "hw:0" is already in use. Please stop the application using it and run JACK again
cannot load driver module alsa
```

Does this mean some other program is using my card? 
In System->Preferences->Sound -> Sound Playback only ESD works properly. 
When I test with ALSA, it says: 
```
audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Resource busy or not available.
```

All this happened only after I installed the "ubuntustudio-audio" package ([https://wiki.ubuntu.com/UbuntuStudio/PackageList](https://wiki.ubuntu.com/UbuntuStudio/PackageList)).

Help!

---

### Post by nutter78 on 2007-11-23
try to install qjackctl and set your prefs to something like hw:1 or hw:2

---

