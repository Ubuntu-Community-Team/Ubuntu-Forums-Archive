---
title: "Media player"
date: 2011-08-11
forum: Multimedia Software
---

### Post by dV_gava on 2011-08-11
Hi guys,I'm new to this forum...
I'm searching for a media player that turns the pc off after the film finishes.
Does anyone have an idea?
Thanx
dV

---

### Post by CatKiller on 2011-08-11
Welcome to the forums.

Not that I know of, but it's not something I've especially looked for.

You could use something like ```
sudo shutdown -h +180
``` to get the computer to shut down in three hours, then start your film. You can also specify a time, if you prefer. You could probably put together a command-line instruction (or shell script, perhaps) that would start something like mplayer or vlc with the file you specified, then run the shutdown command when mplayer/vlc exits.

---

