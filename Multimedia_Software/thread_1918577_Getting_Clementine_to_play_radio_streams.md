---
title: "Getting Clementine to play radio streams"
date: 2012-02-01
forum: Multimedia Software
---

### Post by geovino on 2012-02-01
Running Lubuntu 11.10 64bit 

Installed Clementine, but when selecting radio station, it says "Clementine Stopped" instead of playing the stream. 

What file is missing?
How to get Clementine to play music?

---

### Post by oldos2er on 2012-02-01
Moved to Multimedia & Video.

Do you have the proper codecs installed?

---

### Post by geovino on 2012-02-01
> **oldos2er said:**
> Moved to Multimedia & Video.

Do you have the proper codecs installed?

I installed ubuntu-restricted-extras

And the SomaFM pop-up player does play music. Youtube plays videos.

I think its something in Clementine. or a file that I didn't install yet.

I've installed Clementine on many distros and it's never done this before.

---

### Post by oldos2er on 2012-02-01
Hmm. Try running it in terminal, the output might show the problem.

---

### Post by geovino on 2012-02-01
> **oldos2er said:**
> Hmm. Try running it in terminal, the output might show the problem.

davek@davek-lub:~$ clementine
QGtkStyle was unable to detect the current GTK+ theme.
Couldn't load icon "clementine-panel" 
Couldn't load icon "clementine-panel-grey" 
virtual bool GnomeGlobalShortcutBackend::DoRegister() - starting 
virtual bool GnomeGlobalShortcutBackend::DoRegister() - gnome settings daemon not registered 
virtual bool QxtGlobalShortcutBackend::DoRegister() 
Couldn't load icon "find" 
QGtkStyle was unable to detect the current GTK+ theme.
^C
davek@davek-lub:~$

is this because I'm not running gnome? I have installed Clementine on Mint 11 LXDE and it worked fine.

---

