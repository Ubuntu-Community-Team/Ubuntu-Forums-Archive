---
title: "RAM files opening from Epihpany in Totem"
date: 2009-01-05
forum: Multimedia Software
---

### Post by mikeym on 2009-01-05
Hi this is actually a copy and paste of [another thread](http://ubuntuforums.org/showthread.php?t=611375) that for some reason I cant reply to, but I have exactly the same issue and it wasn't resolved on their post:


[QUOTE=mirwin77]Does anyone know how to associate .ram (real audio) files to open with RealPlayer when using the Epiphany web browser? Currently, when I click on a link to a .ram file the browser tries to open Totem which cannot play these audio files. I've tried changing the assiciation by saving a .ram file, righ-clicking to get to it's properties, and changing the "open with" program to RealPlayer. Unfortunately, this does not change the behavior when clicking on a .ram link in Epiphany. Any help with this is much appreciated. I wanna use Epiphany as my main browser![/QUOTE]

---

### Post by mikeym on 2009-01-06
Surely it can't be because RealPlayer is 32bit and my browsers are 64bit because it should just by opening them as a command? Firefox will open it externally by changing the open with command in firefox but I can't do the same in Epiphany. What I've done so far is:


I've tried saving the RAM file and opening it in nautilus and *Properties* and *open with* and setting realplayer: no luck still opens Totem but opens realplayer in nautilus

I've tried opening *gconf-editor* and setting */desktop/gnome/url-handlers/rtp & rtsp command* to *realplay "%s"*: no luck still opens Totem but breaks Firefox's embeded flash playback from the BBC. (doesn't break epiphany)

In Firefox I've tried selecting *open with* and coosing my install of realplayer: this works in Firefox but epiphany stall opens totem.

---

