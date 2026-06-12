---
title: "Deliver me from EVIL please...!"
date: 2007-08-17
forum: Multimedia &amp; Video
---

### Post by bigbrovar on 2007-08-17
My ubuntu experience as been great and even though am just a month old in  on this revolutionary OS i hardly Boot into my vista evil empire..but now i days i find my self going but to the evil empire just to listen to music and the reason been that amarok has refused to work anymore on my system...everytime i use it it just crashes on me..its really embarrassing especially when when this happens in front of my EVIL empire infested friends..u can just imagine the laughter...the is even small compared to the agony of having to boot to evil just to listen to music:(...i know that there are other music players in ubuntu ..but non does the job 4 me like amorok...please i really need help i would really appreciate cus i want to be independent of evil ...FOREVER...

SYSTEM
Feisty fawn 386i
core2 duo 1.6 ghz
2.gb ram
160gb hd
intel graphic   accelerator GMA945 

also i play my sounds from my ntfs partition which i can read and write from..

---

### Post by loudestnoise on 2007-08-17
Have you tried any other music playing apps?  Rhythmbox, Banshee to name a couple.

---

### Post by happy-and-lost on 2007-08-17
Try running Amarok from the command line, and post back the crash output.

---

### Post by bigbrovar on 2007-08-17
when i ran amarok for terminal i got this [PHP]bigbrovar@bigbrovar-laptop:~$ amarok
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
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
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
kdecore (KAction): WARNING: KAction::insertKAccel( kaccel = 0x8212fb0 ): KAccel object already contains an action name "play_pause"
QLayout "unnamed" added to QVBox "unnamed", which already has a layout
kdecore (KAction): WARNING: KAction::insertKAccel( kaccel = 0x8212fb0 ): KAccel object already contains an action name "play_pause"
QLayout: Adding KToolBar/mainToolBar (child of QVBox/unnamed) to layout for PlaylistWindow/PlaylistWindow
QObject::connect: Incompatible sender/receiver arguments
        StarManager::ratingsColorsChanged() --> ContextBrowser::ratingOrScoreOrLabelsChanged(const QString&)
QColor::setRgb: RGB parameter(s) out of range
QColor::setRgb: RGB parameter(s) out of range
QColor::setRgb: RGB parameter(s) out of range
Amarok: [Loader] Amarok is taking a long time to load! Perhaps something has gone wrong?
amarokapp: Fatal IO error: client killed
bigbrovar@bigbrovar-laptop:~$ 


 [/PHP]
can anybody make sense of these it look so scary :confused:

---

### Post by happy-and-lost on 2007-08-17
According to [http://amarok.kde.org/forum/index.php?topic=14361.msg19538](http://amarok.kde.org/forum/index.php?topic=14361.msg19538), the answer you seek is here: [http://ubuntuforums.org/showthread.php?t=510165](http://ubuntuforums.org/showthread.php?t=510165)

It seems you have to delete ~/.kde/share/apps/amarok

---

### Post by bigbrovar on 2007-08-17
[HTML]happy-and-lost  	
Re: Deliver me from EVIL please...!
According to http://amarok.kde.org/forum/index.ph...14361.msg19538, the answer you seek is here: http://ubuntuforums.org/showthread.php?t=510165

It seems you have to delete ~/.kde/share/apps/amarok  [/HTML]

Thanks Mahn i followed the link and everything is fine now ..amarok as started working fine again...and the world as been saved...:lolflag:

---

