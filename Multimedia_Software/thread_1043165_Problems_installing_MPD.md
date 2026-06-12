---
title: "Problems installing MPD"
date: 2009-01-18
forum: Multimedia Software
---

### Post by ruipalmeira on 2009-01-18
hey there... i've been having problems installing MPD in my ubuntu box, i know that mpd is on the repos, but i can't install it... i'm pasting the terminal output when trying to install mpd.

[Quote="gnome-terminal"]
rui@rui-desktop:~$ sudo apt-get install mpd mpc gmpc
A instalar mpd (0.13.2-2ubuntu1) ...
 * Starting Music Player Daemon mpd                                              * creating /var/lib/mpd/tag_cache... 
No protocol specified
E: client-conf-x11.c: XOpenDisplay() failed
No protocol specified
E: client-conf-x11.c: XOpenDisplay() failed
Segmentation fault
                                                                         [fail]
invoke-rc.d: initscript mpd, action "start" failed.
dpkg: error processing mpd (--configure):
 subprocess post-installation script retrieve status error 139
A processar 'triggers' para libc6 ...
there where errors when processing package : 
mpd
[/quote]

I'm using Ubuntu 8.10, with kernel linux 2.6.27-11-generic, with gnome 2.24.

Thanks in advance, 

ruipalmeira

---

