---
title: "Automatically mute Rhythmbox when you play a video in Firefox with paclientmonitor"
date: 2009-03-14
forum: Multimedia Software
---

### Post by spiregrain on 2009-03-14
Just a quick post to boost a new program called "paclientmonitor".

You can get it here: [https://sourceforge.net/projects/paclientmonitor/](https://sourceforge.net/projects/paclientmonitor/)

The README file offers this incantation for pausing and resuming Rhythmbox in response to YouTube videos etc being played in Firefox.  But the syntax looks flexible enough to tackle anything of the sort:
```

paclientmonitor -n 'ALSA plug-in [firefox]' \
                  -c 'rhythmbox-client --no-start --pause' \
                  -d 'rhythmbox-client --no-start --play'
```

---

### Post by dmizer on 2009-03-23
Courtesy bump.

---

### Post by zpotonaator on 2010-12-27
Good stuff


EDIT: "ALSA plug-in [npviewer.bin]" for firefox flashplugin

---

