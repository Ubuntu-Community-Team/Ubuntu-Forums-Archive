---
title: "control video player remotely?"
date: 2008-05-14
forum: Multimedia Software
---

### Post by supersonicdarky on 2008-05-14
is it possible to control totem/(gnome-)mplayer/vlc remotely? What I would like to do it sit back on my couch to watch something on the 22" desktop monitor, but control playback on with my laptop which is beside me. Would this be done over ssh or some other way?

---

### Post by Stochastic on 2008-05-14
first, I think you'll get a more accurate and knowledgeable response if you posted this in the Multimedia & Video section of the forums.  This is more for producing multimedia.

SSH is probably not the way to go as it creates a new login to the system.  The only way I could see this possibly working would be if the computer didn't initialize X on boot, and permissions were granted for remote users to use X - don't ask me how.

A better solution would be to look into VLC, as I'm fairly certain its main strength is in Networked Video.

---

### Post by bapoumba on 2008-05-15
Moved to Multimedia & Video.

---

