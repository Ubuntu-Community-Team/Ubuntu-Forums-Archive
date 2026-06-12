---
title: "TightVncserver Event on connection"
date: 2012-02-09
forum: Networking &amp; Wireless
---

### Post by ronaldprettyman on 2012-02-09
Trying to have vncserver trigger an event on connection, for instance a script to play a sound, i've read through documentation but not sure how to do this, if i can add a line to the vncviewer to execute a bit of code when it connects
just some background, i have 3 ubuntu machines headless connected to audio systems that are controlled from a thin client tablet and want them to perform an action on connection, the vncserver are persistant and started at boot so not a startup event but a connection event...idk is their even a file that is created on connection like in /proc, could use even just use a basic c program with inotify

---

