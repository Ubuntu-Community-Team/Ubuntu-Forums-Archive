---
title: "Problems with Amarok"
date: 2008-02-02
forum: Multimedia &amp; Video
---

### Post by qbox on 2008-02-02
So the problem is
When I start the f***ing amarok, my computer freaze automatically. HDD scaning something and I cant work nothing half an hour or more. What is f***ing wrong with f***ing Amarok? I turn off options to scan for new files. I cant open console.
:confused:'
Im pretty nervous now.

---

### Post by rainwalker on 2008-02-02
Please tone down your language, it won't fix anything.

How did you install Amarok? If you didn't use Synaptic, you should isntall it that way. If you did, try starting it from the terminal

---

### Post by qbox on 2008-02-02
Instaled sudo apt-get install amarok
in terminal started

qbox@qbox:~$ amarok
Amarok: [Loader] Starting amarokapp..
Amarok: [Loader] Don't run gdb, valgrind, etc. against this binary! Use amarokapp.
kdecore (KAction): WARNING: KAction::insertKAccel( kaccel = 0x76e4b0 ): KAccel object already contains an action name "play_pause"
QLayout "unnamed" added to QVBox "unnamed", which already has a layout
kdecore (KAction): WARNING: KAction::insertKAccel( kaccel = 0x76e4b0 ): KAccel object already contains an action name "play_pause"
QLayout: Adding KToolBar/mainToolBar (child of QVBox/unnamed) to layout for PlaylistWindow/PlaylistWindow
QObject::connect: Incompatible sender/receiver arguments
        StarManager::ratingsColorsChanged() --> ContextBrowser::ratingOrScoreOrLabelsChanged(const QString&)
qbox@qbox:~$ 

still freezing. something scanning in background. a cant work nothing.

---

### Post by rainwalker on 2008-02-02
Try using the "amarokapp" command instead of "amarok". I don't know why it's like that, because "amarok" wouold make more sense, but oh well.

---

