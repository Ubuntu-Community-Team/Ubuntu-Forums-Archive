---
title: "Amarok won't start in gutsy"
date: 2008-02-10
forum: Multimedia &amp; Video
---

### Post by jithin1987 on 2008-02-10
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/amarok/+bug/149936](https://bugs.launchpad.net/ubuntu/+source/amarok/+bug/149936) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				I use kubuntu gutsy. MY system is pentuim core 2 duo 2.2 + intel 945 gcnl. I upgraded my system recently. Before that kubuntu used to work properly. No amarok problems But after that i had a fresh install and amark is not at all loading. But it loads when using live dvd. I used the same dvd in my old system to install. I searched a lot and no one seems to have a fix.

This is my output on terminal

Amarok: [Loader] Starting amarokapp..
Amarok: [Loader] Don't run gdb, valgrind, etc. against this binary! Use amarokapp.
Amarok: [Loader] Amarok is taking a long time to load! Perhaps something hasgone wrong?
kdecore (KAction): WARNING: KAction::insertKAccel( kaccel = 0x8154738 ): KAccel object already contains an action name "play_pause"
QLayout "unnamed" added to QVBox "unnamed", which already has a layout
kdecore (KAction): WARNING: KAction::insertKAccel( kaccel = 0x8154738 ): KAccel object already contains an action name "play_pause"
QLayout: Adding KToolBar/mainToolBar (child of QVBox/unnamed) to layout for PlaylistWindow/PlaylistWindow
QObject::connect: Incompatible sender/receiver arguments
        StarManager::ratingsColorsChanged() --> ContextBrowser::ratingOrScoreOrLabelsChanged(const QString&)

Some times it loads and the amarok window appears thats all and it stays frozen.
Can anyone help me

---

### Post by jithin1987 on 2008-02-12
when i ran amarok with strace This is what i got before i killed it
.........................................................................
 waitpid(6028, 0xbfcbf430, WNOHANG) = 0
 ioctl(7, FIONREAD, [0]) = 0
 ioctl(5, FIONREAD, [0]) = 0
 gettimeofday({1202820419, 191369}, NULL) = 0
 select(18, [5 6 7 16 17], [], [], {0, 9872}) = 0 (Timeout)
 gettimeofday({1202820419, 200940}, NULL) = 0
 ioctl(5, FIONREAD, [0]) = 0
 gettimeofday({1202820419, 201263}, NULL) = 0
 select(18, [5 6 7 16 17], [], [], {0, 0}) = 0 (Timeout)
 gettimeofday({1202820419, 201589}, NULL) = 0
 waitpid(6028, 0xbfcbf430, WNOHANG) = 0
 ioctl(7, FIONREAD, [0]) = 0
 ioctl(5, FIONREAD, [0]) = 0
 gettimeofday({1202820419, 202193}, NULL) = 0
 select(18, [5 6 7 16 17], [], [], {0, 9048}) = 0 (Timeout)
 gettimeofday({1202820419, 249667}, NULL) = 0
 waitpid(6028, 0xbfcbf430, WNOHANG) = 0
 ioctl(7, FIONREAD, [0]) = 0
 ioctl(5, FIONREAD, [0]) = 0
 gettimeofday({1202820419, 250423}, NULL) = 0
 select(18, [5 6 7 16 17], [], [], {0, 9244}) = 0 (Timeout)
 gettimeofday({1202820419, 275255}, NULL) = 0
 waitpid(6028, 0xbfcbf430, WNOHANG) = 0
 ioctl(7, FIONREAD, [0]) = 0
 ioctl(5, FIONREAD, [0]) = 0
 gettimeofday({1202820419, 275387}, NULL) = 0
 select(18, [5 6 7 16 17], [], [], {0, 9868}) = 0 (Timeout)
 gettimeofday({1202820419, 284882}, NULL) = 0
 ioctl(5, FIONREAD, [0]) = 0
 gettimeofday({1202820419, 285195}, NULL) = 0
 select(18, [5 6 7 16 17], [], [], {0, 60}) = 0 (Timeout)
 gettimeofday({1202820419, 288838}, NULL) = 0
 waitpid(6028, 0xbfcbf430, WNOHANG) = 0
 ioctl(7, FIONREAD, [0]) = 0
 ioctl(5, FIONREAD, [0]) = 0
 gettimeofday({1202820419, 289533}, NULL) = 0
 select(18, [5 6 7 16 17], [], [], {0, 5722}) = 0 (Timeout)
 gettimeofday({1202820419, 297166}, NULL) = 0
 waitpid(6028, 0xbfcbf430, WNOHANG) = 0
 ioctl(7, FIONREAD, [0]) = 0
 ioctl(5, FIONREAD, [0]) = 0
 gettimeofday({1202820419, 298383}, NULL) = 0
 select(18, [5 6 7 16 17], [], [], {0, 6872}) = 0 (Timeout)
 gettimeofday({1202820419, 304849}, NULL) = 0
 ioctl(5, FIONREAD, [0]) = 0
 gettimeofday({1202820419, 305161}, NULL) = 0
 select(18, [5 6 7 16 17], [], [], {0, 94}) = 0 (Timeout)
 gettimeofday({1202820419, 308841}, NULL) = 0
 waitpid(6028, 0xbfcbf430, WNOHANG) = 0
 ioctl(7, FIONREAD, [0]) = 0
 ioctl(5, FIONREAD, [0]) = 0
 gettimeofday({1202820419, 309524}, NULL) = 0
 select(18, [5 6 7 16 17], [], [], {0, 5731}) = 0 (Timeout)
 gettimeofday({1202820419, 349352}, NULL) = 0
 waitpid(6028, 0xbfcbf430, WNOHANG) = 0
 ioctl(7, FIONREAD, [0]) = 0
 ioctl(5, FIONREAD, [0]) = 0
 gettimeofday({1202820419, 349480}, NULL) = 0
 select(18, [5 6 7 16 17], [], [], {0, 9872}) = 0 (Timeout)
 gettimeofday({1202820419, 375300}, NULL) = 0
 waitpid(6028, 0xbfcbf430, WNOHANG) = 0
 ioctl(7, FIONREAD, [0]) = 0
 ioctl(5, FIONREAD, [0]) = 0
 gettimeofday({1202820419, 376051}, NULL) = 0
 select(18, [5 6 7 16 17], [], [], {0, ...

---

