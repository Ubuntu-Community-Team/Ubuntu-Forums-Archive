---
title: "amarok error debug"
date: 2009-03-10
forum: Multimedia Software
---

### Post by Gosujii-sama on 2009-03-10
While firing amarok from terminal I noticed some error messages. Curious how to debug and fix the errors to eliminate them, and also I have another issue with sound in a way. While running sound via amarok I lose the ability to get sound from other things such as WarIII saying base sound services cant be started. The error from amarok terminal is:

```
construct@Diabolic-Construct:~$ amarok
Amarok: [Loader] Starting amarokapp..
Amarok: [Loader] Don't run gdb, valgrind, etc. against this binary! Use amarokapp.
DCOPClient::attachInternal. Attach failed Could not open network socket
kbuildsycoca running...
kdecore (KAction): WARNING: KAction::insertKAccel( kaccel = 0x813bda8 ): KAccel object already contains an action name "play_pause"
QLayout "unnamed" added to QVBox "unnamed", which already has a layout
kdecore (KAction): WARNING: KAction::insertKAccel( kaccel = 0x813bda8 ): KAccel object already contains an action name "play_pause"
QLayout: Adding KToolBar/mainToolBar (child of QVBox/unnamed) to layout for PlaylistWindow/PlaylistWindow
QObject::connect: Incompatible sender/receiver arguments
	StarManager::ratingsColorsChanged() --> ContextBrowser::ratingOrScoreOrLabelsChanged(const QString&)

```

How do you go about figuring out how to eliminate the errors so I can follow through a debug on other programs I may have issues with and what could possibly be wrong with amarok? I ask due to I wish to learn more about how linux works with programs and trying to further my knowledge of everything I can.

---

