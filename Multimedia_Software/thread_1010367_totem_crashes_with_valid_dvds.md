---
title: "totem crashes with valid dvds"
date: 2008-12-13
forum: Multimedia Software
---

### Post by Richard-g8jvm on 2008-12-13
Hi

Something strange
A complete fresh install of Ibex 8.10 64bit amd

Totem installed plus the bit from medibuntu
If I try to play a commercial DVD totem just shuts down.
If I put in a ripped DVD it plays it.
the ripped DVD doesn't have the menus, on this machine it plays both, 
both machines nearly identical , apart from this having two processors.

Kaffeine wont play either,

any ideas what I missed


TIA

Richard

---

### Post by mc4man on 2008-12-13
The latest totem can have problems with dvds with menus, try totem-xine if you wish a totem player.

For kaffeine (and totem-xine) make sure you have libxine1-ffmpeg installed.

Also kaffeine may need you to adjust the dvd device in it's setting from the default of /dev/dvd to /dev/scd[COLOR="Red"]0[/COLOR]( it did in 8.04, 8.10?

(adjust red to match your drive, sudo lshw -C disk will tell you

---

### Post by Richard-g8jvm on 2008-12-14
thanks
using Totem-xine gets over the problem of menus on this machine


Richard

---

