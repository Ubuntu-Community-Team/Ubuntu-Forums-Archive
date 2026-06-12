---
title: "Rhythmbox barely working any more"
date: 2012-10-17
forum: Multimedia Software
---

### Post by EmreJ on 2012-10-17
I don't know what happened (probably some component got upgraded) but rhythmbox is spewing all kinds of error messages:

[LIST]
[*]**Couldn't start playback: This appears to be a text file** when I try to play a radio station with pls.
[*][B]Required plugin could not be found

Python (v2.7) requires to install plugins to play media files of the following type: text/uri-list decoder[/B] when I try to play a radio station with m3u.
[*][B]Error in podcast

There was a problem adding this podcast: Unable to parse the feed contents[/B] when I try to update a podcast.
[*]**Unable to load feed. Check your network connection **when I try to add a new feed.
[/LIST]
I've already tried re-installing. I'm using version 2.98 on Ubuntu 12.04.

---

### Post by EmreJ on 2012-10-17
I solved the problem by refreshing the configuration files in **~/.local/share/rhythmbox**.

---

### Post by Theeboon on 2012-10-20
Rhythmbox 2.98 seems pretty buggy now. Whenever I have an audio CD in my drive, Rhythmbox crashes when detecting it (or trying to get the track titles of the CD).

Removing the .local rhythmbox dir didn´t help much.

---

### Post by dwpbike on 2013-01-07
i'm attempting 12.10 and looks like the world has changed:

dwp@diabolic:~$ locate Rhythmbox
/usr/lib/rhythmbox/plugins/random/Rhythmbox-Random-Album-Player.py
/usr/share/dbus-1/services/org.gnome.Rhythmbox3.service

can't play "radio" with rhythmbox, vlc, or totem with pls file or url.

---

