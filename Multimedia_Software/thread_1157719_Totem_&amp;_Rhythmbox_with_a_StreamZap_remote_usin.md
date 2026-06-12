---
title: "Totem &amp; Rhythmbox with a StreamZap remote using LIRC"
date: 2009-05-13
forum: Multimedia Software
---

### Post by njee on 2009-05-13
I had an extremely frustrating time getting this up and running. As far as I can tell Ubuntu doesn't provide configuration for its two default media programs under LIRC!

The steps I took to get the remote up and running were installing lirc in synaptic and selecting the streamzap remote when lirc was configured.

Download the following text file and save it as .lircrc in your home directory.

Make sure you have enabled the LIRC plugins for both rhythmbox and totem under the plugins menu for each program (you will probably have to restart the programs for the remote to work).

Hopefully that should be it. I've bound all the functions to sensible buttons on the streamzap remote.

Play/pause/stop
skip forwards and backwards
previous/next chapter (or file in playlist or music track)
volume up/down
mute
exit closes both programs

on totem, menu and directional buttons work as well as ok to select.
on rhythmbox the record button will enable/disable shuffling.

This really isn't a how to that I'm supporting or anything - I never really check the forums I just thought I would post this in case it was helpful to anyone else...

---

### Post by jpeddicord on 2009-05-13
Thanks for your tutorial submission; as you stated this is not really a howto but rather a custom config file that others might find useful. I've moved it to Multimedia & Video as it doesn't quite fit within the Tutorials & Tips criteria. Thanks! :)

---

