---
title: "having problems playing mediafiles"
date: 2009-06-03
forum: Multimedia Software
---

### Post by Heffa on 2009-06-03
I'm having a spot of difficulty playing my music. Tried both amarok and rhythmbox, neither works.

rhythmbox won't load the music, i have the library it just won't play. I am also not able to play internet radio.

tried amarok now and it simply died on me got the error message:

> Amarok: [Loader] Starting amarokapp..
Amarok: [Loader] Don't run gdb, valgrind, etc. against this binary! Use amarokapp.
kbuildsycoca running...
Reusing existing ksycoca
kdecore (KAction): WARNING: KAction::insertKAccel( kaccel = 0x82b8988 ): KAccel object already contains an action name "play_pause"
QLayout "unnamed" added to QVBox "unnamed", which already has a layout
kdecore (KAction): WARNING: KAction::insertKAccel( kaccel = 0x82b8988 ): KAccel object already contains an action name "play_pause"
QLayout: Adding KToolBar/mainToolBar (child of QVBox/unnamed) to layout for PlaylistWindow/PlaylistWindow
QObject::connect: Incompatible sender/receiver arguments
	StarManager::ratingsColorsChanged() --> ContextBrowser::ratingOrScoreOrLabelsChanged(const QString&)
kdecore (KAction): WARNING: KActionCollection::KActionCollection( QObject *parent, const char *name, KInstance *instance )
andreas@Ubbi:~$ 
andreas@Ubbi:~$ QImage::smoothScale: Image is a null image
QImage::smoothScale: Image is a null image
QImage::smoothScale: Image is a null image
QImage::smoothScale: Image is a null image
QImage::smoothScale: Image is a null image
QImage::smoothScale: Image is a null image
X Error: BadWindow (invalid Window parameter) 3
  Major opcode:  7
  Minor opcode:  0
  Resource id:  0x420009a


also i have w32codecs installed.

I am confused please help.

---

### Post by Heffa on 2009-06-12
no worries i fixed it, somehow, I really don't know what i did but now it works.

hmm.

---

