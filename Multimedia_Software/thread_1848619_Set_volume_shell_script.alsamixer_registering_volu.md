---
title: "Set volume shell script./alsamixer registering volume % incorrectly."
date: 2011-09-22
forum: Multimedia Software
---

### Post by firefish5000 on 2011-09-22
I created a small shell script to unmute the speakers at login and set the volume to an audiable but not too loud of a volume. (I have audacious OR vlc playing music in the background) but I noticed a small problem, if I turn the volume all the way down and mute it afterwards, then run this script, it barly turns up the volume (its around 20-30%) 
but, when I run alsamixer in the terminal it tells me that all are set properly
(Master 80%, Headphone 100%(L&R), Speaker 100%(L&R))
on the other hand if I barily ajust the volume using my laptop volume keys or the gnome volume maneger thing then run the command again it will show the true volume (when i turned the volume up it gave me ~30%, 100%, 100%)

```

#!/bin/bash
# Unmutes Speakers and sets the volume
# Originally located in /usr/share/gdm/autostart
# moved to /usr/share/BCustom, with a launcher
# placed in /usr/share/gdm/autostart (thought it
# might be stuck wondering whether to run, display
# , run in terminal, irelevent since I was wrong.

# Note: if one of these are muted, none will play.
amixer set Master playback 80% unmute
amixer set Speaker playback 100% unmute
amixer set Headphone playback 100% unmute
exit

```
What am I doing wrong? should I use something else to ajust the volume?(the keyboard volume keys dont work until I login, I kind of like it this way though for if someone tries using my computer without my permission they will be severly startled. Not to mention the player cant be seen or closed)
by the way, you may copy this script to your desktop, mark it as an exicutable, and run it. there is absulutly no need to add it to the autostart, problem occurs for me any way it goes.

---

### Post by firefish5000 on 2011-09-24
someone told me to try putting the unmute before the volume % part, it didnt work. : P

---

