---
title: "FIX: amarok kaffeine hangs"
date: 2007-08-03
forum: Multimedia &amp; Video
---

### Post by bibstha on 2007-08-03
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/amarok/+bug/89711](https://bugs.launchpad.net/ubuntu/+source/amarok/+bug/89711) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				On user accounts created using adduser command, the "audio" and "video" groups were missing.

So whenever starting amarok for accounts created by adduser,
amarok window opens up and hangs indefinitely.

Starting from konsole it gave this error

kdecore (KAction): WARNING: KAction::insertKAccel( kaccel = 0x8097d50 ): KAccel object already contains an action name "play_pause"
QLayout "unnamed" added to QVBox "unnamed", which already has a layout
kdecore (KAction): WARNING: KAction::insertKAccel( kaccel = 0x8097d50 ): KAccel object already contains an action name "play_pause"
QLayout: Adding KToolBar/mainToolBar (child of QVBox/unnamed) to layout for PlaylistWindow/PlaylistWindow
Amarok: [Loader] Amarok is taking a long time to load! Perhaps something has gone wrong?

Similarly Kaffeine start but when playing anything, it hangs and needs to be terminated

**Solution**
From a superuser account
sudo adduser username audio
sudo adduser username video

now everything works, 
i had to searched for the solution for 2 hours, i hope it helps 

bibstha
[hamrolyrics.com]("http://hamrolyrics.com")

---

