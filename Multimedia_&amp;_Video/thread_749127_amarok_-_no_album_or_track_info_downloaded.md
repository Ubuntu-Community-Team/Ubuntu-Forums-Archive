---
title: "amarok - no album or track info downloaded"
date: 2008-04-08
forum: Multimedia &amp; Video
---

### Post by peterkeyani on 2008-04-08
hi

amarock downloaded and installed and works fine but does not download info about the cd 

any ideas?

thanks

pete

gutsy 7.10 amd64

---

### Post by aeiah on 2008-04-08
judging from a quick google it can be a firewall issue, or an issue with amarok ignoring gnome network settings if you're using a proxy or something, because amarok is used to using kde.

do you get any errors when you launch amarok from the terminal and try to do this?

---

### Post by peterkeyani on 2008-04-08
> **aeiah said:**
> judging from a quick google it can be a firewall issue, or an issue with amarok ignoring gnome network settings if you're using a proxy or something, because amarok is used to using kde.

do you get any errors when you launch amarok from the terminal and try to do this?

Hi, I havent installed a firewall or use a proxy - im a new ubuntu user!

how do i launch it from the terminal and do the other thing you suggested?

thanks
peter

---

### Post by peterkeyani on 2008-04-08
> **peterkeyani said:**
> Hi, I havent installed a firewall or use a proxy - im a new ubuntu user!

how do i launch it from the terminal and do the other thing you suggested?

thanks
peter

PS soundjuicer - defult - displays all the album info as soon as the cd is inserted:confused:

---

### Post by aeiah on 2008-04-08
open up a terminal (accessories > terminal) and type 'amarok'. this will launch amarok. do what you want to do in amarok, and if there are any errors, it should tell you in the terminal window as you do it.

---

### Post by peterkeyani on 2008-04-08
> **aeiah said:**
> open up a terminal (accessories > terminal) and type 'amarok'. this will launch amarok. do what you want to do in amarok, and if there are any errors, it should tell you in the terminal window as you do it.

thanks, i got this:

Amarok: [Loader] Starting amarokapp..
Amarok: [Loader] Don't run gdb, valgrind, etc. against this binary! Use amarokapp.
QSettings::sync: filename is null/empty
QSettings::sync: filename is null/empty
kbuildsycoca running...
DCOP Cleaning up dead connections.
QSettings::sync: filename is null/empty
kdecore (KAction): WARNING: KAction::insertKAccel( kaccel = 0x707590 ): KAccel object already contains an action name "play_pause"
QLayout "unnamed" added to QVBox "unnamed", which already has a layout
kdecore (KAction): WARNING: KAction::insertKAccel( kaccel = 0x707590 ): KAccel object already contains an action name "play_pause"
QLayout: Adding KToolBar/mainToolBar (child of QVBox/unnamed) to layout for PlaylistWindow/PlaylistWindow
QObject::connect: Incompatible sender/receiver arguments
        StarManager::ratingsColorsChanged() --> ContextBrowser::ratingOrScoreOrLabelsChanged(const QString&)
QSettings::sync: filename is null/empty
QSettings::sync: filename is null/empty
QSettings::sync: filename is null/empty
QSettings::sync: filename is null/empty
QPainter::begin: Cannot paint null pixmap

---

### Post by peterkeyani on 2008-04-08
> **aeiah said:**
> open up a terminal (accessories > terminal) and type 'amarok'. this will launch amarok. do what you want to do in amarok, and if there are any errors, it should tell you in the terminal window as you do it.

When I put a CD in the tray and select "Play Audio CD", amarok tries to to get the info but fails and the CD doesnt play either. No errors in terminal.

---

