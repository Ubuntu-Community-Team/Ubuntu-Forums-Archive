---
title: "Amarok won't start"
date: 2007-03-26
forum: Multimedia &amp; Video
---

### Post by Karl S. on 2007-03-26
Here's the error message:

> karl@karl-laptop:~$ amarok
Amarok: [Loader] Starting amarokapp..
Amarok: [Loader] Don't run gdb, valgrind, etc. against this binary! Use amarokapp.
kbuildsycoca running...
Reusing existing ksycoca
kio (KService*): WARNING: Invalid Service : basket_config_features.desktop
kio (KService*): WARNING: Invalid Service : basket_config_notes.desktop
kio (KSycoca): ERROR: No database available!
QLayout "unnamed" added to QVBox "unnamed", which already has a layout
QLayout: Adding KToolBar/mainToolBar (child of QVBox/unnamed) to layout for PlaylistWindow/PlaylistWindow
QPainter::begin: Cannot paint null pixmap
Amarok: [Loader] Amarok is taking a long time to load! Perhaps something has gone wrong?

I get the same message if I start amarok %U.

It's version 1.4.4

If I start it from the application menu, it shows up, with amarokapp, on the system monitor, but that's it: I don't actually see the program running.

Any ideas? I tried moving .kde and .xine directories to the trash. It allowed me to open Amarok, but then it froze. Here's the message:

> Amarok: [Loader] Starting amarokapp..
Amarok: [Loader] Don't run gdb, valgrind, etc. against this binary! Use amarokapp.
QLayout "unnamed" added to QVBox "unnamed", which already has a layout
QLayout: Adding KToolBar/mainToolBar (child of QVBox/unnamed) to layout for PlaylistWindow/PlaylistWindow


Incidentally--and this probably isn't related--I can't play any mp3 files anymore. I had no problem with it until yesterday, but opening an mp3 in VLC Media Player, Rhythmbox, or Songbird freezes the music application. I've tried playing files from my mounted drive and from my Desktop. No difference. I did just remove Xubuntu from my system. I doubt that's responsible--I'm not a computer person, so I don't know--but perhaps it is.


**UPDATED** Okay. It's working now. Why? I don't know. Here's some output:
> karl@karl-laptop:~$ amarok %U
Amarok: [Loader] Starting amarokapp..
Amarok: [Loader] Don't run gdb, valgrind, etc. against this binary! Use amarokapp.
QLayout "unnamed" added to QVBox "unnamed", which already has a layout
QLayout: Adding KToolBar/mainToolBar (child of QVBox/unnamed) to layout for PlaylistWindow/PlaylistWindow
QPainter::begin: Cannot paint null pixmap
karl@karl-laptop:~$ 

And playing mp3s works too. And I didn't lose my data on playcounts &c. I just copied the .kde and .xine folders back to where they were originally.

---

