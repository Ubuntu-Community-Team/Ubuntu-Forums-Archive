---
title: "Flash audio does not work in Firefox only..."
date: 2009-05-10
forum: Multimedia Software
---

### Post by kulturloseramerikaner on 2009-05-10
The system I'm working on is a fresh install of Kubuntu Jaunty.  It's having the same flash audio issue where sound does not work as many others are, but this is happening only in Firefox.  If I go to Youtube, let's say, from Konqueror, it plays audio perfectly, but on Firefox it might as well be muted.  Amarok, Kaffeine, other apps plays audio just fine.
I tried running through some of the guides for getting this working, but they are all Ubuntu specific and I borked an install trying to install pulse to take care of this, which KDE didn't like.
Where would I start on this one?
Thanks in advance.

---

### Post by mirons on 2009-05-10
Have the same problem, but in all applications which embed Flash... ...solved for earlier installation from systemsettings, but I cannot find the same option this time (the fix was set ALSA as audio output)

---

### Post by ille on 2009-05-10
I solved my audio problem with flash yesterday by upgrading flash from version 9 to 10.

```

sudo apt-get install adobe-flashplugin

```

---

