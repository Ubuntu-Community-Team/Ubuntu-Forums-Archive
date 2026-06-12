---
title: "No video at all (after a wrong manipulation)"
date: 2008-04-16
forum: Multimedia &amp; Video
---

### Post by roy.nico on 2008-04-16
Hello !

I probably did something wrong (like uninstalling a package), but i don't know what. Now, i can't play any video file. Either with VLC or with Gnome Video Player.

my config : 
Ubuntu 7.10, gnome 

Symptom: 

if i start VLC, and open a video file, i have in the console :
 
VLC media player 0.8.6c Janus
X Error of failed request:  BadAlloc (insufficient resources for operation)
  Major opcode of failed request:  140 (XVideo)
  Minor opcode of failed request:  19 ()
  Serial number of failed request:  82
  Current serial number in output stream:  83
pure virtual method called
terminate called without an active exception
Abandon (core dumped)


 
any help would be helpful ...

---

### Post by roy.nico on 2008-04-20
Hej, 

I realised that the resolution of my screen was 1280x1024, which is in principle supported by the screen, but officially not by the graphic card. Strange enough, it worked ... for a while. I switched now to 1024x768, and every thing is ok. All video players work now.

Nicolas

---

