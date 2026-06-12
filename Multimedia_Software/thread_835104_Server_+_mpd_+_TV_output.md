---
title: "Server + mpd + TV output"
date: 2008-06-20
forum: Multimedia Software
---

### Post by jonty-comp on 2008-06-20
I've recently had a go at setting up my own little home server, next to the TV, and this morning I set up mpd to play the music through the TV, being told what to do by a DaveMP web interface.  The problem is, to play the sound through the TV speakers the TV has to be on, even though there's no picture - a bit of a waste of power.
I was wondering if there was some way of setting up an X server so that the song information and / or a visualisation would display on the TV screen.  Luckily the TV has a VGA input so connecting it up isn't a problem.

There doesn't seem to be any programs designed for such a thing, so I'm a bit stuck. :(

Does anyone know of anything that might help?

---

### Post by funkydan2 on 2008-06-21
Could you just have one of the mpd gui's ([http://www.musicpd.org/clients.shtml](http://www.musicpd.org/clients.shtml)) running all the time?  Then when you turn on the TV you'll see what's playing and what's next on the playlist.

Just setup X + a simple window manager (like fluxbox) and set the mpd client to autostart.

---

### Post by jonty-comp on 2008-06-22
Unfortunately all the mpd GUIs I can find are ones that are geared towards keyboard/mice use, so they'd look a bit strange on a TV with neither.  I was thinking of finding some way of running one of the libvisual visualizers taking up the whole screen (probably at 480p resolution, this isn't a particularly new computer!) with one of the small clients placed in the corner or across the bottom showing the currently playing track.  Is it possible to dictate that a program should always open at certain x+y coordinates?  Without a window manager I wouldn't have thought it would remember them by itself.

---

