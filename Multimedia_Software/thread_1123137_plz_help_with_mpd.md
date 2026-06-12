---
title: "plz help with mpd"
date: 2009-04-11
forum: Multimedia Software
---

### Post by kratos_prakhar on 2009-04-11
i wanted to uninstall and reinstall mpd...

sudo rm /var/lib/dpkg/info/mpd.*
then

sudo apt-get autoremove --purge mpd

now when i run 

sudo apt-get install mpd

i get the following error: 
* Stopping Music Player Daemon mpd                                      [ OK ] 
 * Starting Music Player Daemon mpd                                             No protocol specified
E: client-conf-x11.c: XOpenDisplay() failed

any ideas?

---

