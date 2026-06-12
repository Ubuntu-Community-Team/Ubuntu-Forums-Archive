---
title: "Amarok taking 30 seconds to load. As in 3 times 10."
date: 2008-06-22
forum: Multimedia Software
---

### Post by Bastaard on 2008-06-22
I love Amarok (use it on Gnome), it's really my favourite of all media players I've used on any OS. Having installed MySQL makes it pretty fast too. The only real problem is the startup time: it takes 30 seconds! Rhythmbox takes 4 seconds. Any ideas what I can do about this?

top outpute (not really relevant but whatver):

```
  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 6204 joris     20   0  134m  41m  26m S  9.3  4.1   4:55.77 amarokapp          

```

edit: running a terminal and typing amarok does nothing for the first 15 seconds, then it shows the splash and starts the actualy start-up progress, giving the following output:

```
Amarok: [Loader] Starting amarokapp..
Amarok: [Loader] Don't run gdb, valgrind, etc. against this binary! Use amarokapp.
DCOPClient::attachInternal. Attach failed Could not open network socket
kbuildsycoca running...
kdecore (KAction): WARNING: KAction::insertKAccel( kaccel = 0x809ca18 ): KAccel object already contains an action name "play_pause"
QLayout "unnamed" added to QVBox "unnamed", which already has a layout
kdecore (KAction): WARNING: KAction::insertKAccel( kaccel = 0x809ca18 ): KAccel object already contains an action name "play_pause"
QLayout: Adding KToolBar/mainToolBar (child of QVBox/unnamed) to layout for PlaylistWindow/PlaylistWindow
QObject::connect: Incompatible sender/receiver arguments
	StarManager::ratingsColorsChanged() --> ContextBrowser::ratingOrScoreOrLabelsChanged(const QString&)

```

---

### Post by mc4man on 2008-06-22
I've noticed the same thing though here at least it's only the first time per session, after that if I was to quit amarok it'll load in a sec or 2 at most from then on out. It may be due the nature of amarok loading the first time in gnome environment. 
Because I know I'll be using amarok at some point I added it to the startup programs to get the initial load up out of the way, it only seems to take 10 secs that way.
Maybe my times are slightly faster than yours due to that I don't use or have playlists, collections ect. I run and control amarok minimized from 3 right click actions.
That's why i like amarok, it's flexibility and some truly useful parameters

---

