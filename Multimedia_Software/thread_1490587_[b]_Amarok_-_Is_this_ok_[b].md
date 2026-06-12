---
title: "[b] Amarok - Is this ok? [/b]"
date: 2010-05-22
forum: Multimedia Software
---

### Post by Guyik on 2010-05-22
Hi everyone,

I have been using **Amarok** - **1.4.9.1** (Using KDE 3.5.10), it says in *Help > About Amarok*, although I use **Gnome 2.22.3** -, and I have noticed some errors, like it sometimes does nothing when I click on play bottom (after having paused the song).
After this I usually have to reboot to get Amarok working again.

Today I have executed Amarok from the terminal, and look at this:

```
:~$ amarok
Amarok: [Loader] Starting amarokapp..
Amarok: [Loader] Don't run gdb, valgrind, etc. against this binary! Use amarokapp.
kbuildsycoca running...
Reusing existing ksycoca
kbuildsycoca: WARNING: Parse error in /home/cristian/.config/menus/applications-merged/xdg-desktop-menu-dummy.menu, line 1, col 1: unexpected end of file
kbuildsycoca: WARNING: Parse error in /home/cristian/.config/menus/applications-merged/xdg-desktop-menu-dummy.menu, line 1, col 1: unexpected end of file
DCOP Cleaning up dead connections.
kdecore (KAction): WARNING: KAction::insertKAccel( kaccel = 0x809be30 ): KAccel object already contains an action name "play_pause"
QLayout "unnamed" added to QVBox "unnamed", which already has a layout
kdecore (KAction): WARNING: KAction::insertKAccel( kaccel = 0x809be30 ): KAccel object already contains an action name "play_pause"
QLayout: Adding KToolBar/mainToolBar (child of QVBox/unnamed) to layout for PlaylistWindow/PlaylistWindow
QObject::connect: Incompatible sender/receiver arguments
    StarManager::ratingsColorsChanged() --> ContextBrowser::ratingOrScoreOrLabelsChanged(const QString&)

```And when I clicked on "Exit", it said:

```
p:~$ QObject::disconnect: Unexpected null parameter
QObject::connect: Cannot connect (null)::activePartChanged( KParts::Part * ) to KHTMLPart::slotActiveFrameChanged( KParts::Part * )
X Error: BadWindow (invalid Window parameter) 3
  Major opcode:  20
  Minor opcode:  0
  Resource id:  0x4200086
X Error: BadWindow (invalid Window parameter) 3
  Major opcode:  7
  Minor opcode:  0
  Resource id:  0x420009a


```And then I had to use Ctrl+C to close it completely.

*xdg-desktop-menu-dummy.menu* is empty. What is this file?

Can I do anything to solve the problems?
Thanks.

---

