---
title: "No sound in games, but sound in other things"
date: 2008-11-29
forum: Multimedia Software
---

### Post by ZonedOut on 2008-11-29
I've just recently run into a problem with sound. I've been using Ubuntu for years and haven't had anything quite like this.  I'm currently using Intrepid Ibex.  Within the past week, I've lost sound in all my games (UT2004, Savage 2, Enemy Territory, and CS Source in WINE) but still have sound perfectly fine when playing movies in Totem, music in Rythmbox, and any sound from Flash video in Firefox.  Sound had been working in all of those games previously.

Does anyone know the difference between what the games are trying to use and what the other things are using?  Were there any recent updates for Intrepid that might cause something like this?  Thanks for any help.

---

### Post by ZonedOut on 2008-12-01
I found that UT2004 uses OpenAL for sound.  Is there a way to test whether OpenAL is working correctly with PulseAudio?

---

### Post by acreda on 2009-04-23
Same here, im sure its the change palseaudio sound system, more like a game is getting old maybe it does need some emulation work so the older games work

---

### Post by markbuntu on 2009-04-23
You are probably missing these plugins. A lot of games use sdl also.

libao-pulse (libao plugin)
libsdl1.2debian-pulseaudio (plugin for sdl apps)

---

