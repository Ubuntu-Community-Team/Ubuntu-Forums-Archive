---
title: "Shutting down sound driver"
date: 2007-04-17
forum: Multimedia &amp; Video
---

### Post by atomicgecko on 2007-04-17
I've gotten ubuntu installed using the alt version, but i'm still running into this nagging problem. When i try to log in, ubuntu is playing a sound loop over and over, and it does not log in. I'm thinking maybe disable the sound driver/device to shut it up, but I'm a noob. anybody got any good terminal commands besides killing gdm, and restarting it (that hasn't worked)?

---

### Post by sujith_m82 on 2007-04-18
Press ALT-CTRL-F1 to get into a terminal and execute "sudo killall -9 esd".
After that you can login.
I think that the login tune would again go into a spin - just kill esd again and you'll land on the desktop.

HTH,
Sujith.

---

