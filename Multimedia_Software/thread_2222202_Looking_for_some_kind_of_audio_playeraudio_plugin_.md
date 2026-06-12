---
title: "Looking for some kind of audio player/audio plugin that gives reverb to my music"
date: 2014-05-05
forum: Multimedia Software
---

### Post by carlos47 on 2014-05-05
I remember I was able to play my music with EAX4 reverb sound effects such as "sound corrider", etc.

I was just wondering if there is something I could use for Ubuntu which could improve my sound life.

Perhaps a plugin, or some software that can turn reverb effects on.

---

### Post by ajgreeny on 2014-05-05
Audacious allow you to use ladspa audio plugins which can make quite a difference to the sound.

First install tap-plugins and/or swh-plugins, then open audacious and go to File->Preferences->Plugins->Effects tab.
You now have to add the pathway to the ladspa plugin modules which is /usr/lib/ladspa/, hit enter and the available plugins will all be detected and listed.
You can then search for the effects you might like such as reverb, echo etc etc and enable them.
From then you can then enable or disable them on the fly with the audacious Output ->Effects menu item.

---

