---
title: "Dcop communication error - Amarok"
date: 2007-06-13
forum: Multimedia &amp; Video
---

### Post by dingledongle on 2007-06-13
Amarok giving noobs a hard time.

Clicking on Amarok gives me......

"DCOP communication error (amarok)
There was an error setting up inter-process communcations for KDE. The message returned by the system was: could not open network socket. Please check that the "dcopserver" program is running" 

Anyway i read somewhere to run it from the comand line, which i duly did - and it gave me
---------------------------------------------------------------------------------------------------
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
Amarok: [Loader] Starting amarokapp..
Amarok: [Loader] Don't run gdb, valgrind, etc. against this binary! Use amarokapp.
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
DCOPClient::attachInternal. Attach failed Could not open network socket
DCOPClient::attachInternal. Attach failed Could not open network socket
WARNING: DCOP communication problem!
kdeinit: Communication error with launcher. Exiting!
DCOPClient::attachInternal. Attach failed Could not open network socket
Amarok: [Loader] Amarok is taking a long time to load! Perhaps something has gone wrong?
DCOPClient::attachInternal. Attach failed Could not open network socket
DCOPClient::attachInternal. Attach failed Could not open network socket
I couldn't enable notifications at the dcopserver!
DCOPRef::send(): no DCOP client or client not attached error
kdecore (KWin): WARNING: Loading of kdetrayproxy failed.
kdecore (KAction): WARNING: KAction::insertKAccel( kaccel = 0x8157498 ): KAccel object already contains an action name "play_pause"
QLayout "unnamed" added to QVBox "unnamed", which already has a layout
kdecore (KAction): WARNING: KAction::insertKAccel( kaccel = 0x8157498 ): KAccel object already contains an action name "play_pause"
QLayout: Adding KToolBar/mainToolBar (child of QVBox/unnamed) to layout for PlaylistWindow/PlaylistWindow
QImage::smoothScale: Image is a null image
QImage::smoothScale: Image is a null image
QImage::smoothScale: Image is a null image

When amarok does start it does so with 2  Amarok tabs running. 1 is just a grey screen, and the other appears to work properly but havent tested it properly yet.

---

### Post by Lanky Juggler on 2007-06-16
i ocassionally get a similar, but not entirely the same, error.  I usually don't have a problem with it (for me i just close it all and try opening amarok again) but in your output it recomends that you try running amarokapp instead of amarok in your command line.  GIve it a shot and see if it works.

---

### Post by deathspell on 2007-07-06
Hello,

What is the command to start the dcop without having to start amarok? Is there also a command to stop dcop?

---

### Post by utsuprainfra on 2008-06-05
dcopserver should start your server or give you errors

man dcopserver

also dcopserver_shutdown


i had to install kubuntu_desktop, and all of its recommended / required packages, because i didn't like that amarok was giving me dcopserver errors.  one oddity was that because i did so via sudo, I ended up with a root:root ~/.ICEauthority with 600 permissions that I had to change to be owned by my personal user:group.

---

