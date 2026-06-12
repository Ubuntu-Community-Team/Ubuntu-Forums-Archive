---
title: "Sound just completely died"
date: 2008-04-22
forum: Multimedia Software
---

### Post by HyperHacker on 2008-04-22
I had sound working (worked right out of the box), until I went to the Login Window settings and tried to assign some sounds to the events. Nothing would happen when I hit Play. Since then any program that tries to use sound (Amarok, Movie Player) will freeze immediately upon opening. The interface appears but is completely unresponsive, with the "busy" cursor. The windows can be moved and activated but the program does nothing and has to be terminated.
The only exception is MPlayer which will play a sound once, but if I stop the sound and play it again or it finishes, it then freezes like the others. Rebooting and reinstalling Amarok hasn't solved the problem, and the login screen is still working fine but the selected sounds don't play.

---

### Post by HyperHacker on 2008-04-23
Anyone? Is there some sort of diagnostic or highly verbose player I can run or something to see what's up? I've tried some more programs and found:
-Writing stuff to /dev/audio works (and is fun :p).
-Pidgin also can't play sounds (using either ESD or ALSA), but doesn't freeze.
-Leaving Amarok open for several minutes doesn't help.

I'm not sure what MPlayer and /dev/audio are doing different but it's as if programs are trying to write to some audio device and waiting forever for a reply, while others (such as Pidgin) don't bother to wait for a reply. But I'm just guessing here.

[edit] Firefox also plays sound just fine in Youtube videos.

---

### Post by HyperHacker on 2008-04-24
Well, I started Amarok from the terminal to see what was up, and it worked fine, and continued to work after a couple reboots. Then it stopped working again. The output is a bit suspicious:

> hyperhacker@Mercury:~$ amarok
Amarok: [Loader] Starting amarokapp..
Amarok: [Loader] Don't run gdb, valgrind, etc. against this binary! Use amarokapp.
kdecore (KAction): WARNING: KAction::insertKAccel( kaccel = 0x8097858 ): KAccel object already contains an action name "play_pause"
QLayout "unnamed" added to QVBox "unnamed", which already has a layout
kdecore (KAction): WARNING: KAction::insertKAccel( kaccel = 0x8097858 ): KAccel object already contains an action name "play_pause"
QLayout: Adding KToolBar/mainToolBar (child of QVBox/unnamed) to layout for PlaylistWindow/PlaylistWindow
QObject::connect: Incompatible sender/receiver arguments
        StarManager::ratingsColorsChanged() --> ContextBrowser::ratingOrScoreOrLabelsChanged(const QString&)
QInputContext: no input method context available
QInputContext: no input method context available
Terminated

hyperhacker@Mercury:~$ amarokapp
kbuildsycoca running...
kdecore (KAction): WARNING: KAction::insertKAccel( kaccel = 0x81b2cc0 ): KAccel object already contains an action name "play_pause"
QLayout "unnamed" added to QVBox "unnamed", which already has a layout
kdecore (KAction): WARNING: KAction::insertKAccel( kaccel = 0x81b2cc0 ): KAccel object already contains an action name "play_pause"
QLayout: Adding KToolBar/mainToolBar (child of QVBox/unnamed) to layout for PlaylistWindow/PlaylistWindow
QObject::connect: Incompatible sender/receiver arguments
        StarManager::ratingsColorsChanged() --> ContextBrowser::ratingOrScoreOrLabelsChanged(const QString&)
QInputContext: no input method context available
QInputContext: no input method context available
X Error: BadWindow (invalid Window parameter) 3
  Major opcode:  7
  Minor opcode:  0
  Resource id:  0x260009a
kio (KIOConnection): ERROR: Header read failed, errno=104
kio (KIOConnection): ERROR: Header has invalid size (-1)
Terminated
hyperhacker@Mercury:~$ kio (KIOConnection): ERROR: Header read failed, errno=104
kio (KIOConnection): ERROR: Header has invalid size (-1)


Totem didn't produce any output at all. I wonder if it's just Amarok and Totem having this problem? Although things like the login screen settings and Pidgin don't play sound either, but they don't freeze.

Interesting, MPlayer also freezes if Amarok is running in the background...

---

### Post by HyperHacker on 2008-04-25
(Anyone...?)

This seems to be an xine-related problem, or so I'm guessing as Amarok and Totem both use it. However completely removing and reinstalling libxine, Amarok and Totem hasn't helped, nor has just removing libxine-ffmpeg.

[edit] It's working again since upgrading to Hardy.

---

