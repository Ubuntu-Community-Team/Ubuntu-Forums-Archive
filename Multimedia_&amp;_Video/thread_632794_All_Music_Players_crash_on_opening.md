---
title: "All Music Players crash on opening"
date: 2007-12-05
forum: Multimedia &amp; Video
---

### Post by kat_olliver on 2007-12-05
When I click the icon or type the command, both xmms and amarok fail to start. The icon does the whole 'bling' thing to show it's been clicked, and in the taskbar it says a window is loading. However this window never shows on screen and eventually the window loading tag goes away, without anything starting.
Also I can't play sound on youtube or other similar players.

I am running Gusty, and it is possible that the music players stopped working around the same time as I upgraded (my dad did the upgrade). I use speakers that have their own soundcard as my computer also runs Vista, (no haters, please. I have reasons.) and windows refuses to  share soundcards.

Ta,
~Kat

---

### Post by BLTicklemonster on 2007-12-05
Um, you're not using DonMcLean for a login name are you?

Anyway, open a terminal, and type in amarok, and see what kind of stuff it says, then paste it in here, some wise sage will probly come along and know right off the top of their head what to do.

---

### Post by kat_olliver on 2007-12-05
...no, I'm not. Is someone else having this problem?

It's not exactly the most helpful of error messages. :D

kat:~$ amarok
Amarok: [Loader] Starting amarokapp..
Amarok: [Loader] Don't run gdb, valgrind, etc. against this binary! Use amarokapp.
Amarok: [Loader] amarokapp probably crashed!

---

### Post by BLTicklemonster on 2007-12-05
Don McLean did American Pie, wherein it was the day "the music died".

So ah... go to synaptic, and find amarok, and reinstall it, see if that helps?

---

### Post by kat_olliver on 2007-12-05
Ahha, so Google tells me.

Have install synaptic, and it died when I tried to re-install amarock. Will try again.

---

### Post by kat_olliver on 2007-12-05
Re-installed it  manually. 
I get a new error message! That's progress, right?

kat:~$ amarok
Amarok: [Loader] Starting amarokapp..
Amarok: [Loader] Don't run gdb, valgrind, etc. against this binary! Use amarokapp.
kdecore (KAction): WARNING: KAction::insertKAccel( kaccel = 0x809a090 ): KAccel object already contains an action name "play_pause"
QLayout "unnamed" added to QVBox "unnamed", which already has a layout
kdecore (KAction): WARNING: KAction::insertKAccel( kaccel = 0x809a090 ): KAccel object already contains an action name "play_pause"
QLayout: Adding KToolBar/mainToolBar (child of QVBox/unnamed) to layout for PlaylistWindow/PlaylistWindow
QObject::connect: Incompatible sender/receiver arguments
        StarManager::ratingsColorsChanged() --> ContextBrowser::ratingOrScoreOrLabelsChanged(const QString&)
\

---

### Post by kat_olliver on 2007-12-05
Amarok has now started, and will play files, but no sound comes out. Possibly it is trying to use the wrong speakers, how would I find out?

---

### Post by kat_olliver on 2007-12-06
All fixed now, got an expert in. 
Thanks for the help!

~Kat

---

