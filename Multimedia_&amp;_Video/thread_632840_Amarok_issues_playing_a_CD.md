---
title: "Amarok issues playing a CD"
date: 2007-12-05
forum: Multimedia &amp; Video
---

### Post by ganymede62 on 2007-12-05
I've been searching around tonight and I can't find a solution. Is it safe to say my issue is a known bug?

My issue is...

After upgrading to the latest distribution I discovered I can't play audio CDs with Amarok. It also won't do a lookup for titles on the CD. Running 'amarokapp' from the CLI I see this:

amarokapp
X Error: BadDevice, invalid or uninitialized input device 158
  Major opcode:  150
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 158
  Major opcode:  150
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
kdecore (KAction): WARNING: KAction::insertKAccel( kaccel = 0x7c8500 ): KAccel object already contains an action name "play_pause"
QLayout "unnamed" added to QVBox "unnamed", which already has a layout
kdecore (KAction): WARNING: KAction::insertKAccel( kaccel = 0x7c8500 ): KAccel object already contains an action name "play_pause"
QLayout: Adding KToolBar/mainToolBar (child of QVBox/unnamed) to layout for PlaylistWindow/PlaylistWindow
QObject::connect: Incompatible sender/receiver arguments
        StarManager::ratingsColorsChanged() --> ContextBrowser::ratingOrScoreOrLabelsChanged(const QString&)
STARTUP
amarok: ERROR: : couldn't create slave : Unable to create io-slave:
klauncher said: Unknown protocol 'cdda'.
amarok: 
amarok: ERROR: : couldn't create slave : Unable to create io-slave:
klauncher said: Unknown protocol 'cdda'.
amarok: 
amarok: ERROR: : couldn't create slave : Unable to create io-slave:
klauncher said: Unknown protocol 'cdda'.
amarok: 
amarok: ERROR: : couldn't create slave : Unable to create io-slave:
klauncher said: Unknown protocol 'cdda'.
amarok: 
amarok: ERROR: : couldn't create slave : Unable to create io-slave:
klauncher said: Unknown protocol 'cdda'.
amarok: 
amarok: ERROR: : couldn't create slave : Unable to create io-slave:
klauncher said: Unknown protocol 'cdda'.
amarok: 
amarok: ERROR: : couldn't create slave : Unable to create io-slave:
klauncher said: Unknown protocol 'cdda'.
amarok: 
amarok: ERROR: : couldn't create slave : Unable to create io-slave:
klauncher said: Unknown protocol 'cdda'.
amarok: 
amarok: ERROR: : couldn't create slave : Unable to create io-slave:
klauncher said: Unknown protocol 'cdda'.
amarok: 
amarok: ERROR: : couldn't create slave : Unable to create io-slave:
klauncher said: Unknown protocol 'cdda'.
amarok: 

Has anyone else seen this issue and have a solution? Any help is greatly appreciated.

---

### Post by nealron on 2007-12-31
I've got this same issue on Gutsy. I even deleted the xine-config as suggested here..

[http://bugs.kde.org/show_bug.cgi?id=151459]("http://bugs.kde.org/show_bug.cgi?id=151459")

Still no worky. I'm still searching, I'll post here if I find anything else.

---

