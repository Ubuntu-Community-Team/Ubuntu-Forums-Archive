---
title: "ATI/AMD HD3450 - missing opengl"
date: 2010-10-29
forum: Multimedia Software
---

### Post by sleepingdragon on 2010-10-29
I've just purchased a new desktop with a dual-core, 2Gb RAM, 1TB drive, etc., - nice little machine. Everything is going well expect for the AMD HD3450 card (it's my first ATi/AMD card). I installed the latest drivers from amd.com and everything installed fine.

The only problem I have is that 3D games/Google Earth/OpenGL screensavers don't work as there appears to be no OpenGL drivers working with the card. Looking at the Catalyst info, the OpenGL section is completely devoid of version numbers. When trying to run 3D games, I get the expected GLX error:

> init: sdl
init: net
init: game
init: video: mode
X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  157 (GLX)
  Minor opcode of failed request:  19 (X_GLXQueryServerString)
  Serial number of failed request:  19
  Current serial number in output stream:  19On the upside, the controls seem to work - I can play around with Gamma, Brightness and Temperature, so something must be going right.

Any ideas on this one would be greatly appreciated.

*** UPDATE ***

Restarted the fglrx install from the repos, and it is certainly better, but still no 3D - screensavers/games/GoogleEarth. Video is showing that OpenGL is being used and there is certainly an improvement in desktop performance. Still not sure what is causing the lack of 3D though. Still looking for help if anyone is out there!

---

### Post by sleepingdragon on 2010-11-10
* SIGH * Had to do the usual nVidia reconfiguration on this... 

Hey, ATi/AMD, listen up:

I know Linux isn't a major priority for a lot of hardware companies, but if your competitor is in the same boat as you, and they can do it RIGHT, it doesn't make you look good. It would also make me question the quality of your software for the big vendors too, such as Microsoft. I know this sounds like a little bit of a moan, and it is, but I've been bitten by your hardware countless times - three for me and plenty more for others I've helped. It hasn't got any better since the mid-2000's.

You never know, some of us might be in control of a serious IT budget, and in a position to write very healthy cheques, this sort of thing doesn't encourage us to write them for you.

---

### Post by Yellow Pasque on 2010-11-10
Completely purge fglrx: [http://wiki.cchtml.com/index.php/Ubuntu_Lucid_Installation_Guide#Removing_the_Driver](http://wiki.cchtml.com/index.php/Ubuntu_Lucid_Installation_Guide#Removing_the_Driver)
Install latest Catalyst using this guide: [http://wiki.cchtml.com/index.php/Ubuntu_Lucid_Installation_Guide#Installing_the_drivers_manually](http://wiki.cchtml.com/index.php/Ubuntu_Lucid_Installation_Guide#Installing_the_drivers_manually)

> Hey, ATi/AMD, listen up:
I'm sure there are so many ATI employees here reading your rant. :roll:

---

