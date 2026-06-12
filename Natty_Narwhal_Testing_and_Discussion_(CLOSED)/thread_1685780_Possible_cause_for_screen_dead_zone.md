---
title: "Possible cause for screen dead zone"
date: 2011-02-11
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by Quackers on 2011-02-11
Recently I haven't been able to start ccsm. I've tried using the launcher which I have kept in the unity sidebar and I've also been to usr/share/bin and tried to launch it from there. All that happens is that the launcher flashes for a few seconds, but nothing appears.
However, when the launcher stops flashing, I have a dead zone in the screen, which is about the size of the ccsm window. I presume the screen real estate is being booked by the screen, even though it doesn't appear.
If I then go to System Monitor and end the process "ccsm" my dead zone goes away.
ccsm launches fine when opened from the terminal, see below
```
nattyalpha@nattyalpha-VGN-AR51SU:~$ ccsm
Info: No sexy-python package found, don't worry it's optional.
Backend     : gconf
Integration : true
Profile     : unity
Adding plugins
Initializing core options...done
Loading icons...
Initializing compiztoolbox options...done
Initializing mousepoll options...done
Initializing wall options...done
Initializing move options...done
Initializing gnomecompat options...done
Initializing detection options...done
Initializing session options...done
Initializing staticswitcher options...done
Initializing regex options...done
Initializing decor options...done
Initializing scale options...done
Initializing opengl options...done
Initializing animation options...done
Initializing ezoom options...done
Initializing fade options...done
Initializing place options...done
Initializing wobbly options...done
Initializing composite options...done
Initializing unityshell options...done
Initializing bailer options...done
Initializing resize options...done
Initializing vpswitch options...done
Initializing expo options...done
Initializing workarounds options...done
nattyalpha@nattyalpha-VGN-AR51SU:~$ 

```
The only dodgy line is the first one, about no sexy-python package found. Is this why the launcher and usr/share/bin won't load ccsm?
Thanks.

---

### Post by Quackers on 2011-02-11
Oops, it just got worse.
I had ccsm opened in an unmaximised window and I tried to run gparted. No errors messages appeared, but neither did the gparted window.
I closed ccsm and have a dead zone in the middle of the screen (where ccsm window was) but I now have a zone top left, that thinks it's a gparted window - but it isn't showing! However, if I right-click near the top left of the screen I get options like "unmount" "manage flags" and "information", which clearly indicates that the desktop thinks the gparted window is open.
An added problem is that gparted (nor parted) show as running in System Monitor, so I can't end the process. :-(
How do you stop gparted from the terminal, please? The commands I've tried show "Unknown job gparted".
Thanks

---

### Post by dino99 on 2011-02-11
you might have , into system manager, the gparted ID, then kill it

or 

use comand to unmount

sudo umount /dev/xxxy

---

### Post by Quackers on 2011-02-11
System Manager? In system monitor it isn't showing as running and yet I have a mini screen open to resize a partition! A screen which I can't close or move, because it's in the dead zone!
See attached

---

### Post by Quackers on 2011-02-11
I gave up and rebooted :-)
All is back to normal now. Something is wrong though, somewhere, with screen deployment.

---

### Post by mc4man on 2011-02-11
try updating - the latest window stacking fix (compiz) is in a compiz(..ubuntu11) update
There also is a another unity update to fix some possible launcher hiding mis-behavior (3.4.2-0ubuntu2

---

### Post by Quackers on 2011-02-11
System was fully updated at the time, but those two updates may have come through since I've been booted into another install.
I'll go back, update and try again to create the problem.

---

### Post by Quackers on 2011-02-11
I can't recreate the same problem now. Watch this space :-)

---

