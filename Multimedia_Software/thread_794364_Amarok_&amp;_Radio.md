---
title: "Amarok &amp; Radio"
date: 2008-05-14
forum: Multimedia Software
---

### Post by qweqwe on 2008-05-14
kUbuntu 8.04: Amarok stops radio playing after 2-3 minutes. Every time had to click 'stop' button and again 'play'

---

### Post by warbread on 2008-05-15
Are you using KDE 3 or 4?  

Try running amarokapp in the terminal and watch its output when it stops.  It may tell you there's an error.

---

### Post by qweqwe on 2008-05-15
KDE3, Amarok 1.4.9.1

Output:
kdecore (KAction): WARNING: KAction::insertKAccel( kaccel = 0x809e8a0 ): KAccel object already contains an action name "play_pause"
QLayout "unnamed" added to QVBox "unnamed", which already has a layout
kdecore (KAction): WARNING: KAction::insertKAccel( kaccel = 0x809e8a0 ): KAccel object already contains an action name "play_pause"
QLayout: Adding KToolBar/mainToolBar (child of QVBox/unnamed) to layout for PlaylistWindow/PlaylistWindow
QObject::connect: Incompatible sender/receiver arguments
        StarManager::ratingsColorsChanged() --> ContextBrowser::ratingOrScoreOrLabelsChanged(const QString&)
STARTUP
QWidget::setMinimumSize: The smallest allowed size is (0,0)
QComboBox::setCurrentItem: (speakerComboBox) Index 2 out of range
QComboBox::setCurrentItem: (speakerComboBox) Index 2 out of range

It seems to be related to the UI only, no hints about streaming problems.

---

### Post by dage on 2008-09-14
hello, I've the same prob here.
Can someone help us to fix it please

---

