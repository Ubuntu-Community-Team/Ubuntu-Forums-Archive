---
title: "Linux media player Box"
date: 2009-03-19
forum: Multimedia Software
---

### Post by dkveera on 2009-03-19
Hi i am working on a way to convert my PC to a Media center box.
The idea is to modify linux / linux apps to autorum media (mostly JPG's or MPG's ) at fullscreen. The application would run from startup and would not require any tweaking to be done.
The media can be picked up from one the folders in the machine
Is there any way to do this in Ubuntu>?

---

### Post by roblubbers on 2009-03-19
look at XBMC, freevo, elize or even boxee i gues....

---

### Post by dkveera on 2009-03-19
I will try them. But is there anyway they would pick up files froma specific folder and start playing immediately after startup?

---

### Post by roblubbers on 2009-03-19
you could always make a script which starts on boot and then use mplayer to play the entire directory

---

### Post by lovinglinux on 2009-03-19
Try this script

```
#!/bin/bash

find **[COLOR="Red"]$HOME/Videos[/COLOR]** -type f \( -name "*.avi" -o -name "*.mp4" -o -name "*.wmv" -o -name "*.mkv" -o -name "*.mov" -o -name "*.flv" -o -name "*.mpeg" -o -name "*.mpg" -o -name "*.rm" -o -name "*.ram" -o -name "*.ogm" -o -name "*.ogv" -o -name "*.divx" \) | sort > [COLOR="Red"]**$HOME/Videos/**[/COLOR]playlist.pls

gnome-mplayer  [COLOR="Red"]**$HOME/Videos/**[/COLOR]playlist.pls
```

This method works with gnome-mplayer, but not with all players due to simple playlist format used.

Add the script path to the session to make it launch automatically on startup:

Applications >>> System >>> Preferences >>> Sessions

Make sure you setup gnome-mplayer to start at fullscreen. I'm not sure if you can do this in the player config, but you can use compiz "Window rules" plugin to achieve this.

Don't forget to take a look at my FoxMediaCenter extension (link in the signature).

---

