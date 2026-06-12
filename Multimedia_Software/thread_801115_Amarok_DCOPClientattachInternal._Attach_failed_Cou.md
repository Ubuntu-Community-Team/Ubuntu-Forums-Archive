---
title: "Amarok: DCOPClient::attachInternal. Attach failed Could not open network socket"
date: 2008-05-20
forum: Multimedia Software
---

### Post by themightymegatron on 2008-05-20
That's part of the message I get when I run Amarok in a terminal. I was going to set up MySQL but I don't want to do that until I can resolve this issue. This is the full output for when I run amarok in a terminal:

> 
primus@vectorsigma:~$ amarokapp
**DCOPClient::attachInternal. Attach failed Could not open network socket**
kbuildsycoca running...
Reusing existing ksycoca
kdecore (KAction): WARNING: KAction::insertKAccel( kaccel = 0x809cb50 ): KAccel object already contains an action name "play_pause"
QLayout "unnamed" added to QVBox "unnamed", which already has a layout
kdecore (KAction): WARNING: KAction::insertKAccel( kaccel = 0x809cb50 ): KAccel object already contains an action name "play_pause"
QLayout: Adding KToolBar/mainToolBar (child of QVBox/unnamed) to layout for PlaylistWindow/PlaylistWindow
QObject::connect: Incompatible sender/receiver arguments
	StarManager::ratingsColorsChanged() --> ContextBrowser::ratingOrScoreOrLabelsChanged(const QString&)
QColor::setRgb: RGB parameter(s) out of range
STARTUP


I'm not sure what to make of most if not all of that. I'm most concerned about getting the networking function up and running for MySQL, but if you could help me with the other errors that'd be awesome!

I have no idea what dcopclient is, but I tried to install it with apt-get and got nothing, and I can't figure out how to get it working :(

I appreciate any/all help! Thanks!

---

### Post by themightymegatron on 2008-05-20
*bump*

---

### Post by darkknight209 on 2008-06-26
old post, but heck i'll post what i did to get it going, i added kdeinit and dcopserver to my startup file, i use fluxbox :-p maybe we can figure this out together lol

---

### Post by Emily the strange on 2009-03-30
I have same or similar problem. I have ubuntu 8.10 and if I use terminal to open amarok it gives me this:

```
nika@Polux:~$ amarok
Amarok: [Loader] Starting amarokapp..
Amarok: [Loader] Don't run gdb, valgrind, etc. against this binary! Use amarokapp.
DCOPClient::attachInternal. Attach failed Could not open network socket
Could not open library dcopserver.la: libkdeinit_dcopserver.so: cannot open shared object file: No such file or directory
dcopserver: error while loading shared libraries: libkdeinit_dcopserver.so: cannot open shared object file: No such file or directory
kdeinit: DCOPServer could not be started, aborting.
DCOPClient::attachInternal. Attach failed Could not open network socket
DCOPClient::attachInternal. Attach failed Could not open network socket
Amarok: [Loader] Amarok is taking a long time to load! Perhaps something has gone wrong?
DCOPClient::attachInternal. Attach failed Could not open network socket
I couldn't enable notifications at the dcopserver!
DCOPRef::send(): no DCOP client or client not attached error
QLayout "unnamed" added to QVBox "unnamed", which already has a layout
QLayout: Adding KToolBar/mainToolBar (child of QVBox/unnamed) to layout for PlaylistWindow/PlaylistWindow
QObject::connect: Incompatible sender/receiver arguments
	StarManager::ratingsColorsChanged() --> ContextBrowser::ratingOrScoreOrLabelsChanged(const QString&)
QColor::setRgb: RGB parameter(s) out of range
DCOPClient::attachInternal. Attach failed Could not open network socket
DCOPClient::attachInternal. Attach failed Could not open network socket
DCOPClient::attachInternal. Attach failed Could not open network socket
DCOPClient::attachInternal. Attach failed Could not open network socket
amarokapp: Fatal IO error: client killed

```

any ideas? =|

I find something [http://ubuntuforums.org/showthread.php?t=107269&highlight=dcopserver]("http://ubuntuforums.org/showthread.php?t=107269&highlight=dcopserver") but when I type 

"sudo chown -R myusername:myusername /home/myusername/.*" (ok I was change all "myusername"s) it looks like this:


```
chown: cannot access `/home/nika/./.gvfs': Permission denied
chown: cannot access `/home/nika/.gvfs': Permission denied
``` (and I get the same msg even if I have root permissions)

---

### Post by JoshRobertson92 on 2009-05-15
I get this same problem when using conky
[B][I]'DCOPClient::attachInternal. Attach failed Could not open network socket'
'Failed to attach to DCOPClient.[/I][/B]

From another thread I got the idea that other people were having the same problem and that the solution was to type in the terminal
'joshua@Joshua-desktop:~$ sudo chown -R joshua:joshua /home/joshua/' (Joshua being 'MYUSERNAME')

When I tried this I got a different problem of it an error message saying '***chown: cannot access `/home/joshua/.gvfs': Permission denied***'
' (even with super user access).

As well as this when I try open nautilus as root the file cannot be found 
:confused:
Thanks in advance.

---

