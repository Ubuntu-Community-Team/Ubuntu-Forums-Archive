---
title: "Amarok &amp; dcopserver problems."
date: 2007-12-23
forum: Multimedia &amp; Video
---

### Post by oliver.drew on 2007-12-23
I've searched through these forums for a solution and none of the available ones seem to work for me, hence I'm stuck!

I'm running 7.10 with Gnome.

I was running Amarok fine until a week or so ago when I got this message:

[I]"There was an error setting up inter-process communications for KDE.  The message returned by the system was:

Could not read network connection list.
/home/oliver/.DCOPserver_Oliver Laptop__1

Please check that the dcopserver program is running![/I]

The solutions I tried suggested I tried running amarokapp in the terminal and this was the output:

oliver@Oliver Laptop:~$ amarokapp
/usr/bin/iceauth: /tmp/dcopPfMg8b:1:  bad "add" command line
/usr/bin/iceauth: /tmp/dcopPfMg8b:2:  bad "add" command line
ICE Connection rejected!

DCOPClient::attachInternal. Attach failed Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed
ICE Connection rejected!

DCOPClient::attachInternal. Attach failed Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed
DCOPServer self-test failed.
kdeinit: DCOPServer could not be started, aborting.
I couldn't enable notifications at the dcopserver!
DCOPRef::send(): no DCOP client or client not attached error
kdecore (KWin): WARNING: Loading of kdetrayproxy failed.
kdecore (KAction): WARNING: KAction::insertKAccel( kaccel = 0x794060 ): KAccel object already contains an action name "play_pause"
QLayout "unnamed" added to QVBox "unnamed", which already has a layout
kdecore (KAction): WARNING: KAction::insertKAccel( kaccel = 0x794060 ): KAccel object already contains an action name "play_pause"
QLayout: Adding KToolBar/mainToolBar (child of QVBox/unnamed) to layout for PlaylistWindow/PlaylistWindow
QObject::connect: Incompatible sender/receiver arguments
        StarManager::ratingsColorsChanged() --> ContextBrowser::ratingOrScoreOrLabelsChanged(const QString&)
STARTUP

Does anyone have any ideas?

---

### Post by oliver.drew on 2007-12-23
SOLVED

It turns out that the hostname for my laptop had a space in it and that was causing the problem.  I've now removed the space and everything is working dandy again.

Hopefully that will solve some other newbies (like me) problem too!!!!

---

### Post by bennettg on 2007-12-27
how do you change the host name?

---

### Post by XavierPR on 2007-12-30
I recently re-installed Ubuntu 7.10, and when i installed Amarok i got the exact same problem as original poster.

So how did you go about chaning the hostname?

total newbie on all things ubuntu/linux here....

any help would be appreciated,

i cant live without amarok on ubuntu =(

---

### Post by elecompte on 2008-06-11
Bump

---

### Post by ZAxisMapping on 2008-06-11
I'm finding on a clean install of 8.04 that amarok locks up (can't refresh it's gui, etc.) with the following on the command line:

```
kdecore (KAction): WARNING: KAction::insertKAccel( kaccel = 0x809d800 ): KAccel object already contains an action name "play_pause"
QLayout "unnamed" added to QVBox "unnamed", which already has a layout
kdecore (KAction): WARNING: KAction::insertKAccel( kaccel = 0x809d800 ): KAccel object already contains an action name "play_pause"
QLayout: Adding KToolBar/mainToolBar (child of QVBox/unnamed) to layout for PlaylistWindow/PlaylistWindow
QObject::connect: Incompatible sender/receiver arguments
	StarManager::ratingsColorsChanged() --> ContextBrowser::ratingOrScoreOrLabelsChanged(const QString&)

```

My hostname is one string with no spaces.

All of the residual amarok apps (amarokapp, dcopserver, ruby on score_default.rb, etc) are all still running.  Thoughts?  I already removed and re-installed with aptitude - no luck there.

---

