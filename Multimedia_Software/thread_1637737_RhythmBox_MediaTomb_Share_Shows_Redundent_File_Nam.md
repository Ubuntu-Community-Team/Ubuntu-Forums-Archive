---
title: "RhythmBox MediaTomb Share Shows Redundent File Names"
date: 2010-12-04
forum: Multimedia Software
---

### Post by Gotit on 2010-12-04
Hi,
I have set up a UPnP share with MediaTomb and when I go to that share in RhythmBox it displays the shared MP3's multiple times (see attached).  I seems to be displaying an MP3 once for each tag attribute (artist, album, title, genre, year...etc).

However in Totem Move Player is seems to display as expected (see attached). I am using the Coherence UPnP/DLNA plugin for both RhythmBox and Totem.

Does anyone know how to make a track display only 1 time (or in proper groupings like Totem) in RhythmBox?
Thanks.

---

### Post by Despot on 2011-01-15
This is an issue I've reported to Gnome's Bugzilla, and the MediaTomb forum. See

[http://sourceforge.net/projects/mediatomb/forums/forum/440751/topic/3801120](http://sourceforge.net/projects/mediatomb/forums/forum/440751/topic/3801120)
[https://bugzilla.gnome.org/show_bug.cgi?id=540200](https://bugzilla.gnome.org/show_bug.cgi?id=540200)

---

### Post by Despot on 2011-02-05
FWIW, if you share your media using a MediaServer that properly handles the refID attribute, the version of the Rhythmbox plugin that's in the Coherence SVN repository (see [urlhttp://coherence.beebits.net/wiki/RhythmBox#ManualInstallation[/url]) will properly filter out the duplicates.

This won't help you with current releases of MediaTomb, though, which don't properly handle the refID attribute.

---

