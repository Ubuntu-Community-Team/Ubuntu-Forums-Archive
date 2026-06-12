---
title: "Ubuntu 8.04 Esound..problems..gnome-settings-daemon"
date: 2010-03-08
forum: Multimedia Software
---

### Post by skyraven on 2010-03-08
Hello guys,


I have a curious setup and the problems are the same:)

I'm running on an Ubuntu 8.04 NxServer...and Nx only knows regarding multimedia to use it's own copy / emulation of esd, called NxESD.
It sets an env. variable $ESPEAKER and so far so good...
Now comes the problem.
I've uninstalled pulseaudio and installed the gstreamer-esd plugin.
If I allow everything as is => I get no sound (not even in audacious let's say with ESD output plugin defined).
If I enable from gstreamer-properties the Sounds -> Enable Software Mixing..then I get full sound in all applications...but..upon entering the Ubuntu Env everything is very slow and I'm faced with a message regarding "gnome-settings-daemon has failed to start...".

I've read a lot about this message, everything is ok in my /etc/hosts file..
All is related to the Enable Software Mixing tab.
Unfortunately if I disable it, then not even the apps that have a separate ESD plugin no longer work.

Can you lend me a hand ?
I'm all left out of ideas.

---

